  - FAQ
    - Can you explain Cmod's license? BSD
  - Why TDD?
  - TDD tutorial for generic embedded system project
  - Adding mocks with FFF
  - Why not Ceedling?
  - Why not bare-metal Unity?
  - Why not CppuTest?
  - Why write and use a style guide?
  - State of current dev tools for embedded C developers
    -  Why we can/should do better, and How
    - LIT review of available frameworks

|  Sample Table                 | std |rustc|cargo| notes                      |
|-------------------------------|-----|-----|-----|----------------------------|
| `x86_64-unknown-linux-musl`   |  ✓  |     |     | 64-bit Linux with MUSL     |
| `arm-linux-androideabi`       |  ✓  |     |     | ARM Android                |
| `arm-unknown-linux-gnueabi`   |  ✓  |  ✓  |     | ARM Linux (2.6.18+)        |
| `arm-unknown-linux-gnueabihf` |  ✓  |  ✓  |     | ARM Linux (2.6.18+)        |
| `aarch64-unknown-linux-gnu`   |  ✓  |     |     | ARM64 Linux (2.6.18+)      |
| `mips-unknown-linux-gnu`      |  ✓  |     |     | MIPS Linux (2.6.18+)       |
| `mipsel-unknown-linux-gnu`    |  ✓  |     |     | MIPS (LE) Linux (2.6.18+)  |