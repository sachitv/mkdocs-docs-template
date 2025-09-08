# TypeScript Quickstart

This page shows a minimal TypeScript setup and a small example.

## Setup

```bash
# Initialize a project
npm init -y

# Install TypeScript and ts-node for running TS directly
npm i -D typescript ts-node @types/node

# Create a tsconfig.json
npx tsc --init --rootDir src --outDir dist --esModuleInterop --resolveJsonModule --strict
```

Project layout:

```text
.
├── package.json
├── tsconfig.json
└── src/
    └── index.ts
```

## Example code

Create `src/index.ts`:

```ts
// Basic types
type ID = string;

// Interface
interface User {
  id: ID;
  name: string;
  email?: string; // optional
}

// Function with typed params + return
function greet(user: User): string {
  return `Hello, ${user.name}!`;
}

// Narrowing example
function isEmailSet(u: User): u is User & { email: string } {
  return typeof u.email === 'string' && u.email.length > 0;
}

const me: User = { id: 'u_123', name: 'Ada', email: 'ada@example.com' };
console.log(greet(me));
if (isEmailSet(me)) {
  console.log('Email:', me.email.toLowerCase());
}
```

Run it:

```bash
npx ts-node src/index.ts
```

Build JavaScript:

```bash
npx tsc
node dist/index.js
```

