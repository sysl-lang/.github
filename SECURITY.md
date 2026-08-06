# Security policy

This policy covers every repository under [sysl-lang](https://github.com/sysl-lang) — the compiler
and its standard library, the documentation site, and the packages.

## Reporting a vulnerability

**Email [security@sysl.sh](mailto:security@sysl.sh)** rather than opening an issue. An issue is
public from the moment it is filed, which for a vulnerability means telling everyone before there is
anything to upgrade to.

Useful to include, in whatever detail you have:

- what you did — the smallest input, source file or command that shows it;
- what happened, and what you expected instead;
- which release, from `sysl --version`, and which platform;
- whether you think it is reachable from untrusted input, and how.

A proof of concept helps and is not required. A clear description of the mechanism is worth more
than a working exploit.

## What to expect

sysl is written by one person, so this is a best-effort promise rather than a service level: mail is
read, reports are acknowledged, and a fix or an explanation follows. If a report turns out to be
something other than a vulnerability, it will be handled as an ordinary bug and moved to a public
issue — with your agreement first.

Credit is given in the release notes unless you would rather it were not.

## Supported versions

sysl is pre-1.0 and moves quickly. **Only the most recent release is supported**, and a fix arrives
as a new release rather than as a patch to an older one.

| version | supported |
|---|---|
| the latest release | yes |
| anything earlier | no — upgrade |

## What is in scope

A memory-safety failure, a miscompile, or a crash the compiler can be driven to by input a program
would plausibly meet. Also anything in the bindings under this organization that reaches C
incorrectly — a length dropped, a lifetime got wrong, a buffer written past.

**Vendored C is upstream's, but tell us anyway.** Several packages carry their dependency's source
rather than linking it, so a vulnerability in QCBOR, Monocypher, linenoise or SQLite reaches users
through this organization too. Report it upstream where you can; a note here means the vendored copy
gets updated rather than sitting at a version nobody rechecked.

**Not in scope:** a program that misuses a raw pointer or an `extern` and crashes. `*T` and `extern`
are the language's unchecked constructs and are documented as such — a program that reaches for them
has taken responsibility for what it does with them.
