# reticulous-builds

Pre-built, ready-to-flash firmware images for [Reticulous](https://github.com/reticulous),
served to the browser flasher.

- **`builds.yaml`** — the catalogue: each entry is a short name + a `spangap build`
  invocation.
- **`main/<name>.zip`** — the built image for each entry (a `flasher.zip`:
  `flasher_args.json` + the bootloader / partition-table / app / data images).
  The [web flasher](https://github.com/spangap/flasher) fetches `main/<name>.zip`
  for `?build=<name>`.

Current builds: `tdeck` (LilyGO T-Deck Plus), `heltecv4` (Heltec WiFi LoRa 32 V4,
headless), `generic` (any ESP32-S3 with PSRAM, WiFi-only, no mesh radio).

## Producing the images

Trigger the **Build firmware** GitHub Action (Actions tab → *Build firmware* →
*Run workflow*). It installs spangap, builds every entry in `builds.yaml`, and
commits the resulting `main/*.zip` back to this repo.

To do it locally instead, from a spangap workspace:

```sh
spangap make-builds /path/to/reticulous-builds   # builds all entries → main/*.zip
```

This repo is **public** so the flasher can fetch its zips over the network.
