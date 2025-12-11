# @reliverse/repackr

> @reliverse/repackr is your high-level, cross-platform archive toolkit — a modern alternative to existing tools that actually feels like it's from this decade.

[💖 GitHub Sponsors](https://github.com/sponsors/blefnk) • [📦 NPM](https://npmjs.com/package/@reliverse/repackr) • [✨ GitHub](https://github.com/reliverse/repackr) • [📚 Docs](https://blefnk.reliverse.org/blog/my-products/repackr)

## 💡 What is Repackr?

- 🎒 CLI & SDK to create, extract, and inspect archives
- 🧩 Supports `.zip`, `.tar`, `.tar.gz`, `.tgz`, `.tar.br`, `.tar.xz`, `.7z`, and more (via plugins)
- ⚡️ Works out of the box — no system-level dependencies required
- 🛠 Fully type-safe SDK for Node.js (with ESM-first globby support)
- 🌍 Cross-platform and framework-agnostic (bun, Node, CI, etc)
- 🔐 Optional password-based encryption (coming soon)

## 🛠 Use Cases

- Bundle a build directory before uploading to your storage bucket
- Extract packages in a CI step
- Create distributable `.zip` files in CLI tools
- Build your own installer or updater logic
- Replace platform-specific deps like `7z`, `tar`, or `zip` in your scripts

## 🚀 Quick Start

### CLI

Install globally:

```bash
bun i -g @reliverse/repackr-cli
# bun • pnpm • yarn • npm
```

Or just run without any installation:

```bash
bunx @reliverse/repackr-cli
# bunx • pnpx • npx
```

### Native App

> Coming soon

### SDK

```bash
bun add @reliverse/repackr
# bun • pnpm • yarn • npm
```

## ✨ CLI Usage

### Pack files into an archive

```bash
repackr pack ./dist --format zip --out ./build/app.zip
```

### Extract archive

```bash
repackr unpack ./build/app.zip --out ./extracted
```

### Inspect archive contents

```bash
repackr list ./build/app.zip
```

### CLI Options

| Command        | Description                      |
|----------------|----------------------------------|
| `pack`         | Create archive from directory    |
| `unpack`       | Extract archive to destination   |
| `list`         | View archive contents            |
| `--format`     | Choose format (`zip`, `tar`, etc)|
| `--out`        | Set output path or folder        |
| `--verbose`    | Enable verbose logs              |

## 🧠 SDK Usage

```ts
import { pack, unpack, list } from "@reliverse/repackr";

await pack({
  src: "./dist",
  format: "zip",
  dest: "./build/app.zip",
});

await unpack({
  src: "./build/app.zip",
  dest: "./tmp/unpacked",
});

const files = await list({ src: "./build/app.zip" });
console.log(files);
```

All options are strongly typed, and format plugins are extensible.

## 🎯 Why Repackr?

> You deserve better than platform-specific hacks and ancient CLI wrappers.

- 📦 Everything in JS/TS — no external binaries required
- 🛡 Safe paths (no extraction to `/etc`)
- 🌐 Built-in format adapters (extensible via plugins)
- 🔄 Deterministic output archives
- ✨ Designed for modern build pipelines

## 🧩 Supported Formats

| Format    | Read | Write | Notes                            |
|-----------|------|-------|----------------------------------|
| `.zip`    | 🟡   | 🟡    | Fully supported out of the box   |
| `.tar`    | 🟡   | 🟡    |                                 |
| `.tar.gz` | 🟡   | 🟡    | Alias: `.tgz`                    |
| `.tar.br` | 🟡   | 🟡    | Brotli-compressed tar            |
| `.tar.xz` | 🟡   | 🟡    | XZ compression                   |
| `.7z`     | 🟡   | 🟡    | Read only for now (write soon)  |

_Plugin system coming soon for rar, iso, etc._

## 🧪 Playground

```bash
git clone https://github.com/reliverse/repackr
cd repackr
bun i
bun dev
```

## 💬 Example Use in CI/CD

```yaml
- name: Compress build
  run: repackr pack ./dist --format zip --out ./release.zip

- name: Upload artifact
  uses: actions/upload-artifact
  with:
    name: webapp
    path: ./release.zip
```

## 🔋 Related Projects

- [`@reliverse/runnr`](https://npmjs.com/package/@reliverse/runnr) — Modern process runner
- [`@reliverse/prompts`](https://npmjs.com/package/@reliverse/prompts) — Interactive CLI prompt library
- [`@reliverse/relinka`](https://npmjs.com/package/@reliverse/relinka) — Styled logger with config

## 🫶 Show some love

If Repackr saved you a few lines of bash or minutes of debugging:

- ⭐ [Star the repo](https://github.com/reliverse/repackr)
- 💖 [Sponsor on GitHub](https://github.com/sponsors/blefnk)
- 🔁 Share it with a fellow builder

## 📄 License

MIT © 2025 [blefnk (Nazar Kornienko)](https://github.com/blefnk)
