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
| [**pico2**](https://github.com/sysl-lang/pico2) | `sh.sysl.pico2` | the Raspberry Pi Pico 2 W — the board's own entry points, for a program the C SDK hosts |

The package and the module are deliberately different names: a package is a unit of distribution and
a module is a unit of code, which is why `sqlite3` is imported as `sh.sysl.sqlite`.

**Two of them need something installed** — `sqlite3` wants SQLite, and `pico2` wants the Raspberry Pi
Pico SDK. The rest get there three different ways. `table` is sysl all the way down and binds nothing
at all. `regex` binds the C library every hosted machine already has, so it carries a shim for what
only a header knows and no upstream source whatever. `qcbor`, `qoi`, `monocypher`, `linenoise` and
`termbox2` carry their C and compile it as part of the build. None of the nine asks you to write an
`-l` flag: where a library has to be linked, the package's own header says so and the annotation
travels inside the artifact.

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
| [**pico-scratch**](https://github.com/sysl-lang/pico-scratch) | sysl on a microcontroller — a blink program and a REPL on a Pico 2 W over USB serial, with no C in either project |
