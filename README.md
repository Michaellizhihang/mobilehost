# MobileHost

Flutter Android starter app hosting a static website ZIP and forwarding requests through a compatible reverse-tunnel relay.

## Quick start

1. Install Flutter 3.24+ and Android SDK, then run `flutter pub get` and `flutter run`.
2. Create/deploy a relay implementing [`docs/RELAY_PROTOCOL.md`](docs/RELAY_PROTOCOL.md), set its secure WebSocket URL and token in the app.
3. Select a ZIP whose root (or single top-level directory) contains `index.html`; set port and tap Start.
4. GitHub Actions builds `app-release.apk` and exposes it as a workflow artifact.

This repository does not include or provision a public relay. `relay.example.com` is only a placeholder. The app does not directly support public LocalTunnel servers. See the protocol document before deploying a relay. Keep authentication enabled, use TLS, and avoid hosting sensitive files.

## Android

`INTERNET` permits local listening and outbound relay connections; `ACCESS_NETWORK_STATE` and `ACCESS_WIFI_STATE` are optional diagnostics. Storage permissions are not required because Android's Storage Access Framework (via file_picker) grants access to the user-selected ZIP. For long-running background hosting, a foreground service and Android notification are additionally needed; this starter is intended to stay active while the app remains open.
