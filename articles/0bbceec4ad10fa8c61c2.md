---
title: const prisma = new PrismaClient()を多用してはいけない　lib/prismaを作ろう
topics: [{"name":"TypeScript","versions":[]},{"name":"Next.js","versions":[]},{"name":"prisma","versions":[]}]
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
