---
id: d4f1be24ffc3a93af83b
title: mjsとcjsの違いって何？　普通のjsとどう違うの？　ChatGPTに聞いてみた
created_at: 2024-07-10T13:49:48+09:00
updated_at: 2024-07-10T13:49:48+09:00
tags: [{"name":"JavaScript","versions":[]},{"name":"Web","versions":[]},{"name":"ChatGPT","versions":[]}]
private: false
url: https://qiita.com/Itsuki54/items/d4f1be24ffc3a93af83b
likes_count: 3
type: "tech"
published: true
---

## `mjs` と `cjs` の違い

JavaScriptのモジュールシステムには、主に`mjs`（ECMAScript Modules）と`cjs`（CommonJS）の2種類があります。この記事では、これらの違いについて詳しく説明します。

### 背景

JavaScriptはもともとブラウザ上で動作するスクリプト言語として開発されました。初期の頃は、モジュールという概念が存在せず、全てのコードはグローバルスコープで実行されていました。しかし、プロジェクトが大規模化するにつれて、コードの再利用や分割が求められるようになり、モジュールシステムが導入されました。

#### CommonJS (cjs)
CommonJSは、サーバーサイドJavaScript（特にNode.js）でのモジュール管理のために開発された標準です。Node.jsは2009年に登場し、そのモジュールシステムとしてCommonJSを採用しました。CommonJSはシンプルで直感的な設計が特徴です。

#### ECMAScript Modules (mjs)
ECMAScript Modulesは、JavaScriptの公式標準であるECMAScriptによって定義されたモジュールシステムです。ES6（ES2015）で正式に導入され、ブラウザ環境とサーバー環境の両方で動作することを目指しています。

### 1. モジュールのインポートとエクスポート

**CommonJS (cjs)**
```javascript
// インポート
const module = require('module-name');

// エクスポート
module.exports = {
  functionName,
  variableName,
};
```

**ECMAScript Modules (mjs)**
```javascript
// インポート
import { functionName, variableName } from 'module-name';

// エクスポート
export const functionName = () => { ... };
export const variableName = 'value';
```

**違い:**
- `cjs`では`require`と`module.exports`を使用します。
- `mjs`では`import`と`export`を使用します。

### 2. 実行環境

- **CommonJS (cjs):** Node.js環境で主に使用されます。Node.jsのデフォルトモジュールシステムです。
- **ECMAScript Modules (mjs):** ブラウザ環境とNode.jsの両方で使用可能です。特にES6以降の標準です。

**違い:**
- `cjs`は主にサーバーサイド（Node.js）で使用されます。
- `mjs`はクライアントサイド（ブラウザ）とサーバーサイドの両方で使用されます。

### 3. 非同期処理

- **CommonJS (cjs):** モジュールの読み込みは同期的に行われます。つまり、モジュールの読み込みが完了するまで他の処理はブロックされます。
- **ECMAScript Modules (mjs):** モジュールの読み込みは非同期的に行われます。これにより、パフォーマンスが向上します。

**違い:**
- `cjs`は同期的な読み込みを行います。
- `mjs`は非同期的な読み込みを行い、パフォーマンス向上に寄与します。

### 4. 拡張子

- **CommonJS (cjs):** `.js` 拡張子を使用します。
- **ECMAScript Modules (mjs):** `.mjs` 拡張子を使用します。また、`package.json` で `"type": "module"` を設定することで `.js` 拡張子も使用可能です。

**違い:**
- `cjs`は`.js`拡張子を使用します。
- `mjs`は`.mjs`拡張子を使用し、設定によって`.js`もサポートします。

### 5. 名前空間

- **CommonJS (cjs):** モジュール全体が1つのオブジェクトとしてエクスポートされます。
- **ECMAScript Modules (mjs):** 各エクスポートが独自の名前空間を持ちます。

**違い:**
- `cjs`はモジュール全体が1つのオブジェクト。
- `mjs`は各エクスポートが独自の名前空間。

### 6. デフォルトエクスポート

**CommonJS (cjs)**
```javascript
module.exports = functionName;
```

**ECMAScript Modules (mjs)**
```javascript
export default functionName;
```

**違い:**
- `cjs`はデフォルトエクスポートが標準。
- `mjs`は`export default`を使用。

### まとめ

- **CommonJS (cjs):** Node.jsで広く使用されている伝統的なモジュールシステム。同期的なモジュール読み込み、`.js`拡張子。
- **ECMAScript Modules (mjs):** 新しい標準。ブラウザとNode.jsの両方で使用可能。非同期的なモジュール読み込み、`.mjs`拡張子。

プロジェクトのニーズに応じて使い分けることが重要です。既存のNode.jsプロジェクトでは`cjs`、新しいプロジェクトやブラウザでも動作させたい場合は`mjs`を選ぶと良いでしょう。

