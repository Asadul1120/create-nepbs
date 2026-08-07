# NEPBS

> **Node Express Prisma Backend Server**

[![npm version](https://img.shields.io/npm/v/create-nepbs.svg)](https://www.npmjs.com/package/create-nepbs)
[![npm downloads](https://img.shields.io/npm/dm/create-nepbs.svg)](https://www.npmjs.com/package/create-nepbs)
[![license](https://img.shields.io/npm/l/create-nepbs.svg)](LICENSE)

📦 **NPM Package:** [https://www.npmjs.com/package/create-nepbs](https://www.npmjs.com/package/create-nepbs)

**NEPBS** is a simple CLI for creating a ready-to-use **Node.js + Express + Prisma** backend project in seconds.

It supports **TypeScript** and **JavaScript**, multiple database options, automatic dependency installation, Prisma configuration, common backend utilities, and a clean starter structure.

## Quick Start

Create a new backend project:

```bash
npx create-nepbs my-app
```

Then follow the interactive setup.

```text
Choose your language:

1. TypeScript
2. JavaScript

Enter your choice [1]:
```

TypeScript is selected by default.

Next, choose a database:

```text
Choose your database:

1. PostgreSQL
2. MySQL
3. MariaDB
4. SQLite
5. SQL Server
6. CockroachDB
7. MongoDB

Enter your choice [1]:
```

PostgreSQL is selected by default.

After the project is generated:

```bash
cd my-app
```

Update your database connection in `.env`, then run:

```bash
npm run prisma:migrate -- --name init
npm run dev
```

For MongoDB, use:

```bash
npm run prisma:push
npm run dev
```

Your API will be available at:

```text
http://localhost:5000/api/v1
```

Expected response:

```json
{
  "success": true,
  "message": "API is running"
}
```

---

## Why NEPBS?

Starting a new backend project usually requires repeating the same setup:

- Create the project structure
- Install Express
- Configure TypeScript or JavaScript
- Configure Prisma
- Configure a database
- Setup environment variables
- Setup CORS
- Setup cookies
- Setup JWT utilities
- Setup password hashing
- Setup error handling
- Create a basic API structure

NEPBS automates these repetitive steps so you can spend more time building your application.

---

## Features

- Node.js + Express backend
- Prisma ORM
- TypeScript and JavaScript support
- TypeScript by default
- ES Modules
- PostgreSQL by default
- Multiple database options
- Automatic dependency installation
- Automatic Prisma setup
- Prisma Client configuration
- Environment variable setup
- CORS configuration
- Cookie Parser
- JWT helper
- Password hashing with bcrypt
- Global error handler
- Async error wrapper
- Not-found middleware
- API response helper
- Starter `/api/v1` endpoint
- Node.js version detection
- Windows, macOS, and Linux friendly
- Beginner-friendly project structure

NEPBS intentionally keeps the generated project minimal. It does not generate unnecessary CRUD modules or authentication routes by default.

---

## Language Support

### TypeScript

TypeScript is the default option.

Generated TypeScript projects use:

- Strict TypeScript
- ES Modules
- NodeNext module resolution
- `tsx` for development
- `tsc` for production builds
- `.js` extensions in relative TypeScript imports where required by Node ESM

Example:

```ts
import app from "./app.js";
```

### JavaScript

JavaScript mode generates plain `.js` application source files using ES Modules.

Example:

```js
import express from "express";
```

---

## Database Support

NEPBS provides the following database choices:

| Database | Prisma Provider | Default |
|---|---|---:|
| PostgreSQL | `postgresql` | ✅ |
| MySQL | `mysql` | |
| MariaDB | `mysql` | |
| SQLite | `sqlite` | |
| SQL Server | `sqlserver` | |
| CockroachDB | `cockroachdb` | |
| MongoDB | `mongodb` | |

Managed database services can also be used through the appropriate database option and connection URL.

Examples:

- Neon → PostgreSQL
- Supabase → PostgreSQL
- Railway PostgreSQL → PostgreSQL
- PlanetScale → MySQL

---

## Node.js Compatibility

NEPBS detects the installed Node.js version before creating a project.

It is designed to work with Node.js major versions:

```text
19
20
21
22
23
24
```

When the latest Prisma release does not support the installed Node.js version or selected database, NEPBS uses a compatible Prisma setup instead of blindly installing an incompatible configuration.

For production projects, using a currently supported Node.js LTS release is recommended.

Check your Node.js version:

```bash
node --version
```

Check npm:

```bash
npm --version
```

---

## Generated Dependencies

A generated project includes common backend packages such as:

```text
express
prisma
@prisma/client
dotenv
cors
cookie-parser
jsonwebtoken
bcryptjs
http-status-codes
```

TypeScript projects additionally include development/type packages such as:

```text
typescript
tsx
@types/node
@types/express
@types/cookie-parser
@types/jsonwebtoken
@types/cors
@types/bcryptjs
```

Database-specific Prisma adapters and drivers are installed when required by the selected Prisma setup.

NEPBS installs current compatible package versions during project generation.

---

## Packages Not Added by Default

To keep generated projects minimal, NEPBS does not install these packages automatically:

```text
zod
helmet
morgan
eslint
prettier
husky
swagger
nodemon
```

You can install them manually when your project needs them.

---

## Generated Project Structure

### TypeScript

```text
my-app/
├── src/
│   ├── modules/
│   ├── middleware/
│   ├── utils/
│   ├── config/
│   ├── app.ts
│   ├── server.ts
│   └── index.ts
│
├── prisma/
│   └── schema.prisma
│
├── .env
├── .env.example
├── .gitignore
├── package.json
├── tsconfig.json
└── README.md
```

Depending on the Prisma version/profile selected by NEPBS, a `prisma.config.ts` file and generated Prisma Client directory may also be created.

### JavaScript

JavaScript projects use the same simple structure with `.js` application files where appropriate.

---

## Included Backend Utilities

### Prisma Client

NEPBS creates a reusable Prisma Client configuration for the selected database and Prisma profile.

### Environment Configuration

Common variables are prepared for you:

```env
NODE_ENV=development
PORT=5000
DATABASE_URL=
JWT_SECRET=
JWT_EXPIRES_IN=7d
CORS_ORIGIN=http://localhost:3000
```

### JWT Helper

Functions for:

- Creating JWT tokens
- Verifying JWT tokens

### Password Helper

Functions for:

- Hashing passwords
- Comparing plain and hashed passwords

### Error Handling

The generated project includes:

- Global error handler
- Not-found middleware
- Async error wrapper

### API Response Helper

A simple reusable response structure is included for consistent API responses.

---

## Available Scripts

### Development

```bash
npm run dev
```

### Generate Prisma Client

```bash
npm run prisma:generate
```

### Create a Migration

```bash
npm run prisma:migrate -- --name init
```

### Push Prisma Schema

Useful for MongoDB and development workflows:

```bash
npm run prisma:push
```

### Prisma Studio

```bash
npm run prisma:studio
```

### Build

For TypeScript projects:

```bash
npm run build
```

### Production

```bash
npm run start
```

---

## Example Workflow

Create a project:

```bash
npx create-nepbs blog-api
```

Choose:

```text
Language: TypeScript
Database: PostgreSQL
```

Enter the project:

```bash
cd blog-api
```

Configure `.env`:

```env
DATABASE_URL="postgresql://username:password@localhost:5432/blog_api"
JWT_SECRET="change-this-secret"
```

Create the initial migration:

```bash
npm run prisma:migrate -- --name init
```

Start development:

```bash
npm run dev
```

Test:

```text
GET http://localhost:5000/api/v1
```

Response:

```json
{
  "success": true,
  "message": "API is running"
}
```

---

## Project Name Safety

NEPBS validates the project name before creating files.

It rejects:

- Empty project names
- Names containing spaces
- Unsafe characters
- Unsafe command input
- Existing non-empty target directories

NEPBS will not delete or overwrite an existing non-empty project folder.

---

## Using NEPBS Globally

Using `npx` is recommended:

```bash
npx create-nepbs my-app
```

You can also install it globally:

```bash
npm install -g create-nepbs
```

Then run:

```bash
create-nepbs my-app
```

---

## Who Is NEPBS For?

NEPBS can be useful for:

- Beginner backend developers
- Node.js developers
- Express developers
- Prisma users
- Students learning backend development
- Developers building REST APIs
- Developers who frequently start new backend projects

---

## Philosophy

NEPBS follows a few simple principles:

- Keep generated code readable
- Avoid unnecessary abstraction
- Prefer beginner-friendly structure
- Use modern ES Modules
- Keep configuration understandable
- Automate repetitive setup
- Let developers extend the project as needed

---

## Roadmap

Possible future additions:

- Authentication module
- Zod validation
- Helmet
- Morgan/logger support
- Swagger/OpenAPI
- Docker support
- Testing setup
- Additional project templates
- Optional CRUD generation
- Additional CLI commands

These features are not installed by default.

---

## Contributing

Contributions are welcome.

If you find a bug or have an idea:

1. Fork the repository
2. Create a branch
3. Make your changes
4. Commit your changes
5. Push your branch
6. Open a Pull Request

For bugs and feature requests, please open a GitHub Issue.

---

## Local Development

Clone the repository and install dependencies:

```bash
npm install
```

Build the CLI:

```bash
npm run build
```

Link it locally:

```bash
npm link
```

Test it from another directory:

```bash
create-nepbs my-app
```

Before publishing:

```bash
npm run check
npm run build
npm pack --dry-run
npm publish --dry-run
```

---

## Support

If NEPBS saves you setup time, consider giving the GitHub repository a ⭐.

Feedback, bug reports, feature requests, and contributions are welcome.

---

## License

MIT

---

<p align="center">
  <strong>NEPBS — Node Express Prisma Backend Server</strong>
</p>

<p align="center">
  Create a Node.js + Express + Prisma backend in seconds.
</p>

```bash
npx create-nepbs my-app
```
