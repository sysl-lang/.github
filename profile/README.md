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
  qcbor { git = "github.com/sysl-lang/qcbor", version = "0.1.0" }
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

The package and the module are deliberately different names: a package is a unit of distribution and
a module is a unit of code, which is why `sqlite3` is imported as `sh.sysl.sqlite`.

**Eight of them need something installed** — `sqlite3` wants SQLite, `cairo` wants cairo, `pico` and
`pico2` want the Raspberry Pi Pico SDK, and the four SDL3 packages want SDL3 and its companion
libraries. The rest get there three different ways. `table`, `ogol`, `st7796`, `rp2040`,
`rp2040blocks` and `rp2350` are sysl all the way down and bind nothing at all. `regex` binds the C
library every hosted machine already has, so it carries a shim for what only a header knows and no
upstream source whatever. `qcbor`, `qoi`, `monocypher`, `linenoise`, `termbox2` and `plutovg` carry
their C and compile it as part of the build. None of the twenty-one asks you to write an `-l` flag:
where a library has to be linked, the package's own header says so and the annotation travels inside
the artifact.

**A library a package manager installed does need its prefix on the command line**, which is the one
thing a package cannot say for you — `--include-path /opt/homebrew/include --link-path
/opt/homebrew/lib`, or `CPATH` and `LIBRARY_PATH` in the environment. Where a prefix lives is a fact
about a machine rather than a property of a package, so `design/15 §8` refuses to let a package
declare it. `sqlite3`, `cairo` and the SDL3 packages are the ones this reaches — and `cairo` needs
only the `--link-path` half, because it compiles no C of its own and so never reads a header.

**The four SDL3 packages are four rather than one, and that is forced rather than chosen.** A link
directive is never pruned — every unit of a compilation contributes its libraries whether or not the
program reaches it — so a single package would put `-lSDL3_ttf -lSDL3_image -lSDL3_mixer` on the link
line of every program that used any of it, and a machine with only SDL3 installed could not link a
program that draws rectangles. Depend on what you use. They are also the org's first packages built
on **another package** rather than on C alone: the three companions fetch `sdl3` for its `Color`,
`Surface`, `Renderer` and `Texture`.

**`plutovg` and `cairo` are the two that needed no shim at all**, which is rare enough to say out
loud: not a single function in either API takes or returns a struct by value, so the whole library is
reachable by declaring it. Most bindings here carry a little C for the things only a header knows.

**They are also the two that draw the same pictures, and neither replaces the other.** Cairo has the
vector backends — PDF, SVG, PostScript — and is already on most machines; PlutoVG carries its own C,
asks for no system library and needs no allocator it cannot be given, so it runs on a
microcontroller. The division is about where the program runs rather than about which has more in it.

**`st7796` and `rp2350` are the pair that shows what a package for hardware looks like when it is done
properly.** Neither knows anything about a board: the display driver takes three function pointers and
so serves an ESP32 or an STM32 as readily as a Pico, and the register map is the silicon rather than
any particular product built from it. Where the wires actually go is the program's business.

**`pico2` is the odd one, and is worth reading as such.** It declares and implements nothing — every
name in it is a symbol the Pico SDK already has, so a program using it is compiled by `sysl build-c`
into an archive that the SDK's own CMake links. That is the arrangement turned the other way up: C
hosting sysl, rather than sysl binding C. It is how a sysl program reaches a microcontroller's USB
and Wi-Fi without reimplementing either — and on that board it leaves no C in the project at all,
because sysl exports `main` and the SDK's startup code calls it.
[**pico-scratch**](https://github.com/sysl-lang/pico-scratch), below, is that running on real
silicon.

**One package has left this list rather than been added to it.** `harness`, a test framework that
runs on the target, is part of the standard library from sysl 0.0.31 — `import sysl.harness.*`, with
nothing to fetch and nothing to declare. [Its repository](https://github.com/sysl-lang/harness) stays
for the tags that came before.

## Worked examples

Complete programs rather than libraries — the shortest answers to what a sysl project looks like.

| repository | what it shows |
|---|---|
| [**monocypher-example**](https://github.com/sysl-lang/monocypher-example) | one dependency — two people agree a key over an insecure channel, then send a signed, sealed message |
| [**sqlite-repl**](https://github.com/sysl-lang/sqlite-repl) | three dependencies — a SQL prompt where linenoise reads the line, sqlite3 runs it and table lays the answer out |
| [**sdl3-demo**](https://github.com/sysl-lang/sdl3-demo) | four dependencies, and a graphical one — a bouncing ball with a trail, text, a note per bounce and a screenshot key, with no asset file anywhere |
| [**ogol-host**](https://github.com/sysl-lang/ogol-host) | a language and its console — the hosted half, at a terminal |
| [**ogol-pico2**](https://github.com/sysl-lang/ogol-pico2) | the same program on a Raspberry Pi Pico 2 W over USB serial — the loop is the language's, so only the streams differ |
| [**ogol-pico**](https://github.com/sysl-lang/ogol-pico) | and again on the original Pico W — three lines of source apart from the one above, which is what a shared `session` is worth |
| [**picokit**](https://github.com/sysl-lang/picokit) | one carrier board's glue — the pin map, the registers and the panel of a Pico Breadboard Kit, which is what keeps a display driver from becoming a package for one board |
| [**pico-scratch**](https://github.com/sysl-lang/pico-scratch) | sysl on a microcontroller — a blink program and a REPL on a Pico 2 W over USB serial, with no C in either project |
