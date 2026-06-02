# Example tome

A small, fully offline tome used by Grimoire's smoke tests and local demos. Add it with:

```sh
grm tome add ./example --ref main
```

It registers itself as `example` (the name comes from `tome.rn`).

## Layout

- `tome.rn` — the tome manifest. Its `packages` block points at a local `dist/` directory
  (`format: "local"`), the directory `grm tome build` would publish into.
- `dist/` — git-ignored publish directory holding the package index and prebuilt archives.
  This tome ships none (it builds from source), so `dist/` is absent until you build.
- `runes/` — package definitions:
  - `hello` — minimal package, no dependencies.
  - `greeter` — has a runtime dependency on `hello`.
  - `forge` — has a build dependency on `hello`.
  - `bundle` — builds from `sources/payload.txt`, verified against its checksum.
- `sources/` — source artifacts fetched and checksum-verified during a build.

## Try it

```sh
grm install hello
grm install greeter   # also installs hello
grm install bundle    # verifies the source checksum first
```
