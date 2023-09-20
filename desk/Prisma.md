![workflow](https://www.prisma.io/docs/static/153657b52bde1b006c94234b5753d495/42cbc/prisma-migrate-development-workflow.png)

### The Prisma data models 
Manually adjust your [Prisma data model](https://www.prisma.io/docs/concepts/components/prisma-schema/data-model)
Prisma schema file is in `prisma/schema.prisma`
```javascript
// learn more about it in the docs: https://pris.ly/d/prisma-schema
generator client {
	provider = "prisma-client-js"
}
datasource db {
	provider = "mysql"
	url = env("DATABASE_URL")
}
model User {
	id Int @id @default(autoincrement())
	email String @unique
	password String
}
```

### Prisma Migrate 
Migrate your development database using the `npx prisma migrate dev` CLI command

### Prisma Client
Use Prisma Client in your application code to access your database