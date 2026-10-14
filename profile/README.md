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
| [**sysl**](https://github.com/sysl-lang/sysl) | the compiler, written in sysl — it ships as `sysl` and builds itself, with the standard library and the language reference |
| [**sysl-bootstrap**](https://github.com/sysl-lang/sysl-bootstrap) | archived (retired 2026-10-09) — the former bootstrap compiler, written in Scala |
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
| [**cstd**](https://github.com/sysl-lang/cstd) | `sh.sysl.cstd` | a C standard library written in sysl, for machines that have none: `string.h`, `ctype.h`, `stdlib.h` and the printf family, exported under their C names with headers for `-nostdinc`, so a vendored C package builds on a bare board — plus a Linux half (crt0, the system calls, `malloc` over `brk`) that runs a plain C program on keel |
| [**dal**](https://github.com/sysl-lang/dal) | `sh.sysl.dal` | a dynamic numeric tower — 64-bit integers that grow into big ones, exact rationals and doubles, with promotion, demotion and what `7 / 2` means chosen by a policy value, and comparison across kinds that never rounds |
| [**dsp**](https://github.com/sysl-lang/dsp) | `sh.sysl.dsp` | audio DSP written once for `q15`, `q31` and `f32` — RBJ biquads that round once per sample with error feedback, FIR on `SMLAD`, clipping gain and mix, a phase-accumulator oscillator on a sine table built while compiling, an exact ADSR, meters, and windows into `fft`, with no heap |
| [**duckdb**](https://github.com/sysl-lang/duckdb) | `sh.sysl.duckdb` | DuckDB — an in-process analytical database, where a result column is a view of the engine's own array (`[]const i64`, `[]const f64`, `[]const i128`) rather than a copy, with prepared statements, the appender, and scalar functions written in sysl that run on DuckDB's worker threads |
| [**fat**](https://github.com/sysl-lang/fat) | `sh.sysl.fat` | FAT16 and FAT32 over a block-device trait, with no operating system, allocator or float, so one source serves a kernel's `/boot`, a microcontroller's SD card and the host — and `mkfs.fat`, which picks FAT16 or FAT32 by the volume's size from the specification's own tables, checked by both macOS's and Linux's fsck |
| [**fft**](https://github.com/sysl-lang/fft) | `sh.sysl.fft` | the fast Fourier transform, generic over the float width — radix-2 Cooley-Tukey in place beside the O(n²) sum it is a rearrangement of, so the definition is what says the rearrangement is right |
| [**pitch**](https://github.com/sysl-lang/pitch) | `sh.sysl.pitch` | monophonic pitch detection — YIN in plain time-domain arithmetic, generic over the float width, reading a pluck whose second harmonic outweighs its fundamental at the fundamental, to a fraction of a cent; with the note and cents arithmetic a tuner wraps around it, and nothing allocated per frame |
| [**freertos**](https://github.com/sysl-lang/freertos) | `sh.sysl.freertos` | the real-time kernel, whole — tasks, queues, semaphores, timers, event groups, stream buffers, queue sets and the interrupt half, against whichever port and config the program was built with |
| [**gc**](https://github.com/sysl-lang/gc) | `sh.sysl.gc` | a tracing garbage collector over storage the caller supplies — no allocator, no operating system and no C underneath it, so it runs wherever sysl does |
| [**hiredis**](https://github.com/sysl-lang/hiredis) | `sh.sysl.redis` | Redis — the RESP reader and nothing else, so the socket stays the program's: one reader serves a plain connection, a TLS stream, a libuv callback, or a test with no network |
| [**highlighter**](https://github.com/sysl-lang/highlighter) | `sh.sysl.highlighter` | syntax highlighting driven by VS Code's own TextMate grammars, on the real Oniguruma — HTML with classes or a theme's colours, or the tokens themselves for a renderer of your own, and a hook that hands Markdown code blocks to it |
| [**imui**](https://github.com/sysl-lang/imui) | `sh.sysl.imui` | an immediate-mode user interface — no retained tree, no reconciler and no allocation at all, sized for a panel on a microcontroller |
| [**json**](https://github.com/sysl-lang/json) | `sh.sysl.json` | JSON, read and written — a document that owns itself, so every walk over one is a plain `match`, with numbers kept as written and errors that quote the line and point at the place |
| [**kairos**](https://github.com/sysl-lang/kairos) | `sh.sysl.kairos` | an event loop for a microcontroller — sources an interrupt raises with one atomic OR, one-shot and repeating timers, idle and check handles, and a platform trait for the clock and the sleep; libuv's shape, builds for a bare Cortex-M |
| [**lmdb**](https://github.com/sysl-lang/lmdb) | `sh.sysl.lmdb` | the Lightning Memory-Mapped Database — ordered keys in a mapped file, where a read is a pointer into the map rather than a copy and a reader sees a snapshot nothing committed afterwards disturbs |
| [**libregexp**](https://github.com/sysl-lang/libregexp) | `sh.sysl.libregexp` | ECMAScript regular expressions — QuickJS's own engine, vendored, so a board gets JavaScript's dialect with nothing installed; positions are byte offsets into UTF-8, and every match runs under a step budget, so a pathological pattern answers rather than hangs |
| [**libgit2**](https://github.com/sysl-lang/libgit2) | `sh.sysl.libgit2` | git as a library — repositories, the index, commits and trees, branches and tags, checkout, history walks, diffs with patch text, status, blame, config, the stash and local clones, with closures for progress, walks and credentials, checked against the `git` CLI |
| [**libpq**](https://github.com/sysl-lang/libpq) | `sh.sysl.postgres` | PostgreSQL through its own client library, with no C of its own — the asynchronous path bound, so a query composes with an event loop rather than blocking on one |
| [**libuv**](https://github.com/sysl-lang/libuv) | `sh.sysl.libuv` | the event loop Node.js is built on — TCP, pipes, terminals, timers, signals, child processes, name resolution, a file system that does not block, and a thread pool a `&sync` closure crosses into |
| [**libwebp**](https://github.com/sysl-lang/libwebp) | `sh.sysl.libwebp` | WebP, read and written — probe, decode, lossy and lossless encode against the machine's libwebp, cross-checked byte for byte against `cwebp` and `dwebp`; animation is refused by name rather than half-done |
| [**linalg**](https://github.com/sysl-lang/linalg) | `sh.sysl.linalg` | linear algebra over any element type that behaves like a number — one `solve`, `det`, `rank` and `inverse` running at the reals, at `f32` and over the complexes, with `Matrix[int]` refused at compile time by the one bound a signature cannot carry |
| [**linenoise**](https://github.com/sysl-lang/linenoise) | `sh.sysl.linenoise` | line editing for a terminal REPL |
| [**llhttp**](https://github.com/sysl-lang/llhttp) | `sh.sysl.llhttp` | HTTP/1.1 parsed, bound to Node's own parser with no shim — a callback finds its way home from the handle's own address, which works even for a C library with no user-data slot |
| [**markdown**](https://github.com/sysl-lang/markdown) | `sh.sysl.markdown` | CommonMark 0.31.2, plus what GitHub renders, plus math, mermaid and cmark-style smart punctuation — one arena of nodes with a source span on each, an HTML renderer matching the reference implementation byte for byte, and an open `Extension` trait; in progress, checked against the spec's 652 examples |
| [**miniaudio**](https://github.com/sysl-lang/miniaudio) | `sh.sysl.miniaudio` | audio playback and capture — miniaudio, vendored, which finds PipeWire, PulseAudio, ALSA, CoreAudio, AAudio or WASAPI when the program runs rather than when it links, so one build plays wherever there is sound |
| [**miniz**](https://github.com/sysl-lang/miniz) | `sh.sysl.miniz` | deflate and inflate — zlib and raw streams, with the codec's own working state placed in storage the caller owns, so there is no allocator under it |
| [**mlt**](https://github.com/sysl-lang/mlt) | `sh.sysl.mlt` | the MLT multimedia framework — profiles, producers, filters, transitions, playlists and tractors rendered through its consumers, frames' pixels and samples as slices, and events from the render thread into a `&sync` closure |
| [**musicbox**](https://github.com/sysl-lang/musicbox) | `sh.sysl.musicbox` | music from text — a notation parser and a fixed-point additive synthesizer that fills a buffer and knows no audio API, so the same score plays on a desktop, a phone or a microcontroller |
| [**musicbox-miniaudio**](https://github.com/sysl-lang/musicbox-miniaudio) | `sh.sysl.musicbox_miniaudio` | musicbox played through miniaudio — the two packages meet here so neither needs the other, and a score reaches the speakers of a desktop or a phone with nothing installed |
| [**nghttp2**](https://github.com/sysl-lang/nghttp2) | `sh.sysl.nghttp2` | HTTP/2 — HPACK and a session that speaks the framing layer, bound to the library curl, Apache and Envoy use, and fed bytes by the program so the socket, or the TLS stream, stays its own |
| [**monocypher**](https://github.com/sysl-lang/monocypher) | `sh.sysl.monocypher` | cryptography — authenticated encryption, key exchange, signatures, hashing |
| [**ogol**](https://github.com/sysl-lang/ogol) | `sh.sysl.ogol` | an onboard interactive language — Logo's arity-driven grammar with the brackets and the sigils taken off, small enough to live in a microcontroller's flash |
| [**oniguruma**](https://github.com/sysl-lang/oniguruma) | `sh.sysl.oniguruma` | Oniguruma regular expressions — the engine TextMate grammars are written for, with vscode-oniguruma's dialect as the default and a multi-pattern scanner shaped for a tokenizer; positions are byte offsets into UTF-8, and every search runs under a retry budget |
| [**openssl**](https://github.com/sysl-lang/openssl) | `sh.sysl.openssl` | TLS at both ends over memory BIOs, so OpenSSL never sees the socket — plus the digest signing a token needs, checked against RFC 7515's own published vectors rather than against OpenSSL's command line |
| [**parsing**](https://github.com/sysl-lang/parsing) | `sh.sysl.parsing` | the parts of a hand-written parser every grammar rewrites — a byte cursor, spans and a line table, literal reading with its escape rules, an indentation pass, binding powers, and diagnostics that quote the line and point at the place |
| [**pcre2**](https://github.com/sysl-lang/pcre2) | `sh.sysl.pcre2` | Perl-compatible regular expressions — and the binding that needed no shim at all, every PCRE2 function being a real symbol under an `_8` suffix where the header's plain names are macros |
| [**pico**](https://github.com/sysl-lang/pico) | `sh.sysl.pico` | the original Raspberry Pi Pico W — the same board surface as `pico2`, plus the atomics an Armv6-M core cannot do for itself |
| [**pico2**](https://github.com/sysl-lang/pico2) | `sh.sysl.pico2` | the Raspberry Pi Pico 2 W — the board's own entry points, for a program the C SDK hosts |
| [**plutovg**](https://github.com/sysl-lang/plutovg) | `sh.sysl.plutovg` | 2D vector graphics — paths, gradients, clipping and text, rasterized into memory and nothing else |
| [**png**](https://github.com/sysl-lang/png) | `sh.sysl.png` | PNG read and write, in pure sysl — every colour type and depth, Adam7, the ancillary chunks, APNG frames, and a zlib-grade DEFLATE compressor (levels 0–9) |
| [**pool**](https://github.com/sysl-lang/pool) | `sh.sysl.pool` | a work-stealing scheduler in two layers: the Chase–Lev deque with the PPoPP 2013 weak-memory orderings, `@no_alloc` and OS-free for a kernel's per-core run queues, and a thread pool on it — spawn/join, scoped fork-join, `parallel_for`, `map_reduce`, parking without lost wakeups — level with OpenMP to 18 cores |
| [**qcbor**](https://github.com/sysl-lang/qcbor) | `sh.sysl.qcbor` | CBOR — RFC 8949 |
| [**qoi**](https://github.com/sysl-lang/qoi) | `sh.sysl.qoi` | lossless image compression — the Quite OK Image format, with no heap underneath it |
| [**qrcodegen**](https://github.com/sysl-lang/qrcodegen) | `sh.sysl.qrcodegen` | QR codes — every version, correction level and mask, written into buffers the caller supplies and no allocator anywhere |
| [**quaternion**](https://github.com/sysl-lang/quaternion) | `sh.sysl.quaternion` | 3D rotation by unit quaternions at `real` and `f32`, from one body bounded by `sysl.math.Float`: the non-commuting Hamilton product, matrices, Euler angles with gimbal lock handled, short-path SLERP, and the gyroscope integration step an IMU filter runs on a Cortex-M4F |
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
| [**squiggly**](https://github.com/sysl-lang/squiggly) | `sh.sysl.squiggly` | templates — `{{ … }}` text rendered against a value, with `if`/`for`/`match`, layouts, partials, pipes, lambdas and 74 builtins, every error naming its line and column; the language juicer's themes are written in |
| [**st7796**](https://github.com/sysl-lang/st7796) | `sh.sysl.st7796` | a 320×480 SPI display — the driver is three function pointers wide, so it belongs to no particular board |
| [**stb**](https://github.com/sysl-lang/stb) | `sh.sysl.stb` | images — nine formats decoded, four written and a resampler between them, bound to Sean Barrett's three headers, where a decode and an encode each answer a handle whose destructor gives stb's storage back |
| [**syslui**](https://github.com/sysl-lang/syslui) | `sh.sysl.ui` | a declarative retained user interface, for a machine with a heap |
| [**syslui-sdl**](https://github.com/sysl-lang/syslui-sdl) | `sh.sysl.ui_sdl` | syslUI's driver — the window, the frame loop, the events, the density and the on-screen keyboard, and one driver rather than two because of the ~120 lines an Android loop took, seventeen were about being on a phone |
| [**table**](https://github.com/sysl-lang/table) | `sh.sysl.table` | tables of text — grids, Markdown, matrices, laid out by the columns a character occupies |
| [**termbox2**](https://github.com/sysl-lang/termbox2) | `sh.sysl.termbox2` | a full-screen terminal interface — cells, colours, keys and the mouse |
| [**toml**](https://github.com/sysl-lang/toml) | `sh.sysl.toml` | TOML v1.0.0 read into a sysl value — validated against the specification's own conformance corpus, all 210 valid documents parsing to the value it names and all 501 invalid ones refused |
| [**tree-sitter**](https://github.com/sysl-lang/tree-sitter) | `sh.sysl.treesitter` | tree-sitter, the incremental parser behind editors' syntax trees: parsers, trees, nodes, cursors, queries with predicates as data, edit and re-parse with changed ranges, a closure as the reader and the logger, checked against the tree-sitter CLI |
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
| [**httpd**](https://github.com/sysl-lang/httpd) | an async HTTP/1.1 server — one task per connection on kairos's libuv loop, llhttp parsing pipelined requests across reads, timeouts and shutdown by cancelling tasks, within 1.5× of the same server in C |
| [**imui-demo**](https://github.com/sysl-lang/imui-demo) | a user interface rather than a picture — a 320×480 settings panel drawn by cairo through `imui`'s painter trait, repainting only the horizontal bands that changed, which is 30 rows of 480 on an idle frame |
| [**keel**](https://github.com/sysl-lang/keel) | a research kernel for aarch64 under QEMU, written in sysl to find where sysl falls short — four cores, processes, signals, threads, a journaled filesystem and Linux's system-call numbers, so Alpine's unmodified busybox runs from its shell; every gap it hit is written up in `FINDINGS.md` and fixed in the compiler rather than worked around |
| [**monocypher-example**](https://github.com/sysl-lang/monocypher-example) | one dependency — two people agree a key over an insecure channel, then send a signed, sealed message |
| [**musicbox-android**](https://github.com/sysl-lang/musicbox-android) | a music box on a phone — one button and a tune written as text, rendered by musicbox and played through miniaudio's AAudio stream, which miniaudio opens with `dlopen` at run time, so the app carries no audio library and no C |
| [**musicbox-pico**](https://github.com/sysl-lang/musicbox-pico) | the same synthesizer on a Raspberry Pi Pico 2 W — a score rendered on the board and played out of one GPIO as PWM audio, the DMA engine pacing a self-wrapping ring with no interrupt and no C |
| [**nghttp2-demo**](https://github.com/sysl-lang/nghttp2-demo) | HTTP/2 over TLS, both ends in one process and no socket anywhere — the seam between the openssl and nghttp2 packages, which were written apart and meet here |
| [**ogol-host**](https://github.com/sysl-lang/ogol-host) | a language and its console — the hosted half, at a terminal |
| [**ogol-pico**](https://github.com/sysl-lang/ogol-pico) | the same console on the original Pico W — three lines of source apart from the Pico 2 W program below, which is what a shared `session` is worth |
| [**ogol-pico2**](https://github.com/sysl-lang/ogol-pico2) | that same program on a Raspberry Pi Pico 2 W over USB serial — the loop is the language's, so only the streams differ |
| [**orbits**](https://github.com/sysl-lang/orbits) | the solar system as a 3D n-body problem in f64 — RK4, leapfrog and Yoshida switchable, Kepler's equation and orbital elements, tracks drawn through a quaternion camera by cairo; within 4e-5 AU of JPL Horizons after ten years, the gap being relativity and the asteroids, and within 1.2× of the same force loop in C |
| [**pico-scratch**](https://github.com/sysl-lang/pico-scratch) | sysl on a microcontroller — a blink program and a REPL on a Pico 2 W over USB serial, with no C in either project |
| [**picokit**](https://github.com/sysl-lang/picokit) | one carrier board's glue — the pin map, the registers and the panel of a Pico Breadboard Kit, which is what keeps a display driver from becoming a package for one board |
| [**raytrace**](https://github.com/sysl-lang/raytrace) | a path tracer in the scope of Shirley's two books — spheres, quads and meshes behind a BVH, materials as trait objects, rows on a thread pool, and an image byte-identical to its own C port at any thread count |
| [**sdl3-demo**](https://github.com/sysl-lang/sdl3-demo) | four dependencies, and a graphical one — a bouncing ball with a trail, text, a note per bounce and a screenshot key, with no asset file anywhere |
| [**skiff**](https://github.com/sysl-lang/skiff) | keel's microcontroller sibling — a real-time kernel for chips with no MMU, starting on the STM32H747, whose Cortex-M7 and Cortex-M4 each run their own copy and talk by message passing; written in sysl to find where sysl falls short on a bare board |
| [**skitter-app**](https://github.com/sysl-lang/skitter-app) | an Android application configured in two lines — the project `skitter init` writes, where the activity, the JNI symbol and the build are Skitter's, so `applicationId` is a string nothing else has to agree with |
| [**solder-host**](https://github.com/sysl-lang/solder-host) | the other language and its console — thirty lines, none of them about SOLDER, because the read-run-print loop lives in the package where every console can share it |
| [**solder-pico2**](https://github.com/sysl-lang/solder-pico2) | the same trick for the other language — SOLDER on a Pico 2 W in 405 KB of flash, the board console being the desktop one with its first few lines swapped |
| [**sqlite-repl**](https://github.com/sysl-lang/sqlite-repl) | three dependencies — a SQL prompt where linenoise reads the line, sqlite3 runs it and table lays the answer out |
| [**syslui-android**](https://github.com/sysl-lang/syslui-android) | the toolkit on a phone — a form, a text area and a keyboard that comes up when you tap into one, and the thing a desktop could never have found: a tap is a press and a release arriving between two frames, so until the toolkit recorded one no field could be typed into at all |
| [**syslui-demo**](https://github.com/sysl-lang/syslui-demo) | syslUI's worked example — a counter and a scrolling list against SDL3, and the benchmark that priced a rebuild at one allocation a node |
| [**tuner**](https://github.com/sysl-lang/tuner) | a chromatic guitar tuner on a phone — the microphone drained once a frame into a pitch pipeline with no SDL in it, so the median, the hop and the one-second hold are tested on synthesized strings rather than on somebody's guitar |
| [**zephyr-demo**](https://github.com/sysl-lang/zephyr-demo) | a sysl program under Zephyr's CMake, and the binding's own suite — 70 assertions against a real kernel booted under QEMU, because a kernel image is the only place they can run |
| [**webview-demo**](https://github.com/sysl-lang/webview-demo) | a window, a page, and two sysl closures the JavaScript calls — the part of `sh.sysl.webview` no test suite can reach, because opening a window needs a window server |
