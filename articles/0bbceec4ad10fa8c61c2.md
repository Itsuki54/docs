---
id: 0bbceec4ad10fa8c61c2
title: const prisma = new PrismaClient()を多用してはいけない　lib/prismaを作ろう
created_at: 2024-06-11T14:02:16+09:00
updated_at: 2024-06-11T14:10:45+09:00
tags: [{"name":"TypeScript","versions":[]},{"name":"Next.js","versions":[]},{"name":"prisma","versions":[]}]
private: false
url: https://qiita.com/Itsuki54/items/0bbceec4ad10fa8c61c2
likes_count: 1
type: "tech"
published: true
---

### lib/prismaに以下を追加するだけです

```ts
import { PrismaClient } from '@prisma/client';

declare global {
  var prisma: PrismaClient | undefined;
}

const prisma = global.prisma || new PrismaClient();

if (process.env.NODE_ENV === 'development') global.prisma = prisma;

export const db = prisma;
```

使用する際は
```tsx
import {db} from "lib/prisma";

db.user.create({
...
})
```
などのように使います
