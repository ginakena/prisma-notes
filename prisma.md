# Getting Started With Prisma

Prisma is a next-generation ORM for Node.js and TypeScript that provides a type-safe and intuitive way to interact with databases.
** It consists of the following parts:

* Prisma Client: Auto-generated and type-safe query builder for Node.js & TypeScript

* Prisma Migrate: Migration system

* Prisma Studio: GUI to view and edit data in your database.

## Steps to use Prisma
### 1. Installation
Install Prisma as a dev dependency by running the following command: `npm install prisma --save-dev` or `npm install prisma -D` 


### 2. Set Up
Set Up prisma project by creating a schema file. This file will define the structure of your database. You can do this by running the following command:<br> `npx prisma init`. <br>
If you are using another database other than postgresql then run the command<br> `npx prisma init --datasource-provider DATABASE`<br> whereby you replace the DATABASE with the database you are using.<br> 
The above command will then create an .env file that comes with a default database connection string. You can then edit this file to change the database connection string to your own database connection string, that is<br> `DATABASE_URL="postgresql://johndoe:randompassword@localhost:5432/mydb?schema=public` <br>
can be changed to<br> `DATABASE_URL="postgresql://postgres:1234@localhost:5432/Users`

### 3. Create your model(s).
Prisma models define the structure of your database tables using the model keyword.<br>
Each model maps to a table in your database.<br>

#### Key concepts of Prisma Models. 
 * Data Models: Define the tables and their columns (fields) in your database.

* Field Types: Specify the data types for each field (e.g., String, Int, Boolean).

* Relations: Describe how models relate to each other using relation fields.

* Attributes: Add additional metadata to fields and models using attributes like @id, @default, @relation.

##### Field Attributes
Attributes modify how fields behave.

* @id: Marks the field as the primary key.

* @default(value): Sets a default value for the field.

    Can use autoincrement(), uuid(), now(), etc.

* @unique: Ensures field values are unique.

* @updatedAt: Auto-updates with current timestamp on update.

* @relation: Sets up relations between models (e.g., foreign keys).

* @map("db_field_name"): Maps field to a custom database column name.
* @@id: it is a model attribute, and it defines a composite primary key using multiple fields eg @@id([field1, field2])

* @@unique: it is a model attribute, and it ensures a unique constraint on a combination of multiple fields. eg @@unique([username, emailAddress])

* @@map: it is a model attribute, and it maps the model to a table with a different name in the database.


Here is an example of a simple model:
```model User {
  id    Int    @id @default(autoincrement())
  name  String
  email String @unique
}
```
This model defines a table named User with three columns : id, name, email.<br>

### 4. Migrations
Migrations are used to modify your database schema. They are a way to track changes to your database schema over time. 
Track your database changes by running the following command<br> `npx prisma migrate dev --name init`
This will create a new migration and apply it to your database.
View your database in UI by running <br> `npx prisma studio`

### 5. Prisma Client.
The Prisma Client is an auto-generated and type-safe database client that you use to interact with your database in a Node.js or TypeScript application. It’s generated based on the models you define in your Prisma schema (schema.prisma) and provides a simple, intuitive, and type-safe API for CRUD operations, filtering, pagination, and more.

 




  





