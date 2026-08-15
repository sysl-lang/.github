<p align="center">
  <img src="https://sysl.sh/sysl-wordmark.svg" alt="sysl" width="480">
</p>

<p align="center">
  A modern, ref-counted, general-purpose systems language.
</p>

**[sysl.sh](https://sysl.sh) has the documentation** — the tour, the guides, the library reference.
This page is only an index of what lives here.

```bash
brew install sysl-lang/tap/sysl
```

## The language

| repository | what it is |
|---|---|
| [**sysl**](https://github.com/sysl-lang/sysl) | the compiler, the standard library, and the design chapters |
| [**sysl.sh**](https://github.com/sysl-lang/sysl.sh) | the documentation site |
| [**homebrew-tap**](https://github.com/sysl-lang/homebrew-tap) | the Homebrew formula |
| [**svd**](https://github.com/sysl-lang/svd) | a build tool — turns a chip vendor's CMSIS SVD description into sysl constants |

## Packages

Name one in your project's `package.hocon` and `sysl build` fetches it:

```hocon
dependencies {
  qcbor { git = "github.com/sysl-lang/qcbor", version = "0.4.0" }
}
```

| package | module you import | what it is |
|---|---|---|
| [**table**](https://github.com/sysl-lang/table) | `sh.sysl.table` | tables of text — grids, Markdown, matrices, laid out by the columns a character occupies |
| [**qcbor**](https://github.com/sysl-lang/qcbor) | `sh.sysl.qcbor` | CBOR — RFC 8949 |
| [**qoi**](https://github.com/sysl-lang/qoi) | `sh.sysl.qoi` | lossless image compression — the Quite OK Image format, with no heap underneath it |
| [**monocypher**](https://github.com/sysl-lang/monocypher) | `sh.sysl.monocypher` | cryptography — authenticated encryption, key exchange, signatures, hashing |
| [**regex**](https://github.com/sysl-lang/regex) | `sh.sysl.regex` | POSIX regular expressions — and the worked example of binding a C library the machine already has |
| [**sqlite3**](https://github.com/sysl-lang/sqlite3) | `sh.sysl.sqlite` | SQLite |
| [**linenoise**](https://github.com/sysl-lang/linenoise) | `sh.sysl.linenoise` | line editing for a terminal REPL |
| [**termbox2**](https://github.com/sysl-lang/termbox2) | `sh.sysl.termbox2` | a full-screen terminal interface — cells, colours, keys and the mouse |
| [**ogol**](https://github.com/sysl-lang/ogol) | `sh.sysl.ogol` | an onboard interactive language — Logo's arity-driven grammar with the brackets and the sigils taken off, small enough to live in a microcontroller's flash |
| [**solder**](https://github.com/sysl-lang/solder) | `sh.sysl.solder` | the other onboard language — a Forth with a typed cell and reference counting, so an array is freed where it stops being referred to rather than at a collection nobody scheduled |
| [**pico2**](https://github.com/sysl-lang/pico2) | `sh.sysl.pico2` | the Raspberry Pi Pico 2 W — the board's own entry points, for a program the C SDK hosts |
| [**plutovg**](https://github.com/sysl-lang/plutovg) | `sh.sysl.plutovg` | 2D vector graphics — paths, gradients, clipping and text, rasterized into memory and nothing else |
| [**st7796**](https://github.com/sysl-lang/st7796) | `sh.sysl.st7796` | a 320×480 SPI display — the driver is three function pointers wide, so it belongs to no particular board |
| [**rp2350**](https://github.com/sysl-lang/rp2350) | `sh.sysl.rp2350` | the register map of the Pico 2's chip — every peripheral as constants, generated from Raspberry Pi's own SVD |
| [**pico**](https://github.com/sysl-lang/pico) | `sh.sysl.pico` | the original Raspberry Pi Pico W — the same board surface as `pico2`, plus the atomics an Armv6-M core cannot do for itself |
| [**rp2040**](https://github.com/sysl-lang/rp2040) | `sh.sysl.rp2040` | the register map of the original Pico's chip, generated from the same SVD pipeline |
| [**rp2040blocks**](https://github.com/sysl-lang/rp2040blocks) | `sh.sysl.rp2040blocks` | that chip's GPIO and SPI — the hand-written half, because a generated package has nowhere for code to live |
| [**sdl3**](https://github.com/sysl-lang/sdl3) | `sh.sysl.sdl3` | a window, an accelerated renderer, the event queue, keyboard and mouse, the clipboard, the system file dialog and queued audio |
| [**sdl3-ttf**](https://github.com/sysl-lang/sdl3-ttf) | `sh.sysl.sdl3_ttf` | text rendered out of a font file, onto a surface or straight to a texture |
| [**sdl3-image**](https://github.com/sysl-lang/sdl3-image) | `sh.sysl.sdl3_image` | image files decoded — PNG, JPEG and whatever else the installed SDL3_image was built with |
| [**sdl3-mixer**](https://github.com/sysl-lang/sdl3-mixer) | `sh.sysl.sdl3_mixer` | sound and music, mixed, looped, faded and stopped |
| [**cairo**](https://github.com/sysl-lang/cairo) | `sh.sysl.cairo` | 2D vector graphics that render to pixels or straight to a PDF, an SVG or a PostScript page, from the same drawing code |
| [**imui**](https://github.com/sysl-lang/imui) | `sh.sysl.imui` | an immediate-mode user interface — no retained tree, no reconciler and no allocation at all, sized for a panel on a microcontroller |
| [**freertos**](https://github.com/sysl-lang/freertos) | `sh.sysl.freertos` | the real-time kernel, whole — tasks, queues, semaphores, timers, event groups, stream buffers, queue sets and the interrupt half, against whichever port and config the program was built with |
| [**zephyr**](https://github.com/sysl-lang/zephyr) | `sh.sysl.zephyr` | the other real-time kernel — threads, semaphores, mutexes, condition variables, events, message queues, timers and work queues, every size measured out of the kernel your own Kconfig produced |
| [**box2d**](https://github.com/sysl-lang/box2d) | `sh.sysl.box2d` | 2D rigid body physics — bodies, shapes, the eight joints, contacts and queries, with every one of its thirty-one by-value structs checked against Box2D's own headers by the C compiler at build time |

## Programs

Complete programs rather than libraries — the shortest answers to what a sysl project looks like.

| repository | what it shows |
|---|---|
| [**monocypher-example**](https://github.com/sysl-lang/monocypher-example) | one dependency — two people agree a key over an insecure channel, then send a signed, sealed message |
| [**sqlite-repl**](https://github.com/sysl-lang/sqlite-repl) | three dependencies — a SQL prompt where linenoise reads the line, sqlite3 runs it and table lays the answer out |
| [**sdl3-demo**](https://github.com/sysl-lang/sdl3-demo) | four dependencies, and a graphical one — a bouncing ball with a trail, text, a note per bounce and a screenshot key, with no asset file anywhere |
| [**cairo-demo**](https://github.com/sysl-lang/cairo-demo) | one drawing function called four times — the same chart written to a PNG, a PDF, an SVG and a PostScript page, which is the whole argument for cairo in one program |
| [**cairo-sdl3-demo**](https://github.com/sysl-lang/cairo-sdl3-demo) | two packages that need each other — cairo rasterizes a tumbling gear train into a buffer SDL3 shows as a texture, and the 3D is exact rather than faked because an orthographic view of a flat object is an affine matrix |
| [**box2d-demo**](https://github.com/sysl-lang/box2d-demo) | three packages and nothing between them — grab a body and throw it, watch the pile go to sleep, with box2d deciding where everything is, cairo cutting the shapes and SDL3 turning the crank |
| [**imui-demo**](https://github.com/sysl-lang/imui-demo) | a user interface rather than a picture — a 320×480 settings panel drawn by cairo through `imui`'s painter trait, repainting only the horizontal bands that changed, which is 30 rows of 480 on an idle frame |
| [**solder-host**](https://github.com/sysl-lang/solder-host) | the other language and its console — thirty lines, none of them about SOLDER, because the read-run-print loop lives in the package where every console can share it |
| [**ogol-host**](https://github.com/sysl-lang/ogol-host) | a language and its console — the hosted half, at a terminal |
| [**solder-pico2**](https://github.com/sysl-lang/solder-pico2) | the same trick for the other language — SOLDER on a Pico 2 W in 405 KB of flash, the board console being the desktop one with its first few lines swapped |
| [**ogol-pico2**](https://github.com/sysl-lang/ogol-pico2) | the same program on a Raspberry Pi Pico 2 W over USB serial — the loop is the language's, so only the streams differ |
| [**ogol-pico**](https://github.com/sysl-lang/ogol-pico) | and again on the original Pico W — three lines of source apart from the one above, which is what a shared `session` is worth |
| [**picokit**](https://github.com/sysl-lang/picokit) | one carrier board's glue — the pin map, the registers and the panel of a Pico Breadboard Kit, which is what keeps a display driver from becoming a package for one board |
| [**pico-scratch**](https://github.com/sysl-lang/pico-scratch) | sysl on a microcontroller — a blink program and a REPL on a Pico 2 W over USB serial, with no C in either project |
| [**zephyr-demo**](https://github.com/sysl-lang/zephyr-demo) | a sysl program under Zephyr's CMake, and the binding's own suite — 70 assertions against a real kernel booted under QEMU, because a kernel image is the only place they can run |
