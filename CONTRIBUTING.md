# Contributing

Use pnpm 9.15.4 with Node.js 20 or newer. Install dependencies with:

```bash
pnpm install --frozen-lockfile
```

Before opening a pull request, run the full gate:

```bash
pnpm typecheck && pnpm test && pnpm lint && pnpm build
```

Then run the protocol conformance suite against the built host. The runner is published from the hub and pinned to the protocol version:

```bash
npx -y @tesseron/conformance@1.2.2 --host "node conformance-host/dist/bin.js"
```

On Windows, prefix that with `TESSERON_CONFORMANCE_UNSUPPORTED=uds`: Unix domain sockets have no Windows implementation, and the six UDS fixtures are skipped instead of failed. CI runs them on Linux.

Biome owns formatting and linting. Run `pnpm format` to format changed files, then `pnpm lint` to check them.

Add a changeset for every user-visible package change:

```bash
pnpm changeset
```

The seven published packages release together as one fixed group. An SDK release PR is complete only after its required hub docs PR has merged.

Sign off every commit for DCO compliance:

```bash
git commit -s
```
