---
name: configuration
description: Configuring new or existing project
metadata:
  tags: configuration
---

# Vitest Configuration

## Common Options

```ts
// vitest.config.ts
const timeout = process.env.VITEST_VSCODE ? 600_000 : 5000; // Are we debugging?

export default defineConfig({
  test: {
    globals: true,
    root: './',
    sequence: {
      hooks: 'stack',
    },
    reporters: [['default', { summary: false }]],
    include: ['**/*.{spec,e2e-spec}.ts'],
    isolate: false,
    pool: 'forks',
    testTimeout: timeout,
    hookTimeout: timeout,
    coverage: {
      provider: 'v8',
      reporter: ['text', 'json', 'html'],
      include: ['src/**/*.ts'],
      exclude: ['index.ts'],
    },
    env: {
      TZ: 'UTC',
    },
  },
});
```

## Projects (Monorepos)

```ts
defineConfig({
  test: {
    projects: ['packages/*'],
  },
});
```

## CLI Commands

```bash
vitest                             # Watch mode in dev, run mode in CI
vitest run                         # Single run without watch
vitest run --coverage              # With coverage
vitest run src/test.spec.ts --run  # Tests specific files
vitest list --json                 # List tests without running
```
