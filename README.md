# Example tome

A small, fully offline tome used by Grimoire's smoke tests and local demos. Add it with:

```sh
grimoire tome add ./example --ref main
```

It registers itself as `example` (the name comes from `tome.rn`).

## Layout

- `tome.rn` — the tome manifest (package index).
- `index.nuon` — binary package index. Empty here, so installs build from source.
- `runes/` — package definitions:
  - `hello` — minimal package, no dependencies.
  - `greeter` — has a runtime dependency on `hello`.
  - `forge` — has a build dependency on `hello`.
  - `bundle` — builds from `sources/payload.txt`, verified against its checksum.
- `sources/` — source artifacts fetched and checksum-verified during a build.

## Try it

```sh
grimoire install hello
grimoire install greeter   # also installs hello
grimoire install bundle    # verifies the source checksum first
```
