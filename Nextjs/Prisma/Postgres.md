### Raw Prisma Queries
1. When using raw queries, columns with type tsvector throws an error. One solution is to explicitly convert the column to a string.