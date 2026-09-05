<p align="center">
  <img src="https://sysl.sh/sysl-wordmark.svg" alt="sysl" width="480">
</p>

<p align="center">
  A modern, ref-counted, general-purpose systems language.
</p>

**[sysl.sh](https://sysl.sh) has the documentation** — the tour, the guides, the library reference.
This page is only an index of what lives here.

```bash
brew tap sysl-lang/tap
brew trust sysl-lang/tap
brew install sysl-lang/tap/sysl
```

Homebrew requires per-tap trust and checks it *after* the download verifies, so without the middle
line the install fails at the end with a message that reads like a defect in the formula.

## The language

| repository | what it is |
|---|---|
| [**homebrew-tap**](https://github.com/sysl-lang/homebrew-tap) | the Homebrew formula |
| [**skitter-cli**](https://github.com/sysl-lang/skitter-cli) | a project tool — writes an Android application and then drives it: build, install, launch, follow the log. Written in sysl, and it drives git, curl, tar, Gradle and adb without a line of shell |
| [**svd**](https://github.com/sysl-lang/svd) | a build tool — turns a chip vendor's CMSIS SVD description into sysl constants |
| [**sysl**](https://github.com/sysl-lang/sysl) | the compiler, the standard library, and the guide programs |
| [**sysl.sh**](https://github.com/sysl-lang/sysl.sh) | the documentation site |

## Packages

Name one in your project's `package.hocon` and `sysl build` fetches it:

```hocon
dependencies {
  qcbor { git = "github.com/sysl-lang/qcbor", version = "0.4.0" }
}
```

| package | module you import | what it is |
|---|---|---|
| [**blake3**](https://github.com/sysl-lang/blake3) | `sh.sysl.blake3` | BLAKE3 — the hash, bound to the reference C implementation |
| [**box2d**](https://github.com/sysl-lang/box2d) | `sh.sysl.box2d` | 2D rigid body physics — bodies, shapes, the eight joints, contacts and queries, with every one of its thirty-one by-value structs checked against Box2D's own headers by the C compiler at build time |
| [**brotli**](https://github.com/sysl-lang/brotli) | `sh.sysl.brotli` | `Content-Encoding: br` at both ends — the encoding every browser asks for first, in one shot or in streams, with `compress` needing no buffer from the caller at all |
| [**cairo**](https://github.com/sysl-lang/cairo) | `sh.sysl.cairo` | 2D vector graphics that render to pixels or straight to a PDF, an SVG or a PostScript page, from the same drawing code |
| [**fft**](https://github.com/sysl-lang/fft) | `sh.sysl.fft` | the fast Fourier transform, generic over the float width — radix-2 Cooley-Tukey in place beside the O(n²) sum it is a rearrangement of, so the definition is what says the rearrangement is right |
| [**freertos**](https://github.com/sysl-lang/freertos) | `sh.sysl.freertos` | the real-time kernel, whole — tasks, queues, semaphores, timers, event groups, stream buffers, queue sets and the interrupt half, against whichever port and config the program was built with |
| [**gc**](https://github.com/sysl-lang/gc) | `sh.sysl.gc` | a tracing garbage collector over storage the caller supplies — no allocator, no operating system and no C underneath it, so it runs wherever sysl does |
| [**hiredis**](https://github.com/sysl-lang/hiredis) | `sh.sysl.redis` | Redis — the RESP reader and nothing else, so the socket stays the program's: one reader serves a plain connection, a TLS stream, a libuv callback, or a test with no network |
| [**imui**](https://github.com/sysl-lang/imui) | `sh.sysl.imui` | an immediate-mode user interface — no retained tree, no reconciler and no allocation at all, sized for a panel on a microcontroller |
| [**json**](https://github.com/sysl-lang/json) | `sh.sysl.json` | JSON, read and written — a document that owns itself, so every walk over one is a plain `match`, with numbers kept as written and errors that quote the line and point at the place |
| [**lmdb**](https://github.com/sysl-lang/lmdb) | `sh.sysl.lmdb` | the Lightning Memory-Mapped Database — ordered keys in a mapped file, where a read is a pointer into the map rather than a copy and a reader sees a snapshot nothing committed afterwards disturbs |
| [**libpq**](https://github.com/sysl-lang/libpq) | `sh.sysl.postgres` | PostgreSQL through its own client library, with no C of its own — the asynchronous path bound, so a query composes with an event loop rather than blocking on one |
| [**libuv**](https://github.com/sysl-lang/libuv) | `sh.sysl.libuv` | the event loop Node.js is built on — TCP, pipes, terminals, timers, signals, child processes, name resolution, a file system that does not block, and a thread pool a `&sync` closure crosses into |
| [**linalg**](https://github.com/sysl-lang/linalg) | `sh.sysl.linalg` | linear algebra over any element type that behaves like a number — one `solve`, `det`, `rank` and `inverse` running at the reals, at `f32` and over the complexes, with `Matrix[int]` refused at compile time by the one bound a signature cannot carry |
| [**linenoise**](https://github.com/sysl-lang/linenoise) | `sh.sysl.linenoise` | line editing for a terminal REPL |
| [**llhttp**](https://github.com/sysl-lang/llhttp) | `sh.sysl.llhttp` | HTTP/1.1 parsed, bound to Node's own parser with no shim — a callback finds its way home from the handle's own address, which works even for a C library with no user-data slot |
| [**miniz**](https://github.com/sysl-lang/miniz) | `sh.sysl.miniz` | deflate and inflate — zlib and raw streams, with the codec's own working state placed in storage the caller owns, so there is no allocator under it |
| [**nghttp2**](https://github.com/sysl-lang/nghttp2) | `sh.sysl.nghttp2` | HTTP/2 — HPACK and a session that speaks the framing layer, bound to the library curl, Apache and Envoy use, and fed bytes by the program so the socket, or the TLS stream, stays its own |
| [**monocypher**](https://github.com/sysl-lang/monocypher) | `sh.sysl.monocypher` | cryptography — authenticated encryption, key exchange, signatures, hashing |
| [**ogol**](https://github.com/sysl-lang/ogol) | `sh.sysl.ogol` | an onboard interactive language — Logo's arity-driven grammar with the brackets and the sigils taken off, small enough to live in a microcontroller's flash |
| [**openssl**](https://github.com/sysl-lang/openssl) | `sh.sysl.openssl` | TLS at both ends over memory BIOs, so OpenSSL never sees the socket — plus the digest signing a token needs, checked against RFC 7515's own published vectors rather than against OpenSSL's command line |
| [**parsing**](https://github.com/sysl-lang/parsing) | `sh.sysl.parsing` | the parts of a hand-written parser every grammar rewrites — a byte cursor, spans and a line table, literal reading with its escape rules, an indentation pass, binding powers, and diagnostics that quote the line and point at the place |
| [**pcre2**](https://github.com/sysl-lang/pcre2) | `sh.sysl.pcre2` | Perl-compatible regular expressions — and the binding that needed no shim at all, every PCRE2 function being a real symbol under an `_8` suffix where the header's plain names are macros |
| [**pico**](https://github.com/sysl-lang/pico) | `sh.sysl.pico` | the original Raspberry Pi Pico W — the same board surface as `pico2`, plus the atomics an Armv6-M core cannot do for itself |
| [**pico2**](https://github.com/sysl-lang/pico2) | `sh.sysl.pico2` | the Raspberry Pi Pico 2 W — the board's own entry points, for a program the C SDK hosts |
| [**plutovg**](https://github.com/sysl-lang/plutovg) | `sh.sysl.plutovg` | 2D vector graphics — paths, gradients, clipping and text, rasterized into memory and nothing else |
| [**png**](https://github.com/sysl-lang/png) | `sh.sysl.png` | PNG, read — the chunk layer, both checksums, DEFLATE and the row filters, with every colour type answering the same `Rgba` |
| [**qcbor**](https://github.com/sysl-lang/qcbor) | `sh.sysl.qcbor` | CBOR — RFC 8949 |
| [**qoi**](https://github.com/sysl-lang/qoi) | `sh.sysl.qoi` | lossless image compression — the Quite OK Image format, with no heap underneath it |
| [**qrcodegen**](https://github.com/sysl-lang/qrcodegen) | `sh.sysl.qrcodegen` | QR codes — every version, correction level and mask, written into buffers the caller supplies and no allocator anywhere |
| [**quickjs-ng**](https://github.com/sysl-lang/quickjs-ng) | `sh.sysl.quickjs` | JavaScript — a whole engine embedded, with no C shim: a value's destructor hands the engine's reference back so nothing calls free, and a sysl closure can be a JavaScript function |
| [**regex**](https://github.com/sysl-lang/regex) | `sh.sysl.regex` | POSIX regular expressions — and the worked example of binding a C library the machine already has |
| [**rp2040**](https://github.com/sysl-lang/rp2040) | `sh.sysl.rp2040` | the register map of the original Pico's chip, generated from the same SVD pipeline |
| [**rp2040blocks**](https://github.com/sysl-lang/rp2040blocks) | `sh.sysl.rp2040blocks` | that chip's GPIO and SPI — the hand-written half, because a generated package has nowhere for code to live |
| [**rp2350**](https://github.com/sysl-lang/rp2350) | `sh.sysl.rp2350` | the register map of the Pico 2's chip — every peripheral as constants, generated from Raspberry Pi's own SVD |
| [**sdl3**](https://github.com/sysl-lang/sdl3) | `sh.sysl.sdl3` | a window, an accelerated renderer, the event queue, keyboard and mouse, the clipboard, the system file dialog and queued audio |
| [**sdl3-image**](https://github.com/sysl-lang/sdl3-image) | `sh.sysl.sdl3_image` | image files decoded — PNG, JPEG and whatever else the installed SDL3_image was built with |
| [**sdl3-mixer**](https://github.com/sysl-lang/sdl3-mixer) | `sh.sysl.sdl3_mixer` | sound and music, mixed, looped, faded and stopped |
| [**sdl3-ttf**](https://github.com/sysl-lang/sdl3-ttf) | `sh.sysl.sdl3_ttf` | text rendered out of a font file, onto a surface or straight to a texture |
| [**sha3**](https://github.com/sysl-lang/sha3) | `sh.sysl.sha3` | SHA-3 and SHAKE — the Keccak family, bound to tiny_sha3 |
| [**skitter**](https://github.com/sysl-lang/skitter) | `sh.sysl.skitter` | the parts of an Android application that are not the application's — the system bars, which reach a program through JNI or not at all, the drawable rectangle they leave, and the orientation pair that does nothing when only half of it is set |
| [**slab**](https://github.com/sysl-lang/slab) | `sh.sysl.slab` | a slab allocator — one region of bytes carved into fixed blocks, the free list threaded through the free blocks' own storage, for the pool where every object is the same size |
| [**solder**](https://github.com/sysl-lang/solder) | `sh.sysl.solder` | the other onboard language — a Forth with a typed cell and reference counting, so an array is freed where it stops being referred to rather than at a collection nobody scheduled |
| [**sqlite3**](https://github.com/sysl-lang/sqlite3) | `sh.sysl.sqlite` | SQLite — prepared statements over the whole value model, integers, reals, text, blobs and null, with row ids, change counts, transactions and FTS5 where the machine's build has it |
| [**st7796**](https://github.com/sysl-lang/st7796) | `sh.sysl.st7796` | a 320×480 SPI display — the driver is three function pointers wide, so it belongs to no particular board |
| [**stb**](https://github.com/sysl-lang/stb) | `sh.sysl.stb` | images — nine formats decoded, four written and a resampler between them, bound to Sean Barrett's three headers, where a decode and an encode each answer a handle whose destructor gives stb's storage back |
| [**syslui**](https://github.com/sysl-lang/syslui) | `sh.sysl.ui` | a declarative retained user interface, for a machine with a heap |
| [**syslui-sdl**](https://github.com/sysl-lang/syslui-sdl) | `sh.sysl.ui_sdl` | syslUI's driver — the window, the frame loop, the events, the density and the on-screen keyboard, and one driver rather than two because of the ~120 lines an Android loop took, seventeen were about being on a phone |
| [**table**](https://github.com/sysl-lang/table) | `sh.sysl.table` | tables of text — grids, Markdown, matrices, laid out by the columns a character occupies |
| [**termbox2**](https://github.com/sysl-lang/termbox2) | `sh.sysl.termbox2` | a full-screen terminal interface — cells, colours, keys and the mouse |
| [**toml**](https://github.com/sysl-lang/toml) | `sh.sysl.toml` | TOML v1.0.0 read into a sysl value — validated against the specification's own conformance corpus, all 210 valid documents parsing to the value it names and all 501 invalid ones refused |
| [**webview**](https://github.com/sysl-lang/webview) | `sh.sysl.webview` | a native window with the platform's own browser engine in it — WKWebView, WebKitGTK or WebView2 rather than a bundled Chromium, where a page reaches sysl by calling a bound closure and gets a promise back |
| [**yaml**](https://github.com/sysl-lang/yaml) | `sh.sysl.yaml` | YAML 1.2 read into a sysl value, bound to libyaml |
| [**zephyr**](https://github.com/sysl-lang/zephyr) | `sh.sysl.zephyr` | the other real-time kernel — threads, semaphores, mutexes, condition variables, events, message queues, timers and work queues, every size measured out of the kernel your own Kconfig produced |
| [**zstd**](https://github.com/sysl-lang/zstd) | `sh.sysl.zstd` | Zstandard — one shot or streaming, dictionaries, a level dial from -131072 to 22, and two allocations per compression, linked against the machine's libzstd |

## Programs

Complete programs rather than libraries — the shortest answers to what a sysl project looks like.

| repository | what it shows |
|---|---|
| [**android-bouncing**](https://github.com/sysl-lang/android-bouncing) | androidkit's demo — a boxful of shapes under Box2D that never settles, tap to add another, and neither the physics package nor the SDL one knows it is on a phone |
| [**androidkit**](https://github.com/sysl-lang/androidkit) | sysl on a phone, and the template to start from — one line of text on the screen and the machinery that gets it there, with no C anywhere, because `@export` defines the `SDL_main` that Android looks for |
| [**box2d-demo**](https://github.com/sysl-lang/box2d-demo) | three packages and nothing between them — grab a body and throw it, watch the pile go to sleep, with box2d deciding where everything is, cairo cutting the shapes and SDL3 turning the crank |
| [**cairo-demo**](https://github.com/sysl-lang/cairo-demo) | one drawing function called four times — the same chart written to a PNG, a PDF, an SVG and a PostScript page, which is the whole argument for cairo in one program |
| [**cairo-sdl3-demo**](https://github.com/sysl-lang/cairo-sdl3-demo) | two packages that need each other — cairo rasterizes a tumbling gear train into a buffer SDL3 shows as a texture, and the 3D is exact rather than faked because an orthographic view of a flat object is an affine matrix |
| [**imui-demo**](https://github.com/sysl-lang/imui-demo) | a user interface rather than a picture — a 320×480 settings panel drawn by cairo through `imui`'s painter trait, repainting only the horizontal bands that changed, which is 30 rows of 480 on an idle frame |
| [**monocypher-example**](https://github.com/sysl-lang/monocypher-example) | one dependency — two people agree a key over an insecure channel, then send a signed, sealed message |
| [**nghttp2-demo**](https://github.com/sysl-lang/nghttp2-demo) | HTTP/2 over TLS, both ends in one process and no socket anywhere — the seam between the openssl and nghttp2 packages, which were written apart and meet here |
| [**ogol-host**](https://github.com/sysl-lang/ogol-host) | a language and its console — the hosted half, at a terminal |
| [**ogol-pico**](https://github.com/sysl-lang/ogol-pico) | the same console on the original Pico W — three lines of source apart from the Pico 2 W program below, which is what a shared `session` is worth |
| [**ogol-pico2**](https://github.com/sysl-lang/ogol-pico2) | that same program on a Raspberry Pi Pico 2 W over USB serial — the loop is the language's, so only the streams differ |
| [**pico-scratch**](https://github.com/sysl-lang/pico-scratch) | sysl on a microcontroller — a blink program and a REPL on a Pico 2 W over USB serial, with no C in either project |
| [**picokit**](https://github.com/sysl-lang/picokit) | one carrier board's glue — the pin map, the registers and the panel of a Pico Breadboard Kit, which is what keeps a display driver from becoming a package for one board |
| [**sdl3-demo**](https://github.com/sysl-lang/sdl3-demo) | four dependencies, and a graphical one — a bouncing ball with a trail, text, a note per bounce and a screenshot key, with no asset file anywhere |
| [**skitter-app**](https://github.com/sysl-lang/skitter-app) | an Android application configured in two lines — the project `skitter init` writes, where the activity, the JNI symbol and the build are Skitter's, so `applicationId` is a string nothing else has to agree with |
| [**solder-host**](https://github.com/sysl-lang/solder-host) | the other language and its console — thirty lines, none of them about SOLDER, because the read-run-print loop lives in the package where every console can share it |
| [**solder-pico2**](https://github.com/sysl-lang/solder-pico2) | the same trick for the other language — SOLDER on a Pico 2 W in 405 KB of flash, the board console being the desktop one with its first few lines swapped |
| [**sqlite-repl**](https://github.com/sysl-lang/sqlite-repl) | three dependencies — a SQL prompt where linenoise reads the line, sqlite3 runs it and table lays the answer out |
| [**syslui-android**](https://github.com/sysl-lang/syslui-android) | the toolkit on a phone — a form, a text area and a keyboard that comes up when you tap into one, and the thing a desktop could never have found: a tap is a press and a release arriving between two frames, so until the toolkit recorded one no field could be typed into at all |
| [**syslui-demo**](https://github.com/sysl-lang/syslui-demo) | syslUI's worked example — a counter and a scrolling list against SDL3, and the benchmark that priced a rebuild at one allocation a node |
| [**zephyr-demo**](https://github.com/sysl-lang/zephyr-demo) | a sysl program under Zephyr's CMake, and the binding's own suite — 70 assertions against a real kernel booted under QEMU, because a kernel image is the only place they can run |
| [**webview-demo**](https://github.com/sysl-lang/webview-demo) | a window, a page, and two sysl closures the JavaScript calls — the part of `sh.sysl.webview` no test suite can reach, because opening a window needs a window server |
