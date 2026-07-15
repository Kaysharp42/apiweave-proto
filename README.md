# @apiweave/proto

Generated TypeScript + ConnectRPC (protobuf-es) stubs for the **APIWeave Cloud**
wire contract. Published for both the public [`apiweave`](https://github.com/Kaysharp42/apiweave)
desktop app and the private `apiweave-cloud` backend to consume from one place.

## Install

```jsonc
// package.json — HTTPS tarball avoids git/SSH so CI and fresh clones install
// without credentials (npm canonicalizes `github:` shorthand to git+ssh).
"dependencies": {
  "@apiweave/proto": "https://github.com/Kaysharp42/apiweave-proto/archive/refs/tags/v0.2.0.tar.gz",
  "@bufbuild/protobuf": "^2.12.1"   // peer dep
}
```

## Use

```ts
import { ChangeOp, RecordKind } from "@apiweave/proto/apiweave/v1/sync_service_pb"
import { UlidSchema } from "@apiweave/proto/apiweave/v1/common_pb"
```

Stubs are shipped as `.ts` under `src/` — bundle/transpile with your own
toolchain (esbuild, tsc, Vite…). Only `@bufbuild/protobuf` is required at runtime.

## Source of truth

The `.proto` definitions live in the private `apiweave-cloud` repo
(`proto/apiweave/v1/*.proto`, buf source of truth). This repo holds only the
**generated** output. Do not edit `src/` by hand.

### Publishing an update

From an `apiweave-cloud` checkout, after `make proto/gen`:

```bash
# copy freshly generated stubs into a checkout of this repo, then:
cd apiweave-proto
git add src && git commit -m "regen: <what changed>"
npm version patch          # or minor/major
git push --follow-tags
```

Consumers bump the `vX.Y.Z` in their tarball URL to pick it up.
