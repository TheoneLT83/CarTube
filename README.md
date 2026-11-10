# CarTube

> **Experimental and unofficial.** CarTube is an unofficial client for YouTube. It is not affiliated with, endorsed by
> or sponsored by Google or YouTube. Use it at your own risk; you are responsible for following YouTube's Terms of
> Service and the laws of your country, and for using it safely: by default the picture shows only while the car is
> parked.

Video in BMWs with iDrive 7 and iDrive 8 (MGU head units), installed from the [MGU Store](https://github.com/TheoneLT83/mgu-store),
in the look of the [idrive7-apps](https://github.com/TheoneLT83/idrive7-apps): the pages are the tabs in BMW's own
title strip, BMW's status icons and clock stay in view.

- **Home**, **Subscriptions**, **Search** and **Watch later**, once you sign in on the car with a code you enter at
  google.com/device on your phone (CarTube never sees your password).
- **The player on the page**: the video on the left, the title, the bar with chapters and big controls on the right;
  **Full screen** puts the video over the whole screen (Back returns to the page).
- **Internet from the MGU Store**: CarTube goes online only through the Store's uplink (Wi-Fi, a phone's hotspot or a
  USB stick); the page shows **Online · Wi-Fi / phone / USB** or **Offline**.
- **While driving**: sound only (the car's own media player), big controls; the picture comes back when parked.
- **SponsorBlock** (sponsors, self-promotion, intros: skip, a Skip button, or off), the video quality, fill or fit.
- Nothing is kept: the video playing is downloaded while it plays, then deleted. Expect the video's whole size on
  your data plan.

## Install

CarTube is a default source of [TheoneLT83/mgu-store](https://github.com/TheoneLT83/mgu-store) (Store 0.9.59 or newer) and
of the iDrive 7 Assistant. With an older Store: Settings, **Add source**, `TheoneLT83/CarTube`, **Releases**.

Install **CarTube** in the Store. It brings, as its requirements, its service `cartube-d`, Node.js 22
(`cartube-node22`) from this source, and from the Store's own source the renderer `mgu-render`, `mgu-python`, the
deploy tool, the internet uplink `mgu-uplink` and, on iDrive 7, the controller gate `mgu-inputgate`. On iDrive 8 the
app installs at the next start of the head unit.

CarTube uses its own names throughout (`cartube`, `cartube8`, `cartube-d`, `/run/cartube-d`, `/var/opt/cartube-d`),
so it can sit beside RideTube; only one of them plays sound at a time.

## Settings

Video while driving (off; only for a car coded for video in motion, where only passengers see the screen), Fill the
screen, Video quality (auto: 720p on Wi-Fi, 480p on phone data), members-only videos, SponsorBlock per category, and
pausing when the 12 V battery is low (parked).

## Layout

| Path | |
|---|---|
| `apps/cartube` | the app (the iDrive's own Node 8 runtime): `cartube` for iDrive 7, `cartube8` for iDrive 8 |
| `kit/` | the idrive7-apps app kit, as RideTube trimmed and extended it |
| `native/cartube-d` | the service on the car: player, fetcher (yt-dlp), account, search, thumbnails |
| `native/ytdec` | the H.264 decoder that draws into the renderer's video layer |
| `tools/cartube-node22` | Node.js 22 for the service |
| `tools/release.sh`, `tools/release.py` | the Store catalog (`catalog.json` and its assets) |

## Release

`.github/workflows/release.yml` builds and tests everything and publishes it to the GitHub release tagged `catalog`
on every change to `main`:

```sh
MGU_STORE=<a clone of github.com/TheoneLT83/mgu-store> tools/release.sh     # -> dist/release/
```

The prebuilt binaries (the decoder `ytdec`, yt-dlp and the Node.js 22 build) are taken from JustAnotherPU's published
RideTube and mgu-apps releases and checked against pinned sha256 sums. No package holds BMW's oap-sdk: the head unit
links the app against the SDK of an app already on the car.

## Credits and licence

CarTube is built on **RideTube** by [JustAnotherPU](https://github.com/JustAnotherPU/ridetube) (iDrive 7) and its
iDrive 8 port by [waliworld](https://github.com/waliworld/iDrive8-RideTube); their changelogs are in `docs/history/`.
Changed for CarTube: the name and every identifier, the idrive7-apps look (header tabs, the page player with Full
screen, the theme), the internet state from the MGU Store's uplink, the release for TheoneLT83's Store.

GPL-3.0-or-later ([LICENSE](LICENSE)). Parts keep their own licences (the app kit: MIT; parts of `native/ytdec`:
GPL-3.0-or-later; yt-dlp: Unlicense; Node.js: MIT; SponsorBlock data: CC BY-NC-SA 4.0): see
[THIRD_PARTY_LICENSES](THIRD_PARTY_LICENSES).
