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
| [**harness**](https://github.com/sysl-lang/harness) | `sh.sysl.harness` | a test framework that runs on the target — no allocator, no operating system |
| [**qcbor**](https://github.com/sysl-lang/qcbor) | `sh.sysl.qcbor` | CBOR — RFC 8949 |
| [**monocypher**](https://github.com/sysl-lang/monocypher) | `sh.sysl.monocypher` | cryptography — authenticated encryption, key exchange, signatures, hashing |
| [**sqlite3**](https://github.com/sysl-lang/sqlite3) | `sh.sysl.sqlite` | SQLite |
| [**linenoise**](https://github.com/sysl-lang/linenoise) | `sh.sysl.linenoise` | line editing for a terminal REPL |

The package and the module are deliberately different names: a package is a unit of distribution and
a module is a unit of code, which is why `sqlite3` is imported as `sh.sysl.sqlite`.

**Only sqlite3 needs anything installed.** `harness` is sysl all the way down and binds nothing at
all; the other three carry their C and compile it as part of the build, so there is no `-l` flag and
nothing to install first.

[**monocypher-example**](https://github.com/sysl-lang/monocypher-example) is a complete worked program
with a dependency, and the shortest answer to what a sysl project looks like.
