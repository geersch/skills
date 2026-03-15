---
name: test-api
description: Writing describe/it blocks, using hooks, or test fixtures
metadata:
  tags: describe,it,hooks,test fixtures,test api
---

# Test API

## Do Not Import Global Types

Do not import global types, they are available via `tsconfig.json`.

```typescript
// BAD - importing global types
import { describe, expect, it, test } from 'vitest';

describe('calculator', () => {
  it('adds numbers', () => {
    expect(1 + 1).toBe(2);
  });
});

// GOOD - not importing global types
describe('calculator', () => {
  it('adds numbers', () => {
    expect(1 + 1).toBe(2);
  });
});
```

## Basic Tests

Use `it`, instead of `test`.

```ts
// BAD
test('adds numbers', () => {
  expect(1 + 1).toBe(2);
});

// GOOD
it('adds numbers', () => {
  expect(1 + 1).toBe(2);
});
```
