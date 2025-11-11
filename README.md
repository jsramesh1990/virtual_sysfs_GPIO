# GPIO Control + Simulator (example)

This repo contains:
- `gpio-sysfs.c` — simple sysfs-based GPIO control (learning / compatibility).
- `gpio-libgpiod.c` — modern libgpiod-based GPIO control.
- `simulator.py` — virtual sysfs GPIO simulator (no hardware needed).
- `Makefile`, `test.sh`, `.gitignore`, this README.

## Quick start (dev machine)
1. Build:

make

2. Run simulator & test:

./test.sh


## Notes
- The sysfs program uses `/sys/class/gpio` by default. For simulation set `VIRT_GPIO_ROOT` to simulator root.
- `gpio-libgpiod` requires libgpiod development headers.
- Use Git to track sources; recommended files to include shown below.

## Files to upload
- All `.c`, `.h`, `Makefile`, `simulator.py`, `test.sh`, `README.md`
- `.gitignore` (provided)

## License
Add an appropriate license file if needed (e.g. `LICENSE`).

## Linux exposes GPIOs to user-space and how you can toggle or read them — both using sysfs (older method) and libgpiod (modern method).
