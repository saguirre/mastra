---
'@mastra/deployer': patch
---

Fixed TypeScript path alias resolution in transpiled workspace packages.

When using `transpilePackages` in a monorepo, path aliases defined in workspace package `tsconfig.json` files (e.g., `~/*` → `./src/*`) were not being resolved during bundling. This caused build failures when workspace packages used their own tsconfig path mappings.

The fix ensures the tsconfig-paths plugin converts relative importer paths to absolute paths before resolving aliases, and moves the plugin earlier in the build pipeline for proper resolution order.
