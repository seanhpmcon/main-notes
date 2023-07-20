### Installation
`npm install prisma @prisma/client dotenv`

### Configure .env file
`DATABASE_URL=postgresql://username:password@localhost:5432/database_name`

### Create Prisma Models
Create a file called `prisma/schema.prisma`
```js
datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

generator client {
  provider = "prisma-client-js"
}

model User {
  id    Int    @id @default(autoincrement())
  email String @unique
  name  String?
}
```

### Create a Prisma Client file 
Create the file in the root directory `lib/prisma.js`
```js
import { PrismaClient } from "@prisma/client";

let prisma;
if (typeof window === "undefined") {
    if (process.env.NODE_ENV === "production") {
        prisma = new PrismaClient();
    } else {
        if (!global.prisma) {
            global.prisma = new PrismaClient();
        }
        prisma = global.prisma;
    }
}

export default prisma;
```

### Import the Prisma client and make requests
Use the follow import `import prisma from "@/lib/prisma";`
Example database query functions:
```js
export default async function getUsers(page) {
    const allUsers = await prisma.User.findMany({
      skip: (page*10),
      take: 10,
    })
  return allUsers;
}

export async function getProducts(page) {
  const products = await prisma.Product.findMany({
    skip: (page*10),
    take: 10,
  })
return products;
}

export async function getSearchResults(searchvar) {
  const products = await prisma.Product.findMany({
    where: {
      name: {
        contains: searchvar,
      },
    },
    take: 10,
  })

return products;
}
```

### Generate the Prisma Client
Use the command `npm prisma generate` to generate the prisma client

### Issues with Database table names
Use `@@map(name: "actor")` to map the correct name of the table in the database