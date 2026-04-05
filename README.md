# Cores-spruce

Build bot for libretro cores targeting spruceOS handheld devices. Builds 32-bit (armhf) and 64-bit (arm64) cores using [libretro-super](https://github.com/libretro/libretro-super).

## Supported devices

| Arch | Devices |
|------|---------|
| arm64 | Trimui Brick, Smart Pro, Smart Pro S, Miyoo Flip |
| armhf | Miyoo Mini/Mini+, Miyoo A30 |

## How it works

- Two Docker images (cached on the `toolchains` release) provide cross-compilation environments
- Each core has its own GitHub Actions workflow — trigger individually or use **Build All Cores** to build everything in parallel
- Output: one zip per core containing `cores/` (armhf), `cores64/` (arm64), and a `.info` metadata file
- Built cores are uploaded to the `beta-{branch}` release

## Usage

1. **Build Docker images** (only needed once, or after Dockerfile changes): run `Build Docker Images`
2. **Build one core**: run `Build <corename>` from Actions
3. **Build all cores**: run `Build All Cores` from Actions

## TODO: cores not yet buildable

These cores are shipped by spruceOS but can't be built from libretro-super and need custom build processes:

- [ ] **fake08** — not in libretro-super
- [ ] **mkxp-z** — hyphen in name breaks libretro-super's bash variable parsing
- [ ] **mupen64plus** — removed from libretro-super (replaced by mupen64plus_next)
- [ ] **km_duckswanstation_xtreme_amped** — Knulli Mod, custom build
- [ ] **km_flycast_xtreme** — Knulli Mod, custom build
- [ ] **km_ludicrousn64_2k22_xtreme_amped** — Knulli Mod, custom build
- [ ] **km_parallel_n64_xtreme_amped_turbo** — Knulli Mod, custom build
