---
name: typescript
description: TypeScript in Node.js
metadata:
  tags: typescript,extensions,import,namespaces
---

# TypeScript in Node.js

## File Extensions

Use `.js` extensions in imports.

```typescript
// GOOD - .js extension
import { helper } from './helper.js';
import type { Config } from './types.js';

// JSON imports
import config from './config.json' with { type: 'json' };
```

Don't use extensions when importing from subpath imports defined in `package.json`.

```json
{
  "imports": {
    "#services": "./services/src/index.js",
    "#types": "./types/index.js"
  }
}
```

```typescript
// GOOD - no extension
import { service } from '#services';
import type { Config } from '#types';
```

## Use Type-Only Imports

Always use `type` keyword for type imports:

```typescript
// GOOD - type-only import
import type { User, Config } from './types.js';
import { createUser } from './user.js';

// GOOD - inline type imports
import { createUser, type User } from './user.js';

// BAD - may fail with type stripping
import { User, createUser } from './user.js';
```

## No Namespaces

Do not use namespaces.

```typescript
// BAD - namespaces don't work
namespace Utils {
  export function format(s: string): string {
    return s.trim();
  }
}

// GOOD - use modules
export function format(s: string): string {
  return s.trim();
}
```

## No Constructor Parameter Properties

Do not use parameter properties.

```typescript
// BAD - parameter properties don't work
class User {
  constructor(
    public name: string,
    private age: number,
  ) {}
}

// GOOD - explicit property declaration
class User {
  name: string;
  private age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}
```

## Workflow

1. Run type checking to validate types:

```bash
# Check types without emitting
tsc --noEmit
```
