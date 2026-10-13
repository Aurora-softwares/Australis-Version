# Australis Version

## Current status

The current source prints a fixed `Version: 0.0.1`. It launches as an AUEX program but does not yet query the running OS version.

`Version.hyproj` builds `version.exec`. The Australis OS aggregate includes
this project and installs the executable at `/Bin/version.exec` in the read-only
HyFS 2 boot image. Run it by its bare name `/Bin/` through the current
recovery shell's `PATH`, or use `run /Bin/version.exec`.

## Planned direction

For userland Stage 2, replace the fixed string with a read-only version query and test the external command over both storage paths.

Build this checkout with:

```bash
mkdir -p build
hy build Version.hyproj -o build/version.exec
```

AUEX `.exec` files currently run in the checked interpreter. Native ring-3
processes and a normal userland shell are later milestones. The boot root is
read-only; writable application data belongs on the separate `/data` volume.
The OS-level build, supported APIs, and packaging rules are described in the
Australis OS `applications/README.md`. This README describes this project's
actual source rather than treating its filename as proof of a finished feature.
