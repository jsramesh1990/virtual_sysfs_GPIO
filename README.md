# GPIO Control + Simulator 

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

 ** visual diagram of the virtual_sysfs_GPIO project**

                   +-----------------------+
                   |  virtual_sysfs_GPIO   |
                   +-----------------------+
                             |
                             v
                  +---------------------+
                  |  GPIO Initialization |
                  |  (sysfs / libgpiod) |
                  +---------------------+
                             |
          ------------------------------------------
          |                                        |
          v                                        v
+----------------------+                 +----------------------+
|  Sysfs Interface     |                 |  libgpiod Interface  |
|  (gpio-sysfs.c)      |                 |  (gpio-libgpiod.c)  |
+----------------------+                 +----------------------+
          |                                        |
          | Export GPIOs, set direction           | Open GPIO chip, request line
          | Write/read 0/1                        | Set value 0/1
          v                                        v
+---------------------------------------------------------+
|                 LED / GPIO Simulation                  |
|  (simulator.py for visualization or test.sh for auto) |
+---------------------------------------------------------+
                             |
                             v
                   +-----------------------+
                   |     Test / Verify     |
                   |   Observe LED states  |
                   +-----------------------+


**Flow Explanation:**

1.GPIO Initialization:

Sets up GPIO pins, decides whether to use sysfs (older interface) or libgpiod (modern interface).

2. Sysfs / libgpiod Control:

Sysfs: export pins, set direction (in/out), write 0/1.

libgpiod: open GPIO chip, request line, set value.

3.Simulation / Visualization:

simulator.py shows LEDs turning on/off virtually.

test.sh can automate toggling sequences.

4.Verification:

Observe console outputs, LED simulation, or test scripts to verify GPIO behavior.

## License
Add an appropriate license file if needed (e.g. `LICENSE`).

## Linux exposes GPIOs to user-space and how you can toggle or read them — both using sysfs (older method) and libgpiod (modern method).
