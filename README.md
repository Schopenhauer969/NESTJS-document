# NestJS — Beginner to Advanced Guide

> A clean, practical, beginner-to-advanced NestJS learning guide with complete examples.
> **English + Khmer explanations 🇬🇧 🇰🇭**

---

## 📚 Table of Contents

* [1. What is NestJS?](#1-what-is-nestjs)
* [2. Prerequisites](#2-prerequisites)
* [3. Installation](#3-installation)
* [4. Create Your First Project](#4-create-your-first-project)
* [5. Project Structure](#5-project-structure)
* [6. Hello World](#6-hello-world)
* [7. Modules](#7-modules)
* [8. Controllers](#8-controllers)
* [9. Providers and Services](#9-providers-and-services)
* [10. Dependency Injection](#10-dependency-injection)
* [11. Route Parameters](#11-route-parameters)
* [12. Query Parameters](#12-query-parameters)
* [13. Request Body](#13-request-body)
* [14. DTOs](#14-dtos)
* [15. Validation](#15-validation)
* [16. Pipes](#16-pipes)
* [17. Exception Handling](#17-exception-handling)
* [18. Middleware](#18-middleware)
* [19. Guards](#19-guards)
* [20. Interceptors](#20-interceptors)
* [21. Custom Decorators](#21-custom-decorators)
* [22. Configuration and Environment Variables](#22-configuration-and-environment-variables)
* [23. CRUD API](#23-crud-api)
* [24. Database with TypeORM](#24-database-with-typeorm)
* [25. Database with Prisma](#25-database-with-prisma)
* [26. Authentication with JWT](#26-authentication-with-jwt)
* [27. Authorization and Roles](#27-authorization-and-roles)
* [28. Password Hashing](#28-password-hashing)
* [29. Swagger / OpenAPI](#29-swagger--openapi)
* [30. API Versioning](#30-api-versioning)
* [31. CORS](#31-cors)
* [32. Helmet](#32-helmet)
* [33. Rate Limiting](#33-rate-limiting)
* [34. File Upload](#34-file-upload)
* [35. Logging](#35-logging)
* [36. Testing](#36-testing)
* [37. E2E Testing](#37-e2e-testing)
* [38. Caching](#38-caching)
* [39. Events](#39-events)
* [40. Queues](#40-queues)
* [41. WebSockets](#41-websockets)
* [42. GraphQL](#42-graphql)
* [43. Microservices](#43-microservices)
* [44. Health Checks](#44-health-checks)
* [45. Graceful Shutdown](#45-graceful-shutdown)
* [46. Production Structure](#46-production-structure)
* [47. Clean Architecture](#47-clean-architecture)
* [48. Best Practices](#48-best-practices)
* [49. Common Mistakes](#49-common-mistakes)
* [50. Production Checklist](#50-production-checklist)

---

# 1. What is NestJS?

## English

**NestJS** is a Node.js framework for building scalable server-side applications.

It is built with TypeScript and provides an architecture based around:

* Modules
* Controllers
* Providers
* Dependency Injection
* Pipes
* Guards
* Interceptors
* Middleware
* Exception Filters
* Decorators

NestJS uses a modular architecture that helps applications remain maintainable as they grow.

## ខ្មែរ

**NestJS** គឺជា Framework សម្រាប់ Node.js ដែលប្រើសម្រាប់បង្កើត Backend និង API ដែលមានរចនាសម្ព័ន្ធច្បាស់លាស់ និងងាយស្រួលពង្រីក។

វាមានគោលគំនិតសំខាន់ៗដូចជា៖

* `Module`
* `Controller`
* `Service / Provider`
* Dependency Injection
* Pipe
* Guard
* Interceptor
* Middleware
* Exception Filter
* Decorator

### Basic architecture

```text
Client
   │
   ▼
Controller
   │
   ▼
Service
   │
   ▼
Repository / Database
```

---

# 2. Prerequisites

You should know:

* JavaScript
* TypeScript
* Node.js
* npm
* HTTP
* REST API
* JSON
* Basic SQL

Current NestJS documentation lists Node.js **20.19+** as a runtime requirement.

## Recommended

```text
Node.js 20+
TypeScript
npm
VS Code
Postman / Insomnia
Git
```

---

# 3. Installation

## Install Nest CLI

```bash
npm install -g @nestjs/cli
```

Or use the CLI without global installation:

```bash
npx @nestjs/cli@latest
```

Check:

```bash
nest --version
```

---

# 4. Create Your First Project

Create a project:

```bash
nest new nest-api
```

Enter the project:

```bash
cd nest-api
```

Start development server:

```bash
npm run start:dev
```

Open:

```text
http://localhost:3000
```

## English

`start:dev` watches your source files and reloads the application when files change.

## ខ្មែរ

`npm run start:dev` នឹងធ្វើឱ្យ Server ដំណើរការ និង Reload ដោយស្វ័យប្រវត្តិ នៅពេលយើងកែ Code។

---

# 5. Project Structure

A basic NestJS project looks like:

```text
nest-api/
├── src/
│   ├── app.controller.ts
│   ├── app.service.ts
│   ├── app.module.ts
│   └── main.ts
│
├── test/
├── package.json
├── tsconfig.json
└── nest-cli.json
```

A larger application can use:

```text
src/
├── main.ts
├── app.module.ts
│
├── common/
│   ├── decorators/
│   ├── filters/
│   ├── guards/
│   ├── interceptors/
│   ├── middleware/
│   └── pipes/
│
├── config/
│
├── auth/
│   ├── auth.controller.ts
│   ├── auth.service.ts
│   ├── auth.module.ts
│   ├── dto/
│   └── guards/
│
├── users/
│   ├── users.controller.ts
│   ├── users.service.ts
│   ├── users.module.ts
│   ├── dto/
│   └── entities/
│
└── products/
    ├── products.controller.ts
    ├── products.service.ts
    ├── products.module.ts
    ├── dto/
    └── entities/
```

---

# 6. Hello World

## `src/main.ts`

```ts
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);

  await app.listen(process.env.PORT ?? 3000);
}

bootstrap();
```

## `src/app.controller.ts`

```ts
import { Controller, Get } from '@nestjs/common';

@Controller()
export class AppController {
  @Get()
  getHello(): string {
    return 'Hello World!';
  }
}
```

## `src/app.module.ts`

```ts
import { Module } from '@nestjs/common';
import { AppController } from './app.controller';

@Module({
  controllers: [AppController],
})
export class AppModule {}
```

Run:

```bash
npm run start:dev
```

Request:

```http
GET http://localhost:3000/
```

Response:

```text
Hello World!
```

---

# 7. Modules

## English

A module organizes related functionality.

## ខ្មែរ

`Module` ប្រើសម្រាប់រៀបចំ Feature ដែលទាក់ទងគ្នា ឱ្យនៅជាក្រុម។

Create:

```bash
nest generate module users
```

Short version:

```bash
nest g module users
```

Example:

## `users/users.module.ts`

```ts
import { Module } from '@nestjs/common';

@Module({})
export class UsersModule {}
```

Import it into the application:

```ts
import { Module } from '@nestjs/common';
import { UsersModule } from './users/users.module';

@Module({
  imports: [UsersModule],
})
export class AppModule {}
```

---

# 8. Controllers

Controllers receive HTTP requests and return responses.

Create:

```bash
nest g controller users
```

Example:

## `users.controller.ts`

```ts
import {
  Controller,
  Get,
} from '@nestjs/common';

@Controller('users')
export class UsersController {
  @Get()
  findAll() {
    return [
      {
        id: 1,
        name: 'Dara',
      },
      {
        id: 2,
        name: 'Sokha',
      },
    ];
  }
}
```

Request:

```http
GET /users
```

Response:

```json
[
  {
    "id": 1,
    "name": "Dara"
  },
  {
    "id": 2,
    "name": "Sokha"
  }
]
```

## HTTP methods

```ts
@Get()
@Post()
@Put()
@Patch()
@Delete()
```

Example:

```ts
@Controller('users')
export class UsersController {
  @Get()
  findAll() {
    return [];
  }

  @Post()
  create() {
    return {
      message: 'User created',
    };
  }

  @Put(':id')
  update() {
    return {
      message: 'User updated',
    };
  }

  @Delete(':id')
  remove() {
    return {
      message: 'User deleted',
    };
  }
}
```

---

# 9. Providers and Services

A service contains business logic.

Create:

```bash
nest g service users
```

## `users.service.ts`

```ts
import { Injectable } from '@nestjs/common';

@Injectable()
export class UsersService {
  findAll() {
    return [
      {
        id: 1,
        name: 'Dara',
      },
      {
        id: 2,
        name: 'Sokha',
      },
    ];
  }

  findOne(id: number) {
    return {
      id,
      name: 'Dara',
    };
  }
}
```

Controller:

```ts
import {
  Controller,
  Get,
  Param,
} from '@nestjs/common';

import { UsersService } from './users.service';

@Controller('users')
export class UsersController {
  constructor(
    private readonly usersService: UsersService,
  ) {}

  @Get()
  findAll() {
    return this.usersService.findAll();
  }

  @Get(':id')
  findOne(@Param('id') id: string) {
    return this.usersService.findOne(Number(id));
  }
}
```

## Why use services?

Bad:

```ts
@Controller('users')
export class UsersController {
  @Get()
  findAll() {
    // Too much business logic here
  }
}
```

Better:

```text
Controller
   ↓
Service
   ↓
Repository
   ↓
Database
```

---

# 10. Dependency Injection

NestJS uses Dependency Injection.

Example:

```ts
@Injectable()
export class UsersService {
  findAll() {
    return [];
  }
}
```

Inject it:

```ts
@Controller('users')
export class UsersController {
  constructor(
    private readonly usersService: UsersService,
  ) {}
}
```

## ខ្មែរ

Dependency Injection មានន័យថា NestJS ជួយបង្កើត និងផ្គត់ផ្គង់ object ដែល Class មួយត្រូវការ។

យើងមិនចាំបាច់សរសេរ៖

```ts
const service = new UsersService();
```

ដោយខ្លួនឯងទេ។

NestJS នឹងគ្រប់គ្រងវា។

---

# 11. Route Parameters

Example:

```http
GET /users/10
```

Controller:

```ts
import {
  Controller,
  Get,
  Param,
} from '@nestjs/common';

@Controller('users')
export class UsersController {
  @Get(':id')
  findOne(@Param('id') id: string) {
    return {
      id: Number(id),
    };
  }
}
```

Request:

```http
GET /users/10
```

Response:

```json
{
  "id": 10
}
```

---

# 12. Query Parameters

Request:

```http
GET /users?page=1&limit=10
```

Code:

```ts
import {
  Controller,
  Get,
  Query,
} from '@nestjs/common';

@Controller('users')
export class UsersController {
  @Get()
  findAll(
    @Query('page') page: string,
    @Query('limit') limit: string,
  ) {
    return {
      page: Number(page),
      limit: Number(limit),
    };
  }
}
```

Response:

```json
{
  "page": 1,
  "limit": 10
}
```

---

# 13. Request Body

Install validation packages:

```bash
npm install class-validator class-transformer
```

Create DTO:

```ts
export class CreateUserDto {
  name: string;
  email: string;
}
```

Controller:

```ts
import {
  Body,
  Controller,
  Post,
} from '@nestjs/common';

@Controller('users')
export class UsersController {
  @Post()
  create(@Body() body: CreateUserDto) {
    return body;
  }
}
```

Request:

```http
POST /users
Content-Type: application/json
```

```json
{
  "name": "Dara",
  "email": "dara@example.com"
}
```

---

# 14. DTOs

DTO means:

> Data Transfer Object

Create:

```bash
mkdir -p src/users/dto
```

## `create-user.dto.ts`

```ts
export class CreateUserDto {
  name: string;
  email: string;
  age: number;
}
```

Use:

```ts
@Post()
create(@Body() dto: CreateUserDto) {
  return dto;
}
```

## Why DTO?

DTOs help define the shape of incoming data.

## ខ្មែរ

DTO គឺជា Class ដែលកំណត់ថា Request របស់ Client ត្រូវមាន Data បែបណា។

---

# 15. Validation

Use `class-validator`.

Install:

```bash
npm install class-validator class-transformer
```

DTO:

```ts
import {
  IsEmail,
  IsInt,
  IsNotEmpty,
  Min,
} from 'class-validator';

export class CreateUserDto {
  @IsNotEmpty()
  name: string;

  @IsEmail()
  email: string;

  @IsInt()
  @Min(18)
  age: number;
}
```

Enable global validation.

## `main.ts`

```ts
import { NestFactory } from '@nestjs/core';
import { ValidationPipe } from '@nestjs/common';

import { AppModule } from './app.module';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);

  app.useGlobalPipes(
    new ValidationPipe({
      whitelist: true,
      transform: true,
    }),
  );

  await app.listen(3000);
}

bootstrap();
```

Now invalid data:

```json
{
  "name": "",
  "email": "wrong-email",
  "age": 10
}
```

will be rejected.

### Important options

```ts
new ValidationPipe({
  whitelist: true,
  transform: true,
  forbidNonWhitelisted: true,
})
```

`whitelist: true`

Removes properties that are not decorated.

`transform: true`

Transforms request values into DTO types where supported.

`forbidNonWhitelisted: true`

Rejects unexpected properties instead of silently removing them.

---

# 16. Pipes

Pipes are commonly used for:

* Validation
* Transformation

Example:

```ts
import {
  Controller,
  Get,
  Param,
  ParseIntPipe,
} from '@nestjs/common';

@Controller('users')
export class UsersController {
  @Get(':id')
  findOne(
    @Param('id', ParseIntPipe) id: number,
  ) {
    return {
      id,
      type: typeof id,
    };
  }
}
```

Request:

```http
GET /users/10
```

`id` becomes:

```text
number
```

Invalid:

```http
GET /users/abc
```

returns a `400 Bad Request`.

---

# 17. Exception Handling

NestJS provides built-in HTTP exceptions.

Example:

```ts
import {
  Injectable,
  NotFoundException,
} from '@nestjs/common';

@Injectable()
export class UsersService {
  findOne(id: number) {
    const user = null;

    if (!user) {
      throw new NotFoundException(
        'User not found',
      );
    }

    return user;
  }
}
```

Common exceptions:

```ts
BadRequestException
UnauthorizedException
ForbiddenException
NotFoundException
ConflictException
InternalServerErrorException
```

Example:

```ts
throw new BadRequestException(
  'Invalid request',
);
```

---

# 18. Middleware

Middleware runs before a route handler.

Example:

```ts
import {
  Injectable,
  NestMiddleware,
} from '@nestjs/common';

import { Request, Response, NextFunction } from 'express';

@Injectable()
export class LoggerMiddleware
  implements NestMiddleware
{
  use(
    req: Request,
    res: Response,
    next: NextFunction,
  ) {
    console.log(
      `${req.method} ${req.originalUrl}`,
    );

    next();
  }
}
```

Register:

```ts
import {
  MiddlewareConsumer,
  Module,
  NestModule,
} from '@nestjs/common';

@Module({})
export class AppModule
  implements NestModule
{
  configure(
    consumer: MiddlewareConsumer,
  ) {
    consumer
      .apply(LoggerMiddleware)
      .forRoutes('*');
  }
}
```

---

# 19. Guards

Guards determine whether a request can continue.

Common use:

```text
Authentication
Authorization
Roles
Permissions
```

Create:

```bash
nest g guard auth
```

Example:

```ts
import {
  CanActivate,
  ExecutionContext,
  Injectable,
} from '@nestjs/common';

@Injectable()
export class AuthGuard
  implements CanActivate
{
  canActivate(
    context: ExecutionContext,
  ): boolean {
    const request =
      context.switchToHttp().getRequest();

    return Boolean(request.headers.authorization);
  }
}
```

Use:

```ts
import { UseGuards } from '@nestjs/common';

@UseGuards(AuthGuard)
@Get('profile')
getProfile() {
  return {
    message: 'Authenticated',
  };
}
```

---

# 20. Interceptors

Interceptors can run code before and after a handler.

Useful for:

* Logging
* Response transformation
* Timing
* Caching
* Error handling

Example:

```ts
import {
  CallHandler,
  ExecutionContext,
  Injectable,
  NestInterceptor,
} from '@nestjs/common';

import { Observable, tap } from 'rxjs';

@Injectable()
export class LoggingInterceptor
  implements NestInterceptor
{
  intercept(
    context: ExecutionContext,
    next: CallHandler,
  ): Observable<any> {
    const started = Date.now();

    return next.handle().pipe(
      tap(() => {
        console.log(
          `Request took ${
            Date.now() - started
          }ms`,
        );
      }),
    );
  }
}
```

Use:

```ts
@UseInterceptors(LoggingInterceptor)
@Get()
findAll() {
  return [];
}
```

---

# 21. Custom Decorators

You can create reusable decorators.

Example:

```ts
import {
  createParamDecorator,
  ExecutionContext,
} from '@nestjs/common';

export const CurrentUser =
  createParamDecorator(
    (
      data: unknown,
      context: ExecutionContext,
    ) => {
      const request =
        context.switchToHttp().getRequest();

      return request.user;
    },
  );
```

Use:

```ts
@Get('profile')
getProfile(
  @CurrentUser() user: any,
) {
  return user;
}
```

This becomes especially useful with JWT authentication.

---

# 22. Configuration and Environment Variables

Install:

```bash
npm install @nestjs/config
```

Create:

```text
.env
```

```env
PORT=3000
DATABASE_URL=postgresql://postgres:password@localhost:5432/mydb
JWT_SECRET=change-this-secret
```

## `app.module.ts`

```ts
import { Module } from '@nestjs/common';
import { ConfigModule } from '@nestjs/config';

@Module({
  imports: [
    ConfigModule.forRoot({
      isGlobal: true,
    }),
  ],
})
export class AppModule {}
```

Use:

```ts
import { ConfigService } from '@nestjs/config';

@Injectable()
export class AppService {
  constructor(
    private readonly configService: ConfigService,
  ) {}

  getPort() {
    return this.configService.get<number>('PORT');
  }
}
```

## `.gitignore`

```gitignore
node_modules/
dist/
.env
.env.*
!.env.example
```

Create:

```text
.env.example
```

```env
PORT=3000
DATABASE_URL=
JWT_SECRET=
```

Never commit real secrets.

---

# 23. CRUD API

A typical CRUD API contains:

```text
POST   /users
GET    /users
GET    /users/:id
PATCH  /users/:id
DELETE /users/:id
```

Generate:

```bash
nest g resource users
```

Nest CLI can generate a resource with controller, service, DTOs, entity, and related files depending on the selected options.

---

# 24. Complete CRUD Without Database

This example uses an in-memory array.

## `users.service.ts`

```ts
import {
  Injectable,
  NotFoundException,
} from '@nestjs/common';

import { CreateUserDto } from './dto/create-user.dto';
import { UpdateUserDto } from './dto/update-user.dto';

interface User {
  id: number;
  name: string;
  email: string;
}

@Injectable()
export class UsersService {
  private users: User[] = [];

  private nextId = 1;

  create(dto: CreateUserDto) {
    const user: User = {
      id: this.nextId++,
      name: dto.name,
      email: dto.email,
    };

    this.users.push(user);

    return user;
  }

  findAll() {
    return this.users;
  }

  findOne(id: number) {
    const user = this.users.find(
      (user) => user.id === id,
    );

    if (!user) {
      throw new NotFoundException(
        'User not found',
      );
    }

    return user;
  }

  update(
    id: number,
    dto: UpdateUserDto,
  ) {
    const user = this.findOne(id);

    if (dto.name !== undefined) {
      user.name = dto.name;
    }

    if (dto.email !== undefined) {
      user.email = dto.email;
    }

    return user;
  }

  remove(id: number) {
    const index = this.users.findIndex(
      (user) => user.id === id,
    );

    if (index === -1) {
      throw new NotFoundException(
        'User not found',
      );
    }

    this.users.splice(index, 1);

    return {
      message: 'User deleted',
    };
  }
}
```

## `create-user.dto.ts`

```ts
import {
  IsEmail,
  IsNotEmpty,
} from 'class-validator';

export class CreateUserDto {
  @IsNotEmpty()
  name: string;

  @IsEmail()
  email: string;
}
```

## `update-user.dto.ts`

```ts
import {
  IsEmail,
  IsOptional,
  IsString,
} from 'class-validator';

export class UpdateUserDto {
  @IsOptional()
  @IsString()
  name?: string;

  @IsOptional()
  @IsEmail()
  email?: string;
}
```

## `users.controller.ts`

```ts
import {
  Body,
  Controller,
  Delete,
  Get,
  Param,
  ParseIntPipe,
  Patch,
  Post,
} from '@nestjs/common';

import { UsersService } from './users.service';
import { CreateUserDto } from './dto/create-user.dto';
import { UpdateUserDto } from './dto/update-user.dto';

@Controller('users')
export class UsersController {
  constructor(
    private readonly usersService: UsersService,
  ) {}

  @Post()
  create(
    @Body() dto: CreateUserDto,
  ) {
    return this.usersService.create(dto);
  }

  @Get()
  findAll() {
    return this.usersService.findAll();
  }

  @Get(':id')
  findOne(
    @Param('id', ParseIntPipe) id: number,
  ) {
    return this.usersService.findOne(id);
  }

  @Patch(':id')
  update(
    @Param('id', ParseIntPipe) id: number,
    @Body() dto: UpdateUserDto,
  ) {
    return this.usersService.update(
      id,
      dto,
    );
  }

  @Delete(':id')
  remove(
    @Param('id', ParseIntPipe) id: number,
  ) {
    return this.usersService.remove(id);
  }
}
```

---

# 25. Database with TypeORM

Install:

```bash
npm install @nestjs/typeorm typeorm pg
```

For PostgreSQL.

## `app.module.ts`

```ts
import { Module } from '@nestjs/common';
import { TypeOrmModule } from '@nestjs/typeorm';

@Module({
  imports: [
    TypeOrmModule.forRoot({
      type: 'postgres',
      host: 'localhost',
      port: 5432,
      username: 'postgres',
      password: 'password',
      database: 'nestdb',
      autoLoadEntities: true,
      synchronize: false,
    }),
  ],
})
export class AppModule {}
```

> `synchronize: true` can be convenient for learning but should generally not be used for production database schema management.

## Entity

```ts
import {
  Column,
  Entity,
  PrimaryGeneratedColumn,
} from 'typeorm';

@Entity('users')
export class User {
  @PrimaryGeneratedColumn()
  id: number;

  @Column()
  name: string;

  @Column({ unique: true })
  email: string;
}
```

Register:

```ts
@Module({
  imports: [
    TypeOrmModule.forFeature([
      User,
    ]),
  ],
})
export class UsersModule {}
```

Inject repository:

```ts
@Injectable()
export class UsersService {
  constructor(
    @InjectRepository(User)
    private readonly usersRepository:
      Repository<User>,
  ) {}

  findAll() {
    return this.usersRepository.find();
  }
}
```

---

# 26. Database with Prisma

Prisma is another popular database approach.

Install:

```bash
npm install prisma @prisma/client
```

Initialize:

```bash
npx prisma init
```

Example schema:

## `prisma/schema.prisma`

```prisma
datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

generator client {
  provider = "prisma-client-js"
}

model User {
  id        Int      @id @default(autoincrement())
  name      String
  email     String   @unique
  createdAt DateTime @default(now())
}
```

Migration:

```bash
npx prisma migrate dev --name init
```

Generate client:

```bash
npx prisma generate
```

Create Prisma service:

```ts
import {
  Injectable,
  OnModuleInit,
} from '@nestjs/common';

import { PrismaClient } from '@prisma/client';

@Injectable()
export class PrismaService
  extends PrismaClient
  implements OnModuleInit
{
  async onModuleInit() {
    await this.$connect();
  }
}
```

Use:

```ts
@Injectable()
export class UsersService {
  constructor(
    private readonly prisma: PrismaService,
  ) {}

  findAll() {
    return this.prisma.user.findMany();
  }

  findOne(id: number) {
    return this.prisma.user.findUnique({
      where: { id },
    });
  }

  create(data: {
    name: string;
    email: string;
  }) {
    return this.prisma.user.create({
      data,
    });
  }
}
```

---

# 27. Authentication with JWT

Install:

```bash
npm install @nestjs/jwt
```

A production authentication system normally contains:

```text
Register
   ↓
Hash Password
   ↓
Save User
   ↓
Login
   ↓
Verify Password
   ↓
Create JWT
   ↓
Client sends Bearer token
   ↓
JWT Guard
   ↓
Protected Controller
```

Install Passport support:

```bash
npm install @nestjs/passport passport
npm install passport-jwt
npm install @types/passport-jwt --save-dev
```

JWT module:

```ts
import { Module } from '@nestjs/common';
import { JwtModule } from '@nestjs/jwt';

@Module({
  imports: [
    JwtModule.register({
      secret: process.env.JWT_SECRET,
      signOptions: {
        expiresIn: '15m',
      },
    }),
  ],
})
export class AuthModule {}
```

Create token:

```ts
@Injectable()
export class AuthService {
  constructor(
    private readonly jwtService: JwtService,
  ) {}

  async login(user: {
    id: number;
    email: string;
  }) {
    const payload = {
      sub: user.id,
      email: user.email,
    };

    return {
      access_token:
        await this.jwtService.signAsync(
          payload,
        ),
    };
  }
}
```

---

# 28. Authorization and Roles

Authentication answers:

> Who are you?

Authorization answers:

> What are you allowed to do?

Create roles:

```ts
export enum Role {
  USER = 'user',
  ADMIN = 'admin',
}
```

Decorator:

```ts
import { SetMetadata } from '@nestjs/common';

export const Roles = (
  ...roles: Role[]
) => SetMetadata('roles', roles);
```

Use:

```ts
@Roles(Role.ADMIN)
@Get('admin')
adminOnly() {
  return {
    message: 'Admin area',
  };
}
```

A roles guard can read the metadata and compare it with the authenticated user.

---

# 29. Swagger / OpenAPI

Install:

```bash
npm install @nestjs/swagger
```

## `main.ts`

```ts
import { NestFactory } from '@nestjs/core';
import {
  DocumentBuilder,
  SwaggerModule,
} from '@nestjs/swagger';

import { AppModule } from './app.module';

async function bootstrap() {
  const app =
    await NestFactory.create(AppModule);

  const config =
    new DocumentBuilder()
      .setTitle('My API')
      .setDescription(
        'NestJS REST API documentation',
      )
      .setVersion('1.0')
      .addBearerAuth()
      .build();

  const document =
    SwaggerModule.createDocument(
      app,
      config,
    );

  SwaggerModule.setup(
    'docs',
    app,
    document,
  );

  await app.listen(3000);
}

bootstrap();
```

Open:

```text
http://localhost:3000/docs
```

DTO example:

```ts
import {
  ApiProperty,
} from '@nestjs/swagger';

export class CreateUserDto {
  @ApiProperty({
    example: 'Dara',
  })
  name: string;

  @ApiProperty({
    example: 'dara@example.com',
  })
  email: string;
}
```

---

# 30. API Versioning

Enable URI versioning:

```ts
app.enableVersioning({
  type: VersioningType.URI,
});
```

Import:

```ts
import {
  VersioningType,
} from '@nestjs/common';
```

Controller:

```ts
@Controller({
  path: 'users',
  version: '1',
})
export class UsersController {
  @Get()
  findAll() {
    return [];
  }
}
```

Request:

```http
GET /v1/users
```

---

# 31. CORS

Enable CORS:

```ts
async function bootstrap() {
  const app =
    await NestFactory.create(AppModule);

  app.enableCors();

  await app.listen(3000);
}
```

More restrictive:

```ts
app.enableCors({
  origin: [
    'http://localhost:3001',
  ],
  credentials: true,
});
```

Production should use a specific trusted origin rather than allowing everything.

---

# 32. Helmet

Install:

```bash
npm install helmet
```

Use:

```ts
import helmet from 'helmet';

async function bootstrap() {
  const app =
    await NestFactory.create(AppModule);

  app.use(helmet());

  await app.listen(3000);
}
```

Helmet adds security-related HTTP headers.

---

# 33. Rate Limiting

Install:

```bash
npm install @nestjs/throttler
```

Configure:

```ts
import { Module } from '@nestjs/common';
import {
  ThrottlerModule,
} from '@nestjs/throttler';

@Module({
  imports: [
    ThrottlerModule.forRoot([
      {
        ttl: 60000,
        limit: 100,
      },
    ]),
  ],
})
export class AppModule {}
```

Meaning:

```text
100 requests
within 60 seconds
```

Adjust the values according to your application.

---

# 34. File Upload

NestJS supports multipart file uploads.

Controller:

```ts
import {
  Controller,
  Post,
  UploadedFile,
  UseInterceptors,
} from '@nestjs/common';

import {
  FileInterceptor,
} from '@nestjs/platform-express';

@Controller('files')
export class FilesController {
  @Post('upload')
  @UseInterceptors(
    FileInterceptor('file'),
  )
  upload(
    @UploadedFile() file: Express.Multer.File,
  ) {
    return {
      filename: file.originalname,
      size: file.size,
      mimetype: file.mimetype,
    };
  }
}
```

Send using:

```text
multipart/form-data
```

Field:

```text
file
```

For production, validate:

* File size
* MIME type
* Extension
* Filename
* Storage location
* Malware/security requirements

---

# 35. Logging

NestJS includes a Logger.

```ts
import {
  Injectable,
  Logger,
} from '@nestjs/common';

@Injectable()
export class UsersService {
  private readonly logger =
    new Logger(UsersService.name);

  findAll() {
    this.logger.log(
      'Finding all users',
    );

    return [];
  }
}
```

Other methods:

```ts
this.logger.log('Information');
this.logger.warn('Warning');
this.logger.error('Error');
this.logger.debug('Debug');
this.logger.verbose('Verbose');
```

---

# 36. Testing

Testing is important for serious applications.

NestJS supports unit and end-to-end testing workflows. The generated projects include test tooling.

## Unit test

Example service:

```ts
import { Injectable } from '@nestjs/common';

@Injectable()
export class CalculatorService {
  add(
    a: number,
    b: number,
  ) {
    return a + b;
  }
}
```

Test:

```ts
describe('CalculatorService', () => {
  let service: CalculatorService;

  beforeEach(() => {
    service = new CalculatorService();
  });

  it('should add numbers', () => {
    expect(
      service.add(2, 3),
    ).toBe(5);
  });
});
```

Run:

```bash
npm test
```

---

# 37. E2E Testing

E2E means:

> End-to-End

It tests the application through HTTP instead of testing only an individual class.

Typical flow:

```text
HTTP Request
     ↓
Middleware
     ↓
Guard
     ↓
Interceptor
     ↓
Controller
     ↓
Service
     ↓
Database
     ↓
HTTP Response
```

Example:

```ts
describe('Users API', () => {
  it('/users (GET)', () => {
    return request(app.getHttpServer())
      .get('/users')
      .expect(200);
  });
});
```

---

# 38. Caching

Caching can improve performance.

Typical examples:

```text
Database query
API response
Expensive calculations
External API responses
```

A cache architecture might be:

```text
Client
  ↓
NestJS
  ↓
Cache
  ├── HIT → Return cached data
  │
  └── MISS
        ↓
      Database
        ↓
      Save cache
        ↓
      Return
```

For distributed production systems, Redis is a common choice.

---

# 39. Events

NestJS can use event-driven architecture.

Install:

```bash
npm install @nestjs/event-emitter
```

Module:

```ts
import { Module } from '@nestjs/common';
import {
  EventEmitterModule,
} from '@nestjs/event-emitter';

@Module({
  imports: [
    EventEmitterModule.forRoot(),
  ],
})
export class AppModule {}
```

Emit:

```ts
this.eventEmitter.emit(
  'user.created',
  {
    userId: user.id,
  },
);
```

Listen:

```ts
import {
  OnEvent,
} from '@nestjs/event-emitter';

@OnEvent('user.created')
handleUserCreated(payload: {
  userId: number;
}) {
  console.log(
    'User created:',
    payload.userId,
  );
}
```

Useful for:

```text
Email notifications
Audit logs
Notifications
Analytics
Background workflows
```

---

# 40. Queues

Queues are useful for background jobs.

Examples:

```text
Send email
Generate PDF
Process images
Process payments
Send notifications
```

Typical architecture:

```text
API
 ↓
Queue
 ↓
Worker
 ↓
Long-running job
```

Redis-backed queues are a common approach.

The important idea is:

> Do not make the HTTP request wait for expensive background work when it can safely be processed asynchronously.

---

# 41. WebSockets

NestJS supports WebSocket gateways.

Install:

```bash
npm install @nestjs/websockets @nestjs/platform-socket.io
```

Gateway:

```ts
import {
  SubscribeMessage,
  WebSocketGateway,
} from '@nestjs/websockets';

@WebSocketGateway()
export class ChatGateway {
  @SubscribeMessage('message')
  handleMessage(
    client: any,
    payload: string,
  ) {
    return {
      event: 'message',
      data: payload,
    };
  }
}
```

Use cases:

```text
Chat
Live notifications
Real-time dashboards
Online presence
Gaming
Live tracking
```

---

# 42. GraphQL

NestJS supports GraphQL.

Install:

```bash
npm install @nestjs/graphql @nestjs/apollo graphql
```

GraphQL separates the API layer from traditional REST routing.

Example concept:

```graphql
query {
  users {
    id
    name
    email
  }
}
```

Mutation:

```graphql
mutation {
  createUser(
    name: "Dara"
    email: "dara@example.com"
  ) {
    id
    name
  }
}
```

GraphQL is especially useful when clients need flexible data selection.

---

# 43. Microservices

NestJS supports microservices.

Common transports include:

```text
TCP
Redis
MQTT
NATS
RabbitMQ
Kafka
gRPC
```

Typical architecture:

```text
                    ┌── User Service
                    │
API Gateway ────────┼── Order Service
                    │
                    ├── Payment Service
                    │
                    └── Notification Service
```

Instead of:

```text
Client
  ↓
One huge application
```

you can split functionality into independently deployable services.

## Important

Do not start with microservices just because they sound advanced.

For many applications:

```text
Modular Monolith
```

is simpler and more appropriate.

---

# 44. Health Checks

Production applications should expose health information.

Typical endpoint:

```http
GET /health
```

Response:

```json
{
  "status": "ok"
}
```

Health checks can verify:

```text
Application
Database
Redis
External services
Disk
Memory
```

A load balancer or container orchestrator can use health endpoints to determine whether an instance is healthy.

---

# 45. Graceful Shutdown

Production applications should close resources cleanly.

Example:

```ts
async function bootstrap() {
  const app =
    await NestFactory.create(AppModule);

  app.enableShutdownHooks();

  await app.listen(3000);
}

bootstrap();
```

This is important for:

```text
Docker
Kubernetes
Cloud deployments
Rolling deployments
Database connections
Queues
WebSockets
```

---

# 46. Production Structure

A scalable project might look like:

```text
src/
│
├── main.ts
├── app.module.ts
│
├── config/
│   ├── configuration.ts
│   └── validation.ts
│
├── common/
│   ├── decorators/
│   ├── filters/
│   ├── guards/
│   ├── interceptors/
│   ├── middleware/
│   ├── pipes/
│   └── constants/
│
├── database/
│   ├── database.module.ts
│   └── migrations/
│
├── auth/
│   ├── auth.module.ts
│   ├── auth.controller.ts
│   ├── auth.service.ts
│   ├── dto/
│   ├── guards/
│   ├── strategies/
│   └── decorators/
│
├── users/
│   ├── users.module.ts
│   ├── users.controller.ts
│   ├── users.service.ts
│   ├── dto/
│   └── entities/
│
├── products/
│   ├── products.module.ts
│   ├── products.controller.ts
│   ├── products.service.ts
│   ├── dto/
│   └── entities/
│
└── orders/
    ├── orders.module.ts
    ├── orders.controller.ts
    ├── orders.service.ts
    ├── dto/
    └── entities/
```

---

# 47. Clean Architecture

For larger systems, separate responsibilities.

Example:

```text
Presentation
     ↓
Application
     ↓
Domain
     ↓
Infrastructure
```

## Presentation

Handles:

```text
HTTP
Controllers
DTOs
Guards
Serialization
```

## Application

Handles:

```text
Use Cases
Business workflows
Application services
```

## Domain

Contains:

```text
Entities
Business rules
Value objects
Domain interfaces
```

## Infrastructure

Contains:

```text
Database
Repositories
External APIs
Message brokers
Storage
```

Example:

```text
src/
├── domain/
│   └── users/
│       ├── entities/
│       └── repositories/
│
├── application/
│   └── users/
│       └── use-cases/
│
├── infrastructure/
│   ├── database/
│   └── external-services/
│
└── presentation/
    └── http/
        └── users/
```

---

# 48. Best Practices

## 48.1 Keep Controllers Thin

Bad:

```ts
@Post()
create(@Body() dto: CreateUserDto) {
  // 200 lines of business logic
}
```

Better:

```ts
@Post()
create(@Body() dto: CreateUserDto) {
  return this.usersService.create(dto);
}
```

---

## 48.2 Put Business Logic in Services

```text
Controller
   ↓
Service
   ↓
Repository
```

---

## 48.3 Validate Input

Use:

```ts
ValidationPipe
```

and DTO validation decorators.

---

## 48.4 Never Store Plain Passwords

Bad:

```ts
password: '123456'
```

Never store passwords directly.

Use a password hashing algorithm such as bcrypt or Argon2.

---

## 48.5 Never Commit Secrets

Never commit:

```text
.env
private keys
JWT secrets
database passwords
API keys
cloud credentials
```

---

## 48.6 Use Environment Variables

Bad:

```ts
const password = 'my-secret-password';
```

Better:

```ts
const password =
  process.env.DATABASE_PASSWORD;
```

Even better:

```ts
ConfigService
```

---

## 48.7 Use Pagination

Bad:

```ts
return repository.find();
```

for a table containing millions of records.

Better:

```text
GET /users?page=1&limit=20
```

---

## 48.8 Avoid Returning Sensitive Data

Do not return:

```json
{
  "id": 1,
  "email": "user@example.com",
  "passwordHash": "..."
}
```

Return:

```json
{
  "id": 1,
  "email": "user@example.com"
}
```

---

## 48.9 Use HTTP Status Codes Correctly

Common codes:

```text
200 OK
201 Created
204 No Content

400 Bad Request
401 Unauthorized
403 Forbidden
404 Not Found
409 Conflict
422 Unprocessable Entity

500 Internal Server Error
```

---

# 49. Common Mistakes

## Mistake 1 — Huge Controllers

Bad:

```text
Controller
 ├── validation
 ├── database
 ├── business logic
 ├── email
 ├── payment
 └── logging
```

Better:

```text
Controller
   ↓
Service
   ↓
Repository
```

---

## Mistake 2 — No DTO Validation

Bad:

```ts
@Post()
create(@Body() body: any) {
  return body;
}
```

Better:

```ts
@Post()
create(
  @Body() dto: CreateUserDto,
) {
  return this.service.create(dto);
}
```

---

## Mistake 3 — `any` Everywhere

Avoid:

```ts
const user: any = ...
```

Prefer:

```ts
interface User {
  id: number;
  name: string;
}
```

or domain/entity types where appropriate.

---

## Mistake 4 — Database Logic in Controllers

Bad:

```ts
@Controller('users')
export class UsersController {
  @Get()
  async users() {
    return database.query(
      'SELECT * FROM users',
    );
  }
}
```

Better:

```text
Controller
   ↓
Service
   ↓
Repository
   ↓
Database
```

---

## Mistake 5 — Hardcoded Secrets

Never:

```ts
const JWT_SECRET =
  'my-super-secret';
```

Use configuration.

---

## Mistake 6 — Returning Database Entities Directly Everywhere

For complex applications, consider dedicated response DTOs/serializers so your public API does not accidentally expose internal fields.

---

# 50. Production Checklist

Before deploying a NestJS application:

## Application

* [ ] TypeScript strictness enabled where practical
* [ ] Environment configuration
* [ ] Validation enabled
* [ ] Proper exception handling
* [ ] Logging configured
* [ ] Health endpoint
* [ ] Graceful shutdown

## Security

* [ ] HTTPS
* [ ] CORS configured
* [ ] Helmet
* [ ] Rate limiting
* [ ] Strong authentication
* [ ] Authorization
* [ ] Password hashing
* [ ] Secrets outside source code
* [ ] Input validation
* [ ] File upload restrictions

## Database

* [ ] Migrations
* [ ] Indexes
* [ ] Transactions where needed
* [ ] Connection pooling
* [ ] Backups
* [ ] No development `synchronize: true` in production

## API

* [ ] Swagger/OpenAPI
* [ ] API versioning where required
* [ ] Pagination
* [ ] Consistent error responses
* [ ] Proper HTTP status codes

## Testing

* [ ] Unit tests
* [ ] Integration tests
* [ ] E2E tests
* [ ] Authentication tests
* [ ] Authorization tests
* [ ] Validation tests

## Deployment

* [ ] Production build
* [ ] Environment variables
* [ ] Docker if appropriate
* [ ] Health checks
* [ ] Logging/monitoring
* [ ] Database migration strategy
* [ ] CI/CD

---

# 🧠 NestJS Request Lifecycle

A useful mental model is:

```text
Incoming Request
       │
       ▼
   Middleware
       │
       ▼
     Guards
       │
       ▼
    Interceptors
       │
       ▼
      Pipes
       │
       ▼
   Controller
       │
       ▼
     Service
       │
       ▼
 Repository / ORM
       │
       ▼
    Database
       │
       ▼
     Service
       │
       ▼
   Controller
       │
       ▼
    Interceptor
       │
       ▼
 HTTP Response
```

Understanding this flow is one of the most important things when learning NestJS.

---

# 🧩 NestJS Core Concepts

| Concept     | Responsibility                 |
| ----------- | ------------------------------ |
| Module      | Organize application features  |
| Controller  | Receive HTTP requests          |
| Provider    | Injectable dependency          |
| Service     | Business logic                 |
| DTO         | Define data shape              |
| Pipe        | Validate/transform             |
| Guard       | Allow/deny request             |
| Interceptor | Wrap request/response          |
| Middleware  | Execute before route handling  |
| Filter      | Handle exceptions              |
| Decorator   | Add metadata/reusable behavior |
| Repository  | Data access                    |
| Entity      | Database model                 |
| Gateway     | WebSocket communication        |

---

# 🏗 Recommended Learning Path

If you are a beginner, do NOT learn everything at once.

Follow this order:

```text
1. JavaScript
       ↓
2. TypeScript
       ↓
3. Node.js
       ↓
4. HTTP / REST
       ↓
5. NestJS CLI
       ↓
6. Modules
       ↓
7. Controllers
       ↓
8. Providers / Services
       ↓
9. Dependency Injection
       ↓
10. DTO
       ↓
11. Validation
       ↓
12. Pipes
       ↓
13. Exception Handling
       ↓
14. Database
       ↓
15. CRUD
       ↓
16. Authentication
       ↓
17. Authorization
       ↓
18. Swagger
       ↓
19. Testing
       ↓
20. Caching
       ↓
21. Queues
       ↓
22. WebSockets
       ↓
23. GraphQL
       ↓
24. Microservices
       ↓
25. Production / DevOps
```

---

# 🚀 Recommended Real-World Project

After learning the fundamentals, build:

## E-Commerce REST API

Features:

```text
Authentication
├── Register
├── Login
├── JWT
├── Refresh Token
└── Logout

Users
├── Profile
├── Roles
└── Permissions

Products
├── Create
├── Read
├── Update
├── Delete
├── Search
├── Filtering
└── Pagination

Categories
├── Create
├── Read
├── Update
└── Delete

Cart
├── Add Product
├── Remove Product
└── Update Quantity

Orders
├── Create Order
├── Order Items
├── Order Status
└── Order History

Payments
├── Payment
├── Payment Status
└── Webhooks

Admin
├── Dashboard
├── Users
├── Products
├── Orders
└── Reports

Infrastructure
├── PostgreSQL
├── Redis
├── Queue
├── Docker
└── CI/CD
```

---

# 📦 Example Final Architecture

```text
Client
  │
  ▼
Load Balancer
  │
  ▼
NestJS API
  │
  ├── Auth Module
  │
  ├── Users Module
  │
  ├── Products Module
  │
  ├── Orders Module
  │
  ├── Payments Module
  │
  └── Notifications Module
  │
  ├──────────────┐
  ▼              ▼
PostgreSQL      Redis
                   │
                   ▼
                 Queue
                   │
                   ▼
                Workers
```

---

# 🛠 Useful Nest CLI Commands

Create application:

```bash
nest new project-name
```

Generate module:

```bash
nest g module users
```

Generate controller:

```bash
nest g controller users
```

Generate service:

```bash
nest g service users
```

Generate guard:

```bash
nest g guard auth
```

Generate interceptor:

```bash
nest g interceptor logging
```

Generate pipe:

```bash
nest g pipe validation
```

Generate middleware:

```bash
nest g middleware logger
```

Generate resource:

```bash
nest g resource users
```

Build:

```bash
npm run build
```

Run development:

```bash
npm run start:dev
```

Run production:

```bash
npm run start:prod
```

Run tests:

```bash
npm test
```

Run E2E tests:

```bash
npm run test:e2e
```

---

# 📜 Example `package.json` Scripts

A typical project contains scripts similar to:

```json
{
  "scripts": {
    "build": "nest build",
    "format": "prettier --write \"src/**/*.ts\" \"test/**/*.ts\"",
    "start": "nest start",
    "start:dev": "nest start --watch",
    "start:debug": "nest start --debug --watch",
    "start:prod": "node dist/main",
    "lint": "eslint \"{src,apps,libs,test}/**/*.ts\" --fix",
    "test": "jest",
    "test:watch": "jest --watch",
    "test:cov": "jest --coverage",
    "test:debug": "node --inspect-brk -r tsconfig-paths/register -r ts-node/register node_modules/.bin/jest --runInBand",
    "test:e2e": "jest --config ./test/jest-e2e.json"
  }
}
```

Your exact generated scripts can differ depending on the NestJS CLI version and project setup.

---

# 🔐 Example Production `main.ts`

A more realistic production bootstrap:

```ts
import { ValidationPipe, VersioningType } from '@nestjs/common';
import { NestFactory } from '@nestjs/core';
import helmet from 'helmet';

import { AppModule } from './app.module';

async function bootstrap() {
  const app =
    await NestFactory.create(AppModule);

  // Security headers
  app.use(helmet());

  // CORS
  app.enableCors({
    origin: [
      'http://localhost:3001',
    ],
    credentials: true,
  });

  // Global validation
  app.useGlobalPipes(
    new ValidationPipe({
      whitelist: true,
      transform: true,
      forbidNonWhitelisted: true,
    }),
  );

  // API versioning
  app.enableVersioning({
    type: VersioningType.URI,
  });

  // Graceful shutdown
  app.enableShutdownHooks();

  // API prefix
  app.setGlobalPrefix('api');

  const port =
    process.env.PORT ?? 3000;

  await app.listen(port);
}

bootstrap();
```

API:

```text
GET /api/v1/users
```

---

# 🎯 Final Advice

## Beginner

Focus on:

```text
TypeScript
↓
Nest CLI
↓
Module
↓
Controller
↓
Service
↓
Dependency Injection
↓
DTO
↓
Validation
↓
CRUD
```

## Intermediate

Learn:

```text
PostgreSQL
↓
ORM
↓
Authentication
↓
JWT
↓
Authorization
↓
Swagger
↓
Testing
↓
Error Handling
```

## Advanced

Learn:

```text
Redis
↓
Caching
↓
Queues
↓
Events
↓
WebSockets
↓
GraphQL
↓
Microservices
↓
Observability
↓
Docker
↓
CI/CD
↓
Cloud Deployment
```

## Professional

Think about:

```text
Architecture
Security
Performance
Scalability
Maintainability
Testing
Observability
Database design
Failure handling
Deployment
```

---

# 📚 Official NestJS Documentation

The official NestJS documentation covers the core architecture, fundamentals, database integration, authentication, security, GraphQL, WebSockets, microservices, OpenAPI, testing, queues, caching, observability, and more.

Use the official documentation as the final reference when package APIs change.

---

# ⭐ Summary

NestJS is easiest to understand when you think in layers:

```text
                 NestJS
                    │
       ┌────────────┴────────────┐
       │                         │
   Presentation              Business
       │                         │
 Controller ──────────────── Service
       │                         │
     DTO                       Logic
       │                         │
     Guard                      │
       │                         │
     Pipe                       │
       └────────────┬────────────┘
                    │
                Repository
                    │
                    ▼
                Database
```

The most important rule is:

> **Keep responsibilities separated.**

Controllers handle requests.

Services handle business logic.

Repositories handle data access.

DTOs define input/output contracts.

Guards handle access control.

Pipes validate and transform data.

Interceptors handle cross-cutting request/response behavior.

Modules organize features.

This architecture is what allows a NestJS application to grow from a small API into a large production system.
