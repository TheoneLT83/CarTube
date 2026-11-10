# Changelog

## 1.0.1 (app)

- **The picture shows**: the app reads the frames where the released decoder writes them (`/dev/shm/mgu-video-ridetube`); only the sound played.
- **Settings tab on iDrive 7 too**: the account and the settings (video while driving, quality, SponsorBlock...).

## 1.0.0 (app and service)

CarTube: RideTube (JustAnotherPU) and its iDrive 8 port (waliworld) as one app for iDrive 7 and iDrive 8, in the
idrive7-apps look, for TheoneLT83's MGU Store. Their history: `docs/history/`.

- **The pages are the tabs in BMW's title strip** (Home, Subscriptions, Search, Watch later, Now playing while
  something plays; Settings), as every idrive7-apps app; BMW's status icons and clock stay in view. No icon rail.
- **The player on the page**: the video on the left, on the right the title, the bar, the chapter and big -10 s,
  Play / Pause, +10 s, then the quality, **Full screen** and Fill / Fit. Full screen puts the video over the whole
  screen with RideTube's overlay; Back there returns to the page. While driving, the page player with the sound only.
  A failed play: Try again.
- **The internet from the MGU Store**: the state of its uplink (`/run/mgu-uplink/status.json`) at the top right of the
  page: Online · Wi-Fi / phone / USB, Connecting, Offline, or No MGU Store internet. The service requires `mgu-uplink`.
- **The idrive7-apps theme**: its background, text and accent red instead of RideTube's navy and pink.
- **Its own names**: `cartube` / `cartube8`, `cartube-d`, `cartube-node22`, `/run/cartube-d`, `/var/opt/cartube-d`,
  logging ids OAC1 / CTB8: it can sit beside RideTube.
- **The release**: one catalog for iDrive 7 and iDrive 8, published to this repository's `catalog` release on every
  change to `main`.
