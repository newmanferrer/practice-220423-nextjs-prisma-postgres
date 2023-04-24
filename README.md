# PRACTICE PRISMA ORM WITH POSTGRESQL

## Project Description

A very simple practice as a start to the implementation of prisma orm using postgres databases.

## Used technology

- Html 5
- CSS Module
- SASS (SCSS) version 1.62.0
- JavaScript
- TypeScript version 5.0.4
- React version 18.2.0
- React Dom version 18.2.0
- Nextjs version 13.2.4
- Prisma version 4.13.0
- PNPM version 8.3.1
- PostgreSQL version 15

## Resources and documentation used

- Nextjs V13: https://beta.nextjs.org/docs
- Nextjs V13.2: https://nextjs.org/blog
- Prisma ORM: https://www.prisma.io/
- PostgreSQL: https://www.postgresql.org/
- Sass: https://sass-lang.com/

## Developers: Requirements

- Web Browser
- Code editor
- Nodejs: https://nodejs.org/en/
- PostgreSQL

## Developers: Installation

1. Clone the repository: https://github.com/newmanferrer/project-220423-nextjs-prisma-postgres.git
2. Another option is to download the repository using ZIP format.
3. Install the dependencies using the command "pnpm install", from the terminal console.
4. From the terminal console, execute the “pnpm dev” command, to run the development server.

---

## APP IMAGES

### Home Page: app\page.tsx (Server Component)

![Home Page Image 1] (public/images/readme/app-image-01.webp)

### Example Page: pages\example.tsx (Client Component)

![Example Page Image 2] (public/images/readme/app-image-02.webp)

---

## Best practice for instantiating PrismaClient with Next.js

### in the root of the project path: lib\prisma\db\client.ts

```js
// PrismaClient is attached to the `global` object in development to prevent
// exhausting your database connection limit.
//
// Learn more:
// https://pris.ly/d/help/next-js-best-practices

import { PrismaClient } from '@prisma/client'

const globalForPrisma = global as unknown as {
  prisma: PrismaClient | undefined
}

export const prisma =
  globalForPrisma.prisma ??
  new PrismaClient({
    log: ['query'],
  })

if (process.env.NODE_ENV !== 'production') globalForPrisma.prisma = prisma
```

### In path: app\page.tsx

```js
import { prisma } from '@/lib/prisma/db/client'

export default async function HomePage() {
  const user = await prisma.user.findUnique({
    where: {
      email: 'newmanferrer@test.com'
    }
  })

  return (
    <main>
      <h2>Hello, {user ? user.first_name : 'user'}</h2>
    </main>
  )
}
```

---

This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `app/page.tsx`. The page auto-updates as you edit the file.

[http://localhost:3000/api/hello](http://localhost:3000/api/hello) is an endpoint that uses [Route Handlers](https://beta.nextjs.org/docs/routing/route-handlers). This endpoint can be edited in `app/api/hello/route.ts`.

This project uses [`next/font`](https://nextjs.org/docs/basic-features/font-optimization) to automatically optimize and load Inter, a custom Google Font.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.

---

## Author: Newman Ferrer

newmanferrer@gmail.com

🌞 Maracaibo - Venezuela 🌞

Practice date: 22/04/2023

Application review date: 24/04/2023
