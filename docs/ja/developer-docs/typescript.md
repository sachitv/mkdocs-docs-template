# TypeScript クイックスタート

最小の TypeScript セットアップと簡単な例を紹介します。

## セットアップ

```bash
# プロジェクト初期化
npm init -y

# TypeScript と ts-node を導入（TS を直接実行）
npm i -D typescript ts-node @types/node

# tsconfig.json を作成
npx tsc --init --rootDir src --outDir dist --esModuleInterop --resolveJsonModule --strict
```

プロジェクト構成:

```text
.
├── package.json
├── tsconfig.json
└── src/
    └── index.ts
```

## サンプルコード

`src/index.ts` を作成:

```ts
// 基本型
type ID = string;

// インターフェース
interface User {
  id: ID;
  name: string;
  email?: string; // 任意
}

// 型付き関数（引数/戻り値）
function greet(user: User): string {
  return `Hello, ${user.name}!`;
}

// 絞り込み（type guard）の例
function isEmailSet(u: User): u is User & { email: string } {
  return typeof u.email === 'string' && u.email.length > 0;
}

const me: User = { id: 'u_123', name: 'Ada', email: 'ada@example.com' };
console.log(greet(me));
if (isEmailSet(me)) {
  console.log('Email:', me.email.toLowerCase());
}
```

実行:

```bash
npx ts-node src/index.ts
```

JavaScript をビルド:

```bash
npx tsc
node dist/index.js
```

