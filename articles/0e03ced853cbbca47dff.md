---
id: 0e03ced853cbbca47dff
title: バックエンドって何してるの？関数と何が違うのか
created_at: 2024-07-10T14:02:45+09:00
updated_at: 2024-07-10T14:02:45+09:00
tags: [{"name":"JavaScript","versions":[]},{"name":"Web","versions":[]},{"name":"バックエンド","versions":[]}]
private: false
url: https://qiita.com/Itsuki54/items/0e03ced853cbbca47dff
likes_count: 0
type: "tech"
published: true
---

### バックエンドの仕組みとは？

バックエンドは、ウェブアプリケーションの裏側で動作し、ユーザーインターフェースとデータベース間の通信や処理を担当する部分です。ここでは、JavaScriptを使ってバックエンドの基本的な仕組みについて解説します。

#### 1. 関数呼び出しとバックエンドの問い合わせの違い

- **関数呼び出し**:
  ```javascript
  function calculateSum(a, b) {
      return a + b;
  }

  // 関数の呼び出し
  let result = calculateSum(3, 5);
  console.log(result); // 出力: 8
  ```
  上記の例では、`calculateSum` 関数が定義され、引数 `3` と `5` を渡して呼び出されています。

- **バックエンドの問い合わせ**:
  ```javascript
  // クライアントからのリクエストを模した例
  fetch('/api/data')
      .then(response => response.json())
      .then(data => console.log(data))
      .catch(error => console.error('エラー:', error));
  ```
  上記の例では、クライアントが `/api/data` エンドポイントにリクエストを送信しています。サーバーはこのリクエストを受け取り、データを処理してクライアントに返します。

#### 2. バックエンドの処理の流れ

- **リクエストの受け取りと処理**:
  ```javascript
  // Expressを使用したサーバーサイドの例
  const express = require('express');
  const app = express();

  // GETリクエストの処理
  app.get('/api/data', (req, res) => {
      // データベースからデータを取得する仮想的な処理
      let data = { id: 1, name: 'John Doe' };
      res.json(data); // データをJSON形式で返す
  });

  app.listen(3000, () => console.log('サーバーがポート3000で起動しました'));
  ```
  上記の例では、Expressフレームワークを使用して、`/api/data` へのGETリクエストを処理するサーバーが定義されています。リクエストを受け取ったら、サーバーはデータベースからデータを取得し、JSON形式でクライアントに返します。

#### 3. 非同期性とスケーラビリティの考慮

- **非同期処理の例**:
  ```javascript
  // ファイルの読み込みを非同期で行う例
  const fs = require('fs');

  fs.readFile('file.txt', 'utf8', (err, data) => {
      if (err) throw err;
      console.log(data);
  });
  ```
  上記の例では、ファイルシステム（Node.jsの場合）からファイルを非同期で読み込んでいます。このような非同期処理は、サーバーが多くのリクエストを同時に処理するために重要です。


---

### ユーザーが体験するバックエンドのフロー

ユーザーがウェブアプリケーションを利用する際に、バックエンドがどのように機能しているか、具体的なフローを説明します。

#### 1. ユーザーが操作を行う

ユーザーはフロントエンドのインターフェースを通じて、アプリケーション内で特定の操作（例: データの検索、更新、新規作成など）を行います。

#### 2. フロントエンドからバックエンドへのリクエスト

ユーザーの操作に応じて、フロントエンドはバックエンドのAPIエンドポイントに対してリクエストを送信します。例えば、新しいユーザー登録を行う場合は、以下のようなリクエストが発生します。

```javascript
fetch('/api/users', {
    method: 'POST',
    headers: {
        'Content-Type': 'application/json'
    },
    body: JSON.stringify({
        username: 'john_doe',
        email: 'john@example.com',
        password: 'password123'
    })
})
.then(response => response.json())
.then(data => console.log('新しいユーザーが作成されました:', data))
.catch(error => console.error('エラー:', error));
```

#### 3. バックエンドでの処理

バックエンドは受け取ったリクエストに基づき、次のような処理を行います。

- **データの検証と処理**: 受け取ったデータのバリデーションや必要なビジネスロジックの適用を行います。
- **データベースの操作**: ユーザー情報のデータベースへの書き込みなど、データの永続化を行います。
- **外部サービスの呼び出し**: 必要に応じて外部サービスとの連携を行い、さらなる処理を行います。

#### 4. レスポンスの受け取りと表示

バックエンドが処理を完了すると、フロントエンドはレスポンスを受け取り、ユーザーに適切なフィードバックを表示します。例えば、新規ユーザー登録の場合は、成功したメッセージやエラーメッセージを表示します。

```javascript
{
    "id": 123,
    "username": "john_doe",
    "email": "john@example.com"
}
```

#### 5. ユーザーのフィードバックと次の操作

ユーザーはフィードバックを元に、次の操作を決定します。成功した場合は、新規作成されたデータを確認したり、その情報を利用して他の操作を続けたりします。

### まとめ

このようにして、ユーザーがアプリケーションを使用する際のバックエンドのフローを理解することで、システムの動作をより具体的にイメージすることができます。バックエンドはユーザーが直接触れることはありませんが、その裏で重要な役割を果たしていることを理解することが重要です。

---
