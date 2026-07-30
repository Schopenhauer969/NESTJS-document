# NestJS Complete Guide (English + Khmer) 🐈
## មគ្គុទ្ទេសក៍ពេញលេញ NestJS (ភាសាអង់គ្លេស + ខ្មែរ)

> A complete beginner-to-advanced guide to NestJS — a progressive Node.js framework for building efficient, reliable, and scalable server-side applications.
> មគ្គុទ្ទេសក៍ពេញលេញពីកម្រិតដំបូងដល់កម្រិតខ្ពស់សម្រាប់ NestJS — ជា framework Node.js ដែលប្រើសម្រាប់សាងសង់ server-side applications ប្រកបដោយប្រសិទ្ធភាព ជឿទុកចិត្តបាន និងអាចពង្រីកបាន។

![NestJS](https://img.shields.io/badge/NestJS-E0234E?style=for-the-badge&logo=nestjs&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=node.js&logoColor=white)

---

## 📚 Table of Contents / មាតិកា

1. [Introduction / សេចក្តីផ្តើម](#1-introduction--សេចក្តីផ្តើម)
2. [Prerequisites / លក្ខខណ្ឌតម្រូវ](#2-prerequisites--លក្ខខណ្ឌតម្រូវ)
3. [Installation & Setup / ការដំឡើង](#3-installation--setup--ការដំឡើង)
4. [Project Structure / រចនាសម្ព័ន្ធគម្រោង](#4-project-structure--រចនាសម្ព័ន្ធគម្រោង)
5. [Modules / ម៉ូឌុល](#5-modules--ម៉ូឌុល)
6. [Controllers / កុងត្រូលឡឺ](#6-controllers--កុងត្រូលឡឺ)
7. [Providers & Services / សេវាកម្ម](#7-providers--services--សេវាកម្ម)
8. [DTOs & Validation](#8-dtos--validation)
9. [Pipes](#9-pipes)
10. [Middleware](#10-middleware)
11. [Guards & Authentication (JWT)](#11-guards--authentication-jwt)
12. [Interceptors](#12-interceptors)
13. [Exception Filters](#13-exception-filters)
14. [Custom Decorators](#14-custom-decorators)
15. [Configuration (.env)](#15-configuration-env)
16. [Database with TypeORM (PostgreSQL)](#16-database-with-typeorm-postgresql)
17. [Relationships (One-to-Many, Many-to-Many)](#17-relationships-one-to-many-many-to-many)
18. [Swagger / OpenAPI Documentation](#18-swagger--openapi-documentation)
19. [Testing (Jest)](#19-testing-jest)
20. [WebSockets Gateway](#20-websockets-gateway)
21. [Microservices (Overview)](#21-microservices-overview)
22. [Task Scheduling & Queues](#22-task-scheduling--queues)
23. [Deployment (Docker)](#23-deployment-docker)
24. [Best Practices](#24-best-practices)
25. [Full Example: Task Manager API](#25-full-example-task-manager-api)

---

## 1. Introduction / សេចក្តីផ្តើម

**English:** NestJS is a framework for building efficient, scalable Node.js server-side applications. It uses progressive JavaScript, is built with and fully supports **TypeScript**, and combines elements of **OOP** (Object-Oriented Programming), **FP** (Functional Programming), and **FRP** (Functional Reactive Programming). Under the hood, NestJS uses robust HTTP server frameworks like **Express** (default) or **Fastify**.

**ខ្មែរ:** NestJS គឺជា framework មួយសម្រាប់សាងសង់ server-side applications របស់ Node.js ប្រកបដោយប្រសិទ្ធភាព និងអាចពង្រីកបាន។ វាប្រើ TypeScript ពេញលេញ ហើយរួមបញ្ចូលគំនិតនៃ OOP, FP និង FRP ចូលគ្នា។ ក្នុងខាងក្នុង NestJS ប្រើ HTTP server framework ដូចជា **Express** (លំនាំដើម) ឬ **Fastify**។

### Why NestJS? / ហេតុអ្វីជ្រើសរើស NestJS?

- **Architecture (ស្ថាបត្យកម្ម):** Inspired by Angular — organized with Modules, Controllers, Providers.
- **TypeScript first:** Strong typing reduces bugs / កាត់បន្ថយកំហុសដោយសារ type checking រឹងមាំ។
- **Dependency Injection (DI):** Built-in DI container makes code testable and maintainable.
- **Scalable (អាចពង្រីកបាន):** Great for microservices, GraphQL, WebSockets, REST APIs.
- **Ecosystem:** Official packages for TypeORM, Mongoose, Passport, Swagger, GraphQL, and more.

---

## 2. Prerequisites / លក្ខខណ្ឌតម្រូវ

**English:** Before starting, you should know:
- Basic **JavaScript / TypeScript**
- Basic **Node.js** and npm
- Basic understanding of **REST APIs**
- Basic **OOP** concepts (classes, decorators)

**ខ្មែរ:** មុននឹងចាប់ផ្តើម អ្នកគួរតែស្គាល់៖
- **JavaScript / TypeScript** កម្រិតមូលដ្ឋាន
- **Node.js** និង npm
- គោលការណ៍ **REST API**
- គោលការណ៍ **OOP** (class, decorator)

### Required Tools / ឧបករណ៍ត្រូវការ

| Tool | Version | Check Command |
|------|---------|----------------|
| Node.js | >= 18.x | `node -v` |
| npm | >= 9.x | `npm -v` |
| NestJS CLI | latest | `nest --version` |

---

## 3. Installation & Setup / ការដំឡើង

**English:** Install the NestJS CLI globally, then generate a new project.
**ខ្មែរ:** ដំឡើង NestJS CLI ជា global ជាមុនសិន បន្ទាប់មកបង្កើតគម្រោងថ្មី។

```bash
# Install NestJS CLI globally
npm install -g @nestjs/cli

# Create a new project
nest new my-nest-app

# Choose package manager: npm / yarn / pnpm
# ជ្រើសរើស package manager: npm / yarn / pnpm

# Navigate into the project
cd my-nest-app

# Run the development server
npm run start:dev
```

**English:** Your app now runs at `http://localhost:3000`.
**ខ្មែរ:** កម្មវិធីរបស់អ្នកកំពុងដំណើរការនៅ `http://localhost:3000` ។

### Useful CLI Commands / ពាក្យបញ្ជាមានប្រយោជន៍

```bash
nest generate module users      # or: nest g mo users
nest generate controller users  # or: nest g co users
nest generate service users     # or: nest g s users
nest generate resource users    # generates full CRUD module (REST/GraphQL/WS)
```

---

## 4. Project Structure / រចនាសម្ព័ន្ធគម្រោង

**English:** Default project structure after `nest new`:
**ខ្មែរ:** រចនាសម្ព័ន្ធគម្រោងលំនាំដើមបន្ទាប់ពី `nest new`:

```
my-nest-app/
├── src/
│   ├── app.controller.ts       # Root controller
│   ├── app.controller.spec.ts  # Unit test for controller
│   ├── app.module.ts           # Root module
│   ├── app.service.ts          # Root service
│   └── main.ts                 # Entry point (bootstrap)
├── test/
│   └── app.e2e-spec.ts         # End-to-end tests
├── nest-cli.json
├── package.json
├── tsconfig.json
└── tsconfig.build.json
```

**English:** As the app grows, organize by **feature module** (e.g., `users/`, `auth/`, `products/`) — each with its own controller, service, module, DTOs, and entities.
**ខ្មែរ:** នៅពេលកម្មវិធីធំឡើង គួរតែរៀបចំតាម **feature module** (ឧ. `users/`, `auth/`, `products/`) — នីមួយៗមាន controller, service, module, DTO និង entity ផ្ទាល់ខ្លួន។

```
src/
├── users/
│   ├── dto/
│   │   ├── create-user.dto.ts
│   │   └── update-user.dto.ts
│   ├── entities/
│   │   └── user.entity.ts
│   ├── users.controller.ts
│   ├── users.module.ts
│   └── users.service.ts
├── auth/
├── app.module.ts
└── main.ts
```

---

## 5. Modules / ម៉ូឌុល

**English:** A module is a class annotated with `@Module()`. It groups related controllers and providers together. Every NestJS app has at least one **root module** (`AppModule`).

**ខ្មែរ:** Module គឺជា class ដែលមាន decorator `@Module()`។ វារួមបញ្ចូល controller និង provider ដែលទាក់ទងគ្នា។ កម្មវិធី NestJS គ្រប់ដងតែងតែមាន **root module** យ៉ាងតិចមួយ (`AppModule`)។

```typescript
// src/users/users.module.ts
import { Module } from '@nestjs/common';
import { UsersController } from './users.controller';
import { UsersService } from './users.service';

@Module({
  imports: [],                    // other modules this module depends on
  controllers: [UsersController], // controllers belonging to this module
  providers: [UsersService],      // services/providers registered in this module
  exports: [UsersService],        // make UsersService available to other modules
})
export class UsersModule {}
```

```typescript
// src/app.module.ts
import { Module } from '@nestjs/common';
import { AppController } from './app.controller';
import { AppService } from './app.service';
import { UsersModule } from './users/users.module';

@Module({
  imports: [UsersModule],   // register feature modules here
  controllers: [AppController],
  providers: [AppService],
})
export class AppModule {}
```

**English:** `main.ts` bootstraps the root module:
**ខ្មែរ:** `main.ts` ជាចំណុចចាប់ផ្តើម bootstrap `root module`:

```typescript
// src/main.ts
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);
  await app.listen(3000);
  console.log(`Application running on: ${await app.getUrl()}`);
}
bootstrap();
```

---

## 6. Controllers / កុងត្រូលឡឺ

**English:** Controllers handle incoming HTTP requests and return responses. They are defined using `@Controller()` and route handlers use decorators like `@Get()`, `@Post()`, `@Put()`, `@Delete()`, `@Patch()`.

**ខ្មែរ:** Controller ទទួលខុសត្រូវទទួល HTTP request ហើយបញ្ជូន response ត្រឡប់មកវិញ។ វាកំណត់ដោយ `@Controller()` ហើយ route handler ប្រើ decorator ដូចជា `@Get()`, `@Post()`, `@Put()`, `@Delete()`, `@Patch()`។

```typescript
// src/users/users.controller.ts
import {
  Controller,
  Get,
  Post,
  Body,
  Param,
  Put,
  Delete,
  Query,
  HttpCode,
  HttpStatus,
  ParseIntPipe,
} from '@nestjs/common';
import { UsersService } from './users.service';
import { CreateUserDto } from './dto/create-user.dto';
import { UpdateUserDto } from './dto/update-user.dto';

@Controller('users') // base route: /users
export class UsersController {
  constructor(private readonly usersService: UsersService) {}

  // GET /users?role=admin
  @Get()
  findAll(@Query('role') role?: string) {
    return this.usersService.findAll(role);
  }

  // GET /users/5
  @Get(':id')
  findOne(@Param('id', ParseIntPipe) id: number) {
    return this.usersService.findOne(id);
  }

  // POST /users
  @Post()
  @HttpCode(HttpStatus.CREATED)
  create(@Body() createUserDto: CreateUserDto) {
    return this.usersService.create(createUserDto);
  }

  // PUT /users/5
  @Put(':id')
  update(
    @Param('id', ParseIntPipe) id: number,
    @Body() updateUserDto: UpdateUserDto,
  ) {
    return this.usersService.update(id, updateUserDto);
  }

  // DELETE /users/5
  @Delete(':id')
  @HttpCode(HttpStatus.NO_CONTENT)
  remove(@Param('id', ParseIntPipe) id: number) {
    return this.usersService.remove(id);
  }
}
```

**English:** Key parameter decorators:
**ខ្មែរ:** Decorator សំខាន់ៗសម្រាប់ parameter:

| Decorator | Purpose (EN) | ការប្រើប្រាស់ (KH) |
|-----------|---------------|----------------------|
| `@Body()` | Access request body | យក request body |
| `@Param()` | Access route params | យក param ពី URL |
| `@Query()` | Access query string | យក query string |
| `@Req()` | Access raw Express request | យក raw request object |
| `@Res()` | Access raw Express response | យក raw response object (use with care) |
| `@Headers()` | Access request headers | យក headers |

---

## 7. Providers & Services / សេវាកម្ម

**English:** Providers (usually services) contain business logic. They are marked with `@Injectable()` and injected into controllers or other providers via **Dependency Injection**.

**ខ្មែរ:** Provider (ជាទូទៅហៅថា service) មាន business logic។ វាកំណត់ដោយ `@Injectable()` ហើយត្រូវបាន inject ចូល controller ឬ provider ផ្សេងទៀតតាមរយៈ **Dependency Injection**។

```typescript
// src/users/users.service.ts
import { Injectable, NotFoundException } from '@nestjs/common';
import { CreateUserDto } from './dto/create-user.dto';
import { UpdateUserDto } from './dto/update-user.dto';

export interface User {
  id: number;
  name: string;
  email: string;
  role: string;
}

@Injectable()
export class UsersService {
  private users: User[] = [];
  private idCounter = 1;

  findAll(role?: string): User[] {
    if (role) {
      return this.users.filter((u) => u.role === role);
    }
    return this.users;
  }

  findOne(id: number): User {
    const user = this.users.find((u) => u.id === id);
    if (!user) {
      throw new NotFoundException(`User with ID ${id} not found`);
    }
    return user;
  }

  create(dto: CreateUserDto): User {
    const newUser: User = { id: this.idCounter++, ...dto, role: dto.role ?? 'user' };
    this.users.push(newUser);
    return newUser;
  }

  update(id: number, dto: UpdateUserDto): User {
    const user = this.findOne(id);
    Object.assign(user, dto);
    return user;
  }

  remove(id: number): void {
    const index = this.users.findIndex((u) => u.id === id);
    if (index === -1) {
      throw new NotFoundException(`User with ID ${id} not found`);
    }
    this.users.splice(index, 1);
  }
}
```

**English:** NestJS's DI container automatically resolves `UsersService` when it sees it in the `UsersController` constructor — you never call `new UsersService()` manually.

**ខ្មែរ:** DI container របស់ NestJS នឹង resolve `UsersService` ដោយស្វ័យប្រវត្តិនៅពេលឃើញនៅក្នុង constructor របស់ `UsersController` — អ្នកមិនចាំបាច់ហៅ `new UsersService()` ដោយផ្ទាល់ដៃទេ។

---

## 8. DTOs & Validation

**English:** A **DTO** (Data Transfer Object) defines the shape of data sent over the network. Combined with `class-validator` and `class-transformer`, NestJS can automatically validate incoming request bodies.

**ខ្មែរ:** **DTO** (Data Transfer Object) កំណត់រូបរាងទិន្នន័យដែលផ្ញើតាមបណ្តាញ។ ដោយរួមផ្សំជាមួយ `class-validator` និង `class-transformer` NestJS អាច validate request body ដោយស្វ័យប្រវត្តិ។

```bash
npm install class-validator class-transformer
```

```typescript
// src/users/dto/create-user.dto.ts
import { IsEmail, IsString, MinLength, IsOptional, IsIn } from 'class-validator';

export class CreateUserDto {
  @IsString()
  @MinLength(2, { message: 'Name must be at least 2 characters' })
  name: string;

  @IsEmail({}, { message: 'Please provide a valid email address' })
  email: string;

  @IsString()
  @MinLength(6, { message: 'Password must be at least 6 characters' })
  password: string;

  @IsOptional()
  @IsIn(['user', 'admin'])
  role?: string;
}
```

```typescript
// src/users/dto/update-user.dto.ts
import { PartialType } from '@nestjs/mapped-types';
import { CreateUserDto } from './create-user.dto';

// Makes all fields from CreateUserDto optional
export class UpdateUserDto extends PartialType(CreateUserDto) {}
```

**English:** Enable global validation in `main.ts` so every DTO is checked automatically:
**ខ្មែរ:** បើក global validation នៅក្នុង `main.ts` ដើម្បីឲ្យ DTO គ្រប់ខ្លួនត្រូវបានពិនិត្យដោយស្វ័យប្រវត្តិ៖

```typescript
// src/main.ts
import { NestFactory } from '@nestjs/core';
import { ValidationPipe } from '@nestjs/common';
import { AppModule } from './app.module';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);

  app.useGlobalPipes(
    new ValidationPipe({
      whitelist: true,            // strip properties not in the DTO
      forbidNonWhitelisted: true, // throw error if extra properties are sent
      transform: true,            // auto-transform payloads to DTO instances
    }),
  );

  await app.listen(3000);
}
bootstrap();
```

---

## 9. Pipes

**English:** Pipes transform or validate input data before it reaches a route handler. NestJS ships built-in pipes: `ValidationPipe`, `ParseIntPipe`, `ParseBoolPipe`, `ParseUUIDPipe`, `DefaultValuePipe`.

**ខ្មែរ:** Pipe ប្រើសម្រាប់ transform ឬ validate ទិន្នន័យមុននឹងទៅដល់ route handler។ NestJS មាន pipe built-in ដូចជា `ValidationPipe`, `ParseIntPipe`, `ParseBoolPipe`, `ParseUUIDPipe`, `DefaultValuePipe`។

```typescript
// Using built-in pipes directly on parameters
@Get(':id')
findOne(@Param('id', ParseIntPipe) id: number) {
  return this.usersService.findOne(id);
}

@Get()
findAll(
  @Query('page', new DefaultValuePipe(1), ParseIntPipe) page: number,
  @Query('limit', new DefaultValuePipe(10), ParseIntPipe) limit: number,
) {
  return this.usersService.paginate(page, limit);
}
```

**English:** Custom pipe example:
**ខ្មែរ:** ឧទាហរណ៍ pipe ផ្ទាល់ខ្លួន៖

```typescript
// src/common/pipes/trim.pipe.ts
import { PipeTransform, Injectable, ArgumentMetadata } from '@nestjs/common';

@Injectable()
export class TrimPipe implements PipeTransform {
  transform(value: any, metadata: ArgumentMetadata) {
    if (typeof value === 'string') {
      return value.trim();
    }
    if (typeof value === 'object' && value !== null) {
      Object.keys(value).forEach((key) => {
        if (typeof value[key] === 'string') {
          value[key] = value[key].trim();
        }
      });
    }
    return value;
  }
}
```

---

## 10. Middleware

**English:** Middleware runs **before** the route handler, similar to Express middleware. Useful for logging, request modification, or authentication checks.

**ខ្មែរ:** Middleware ដំណើរការ **មុន** route handler ស្រដៀងទៅ Express middleware។ មានប្រយោជន៍សម្រាប់ logging, កែប្រែ request ឬពិនិត្យ authentication។

```typescript
// src/common/middleware/logger.middleware.ts
import { Injectable, NestMiddleware } from '@nestjs/common';
import { Request, Response, NextFunction } from 'express';

@Injectable()
export class LoggerMiddleware implements NestMiddleware {
  use(req: Request, res: Response, next: NextFunction) {
    const start = Date.now();
    res.on('finish', () => {
      const ms = Date.now() - start;
      console.log(`${req.method} ${req.originalUrl} ${res.statusCode} - ${ms}ms`);
    });
    next();
  }
}
```

```typescript
// src/app.module.ts
import { Module, NestModule, MiddlewareConsumer, RequestMethod } from '@nestjs/common';
import { LoggerMiddleware } from './common/middleware/logger.middleware';
import { UsersModule } from './users/users.module';

@Module({
  imports: [UsersModule],
})
export class AppModule implements NestModule {
  configure(consumer: MiddlewareConsumer) {
    consumer
      .apply(LoggerMiddleware)
      .exclude({ path: 'health', method: RequestMethod.GET }) // skip some routes
      .forRoutes('*'); // apply to all routes
  }
}
```

---

## 11. Guards & Authentication (JWT)

**English:** Guards determine whether a request should be handled by the route handler, mostly used for **authentication** and **authorization**. Let's build JWT authentication with Passport.

**ខ្មែរ:** Guard កំណត់ថាតើ request គួរត្រូវបានដំណើរការដោយ route handler ដែរឬទេ ភាគច្រើនប្រើសម្រាប់ **authentication** និង **authorization**។ ខាងក្រោមនេះជាឧទាហរណ៍បង្កើត JWT authentication ជាមួយ Passport។

```bash
npm install @nestjs/jwt @nestjs/passport passport passport-jwt bcrypt
npm install -D @types/passport-jwt @types/bcrypt
```

```typescript
// src/auth/auth.module.ts
import { Module } from '@nestjs/common';
import { JwtModule } from '@nestjs/jwt';
import { PassportModule } from '@nestjs/passport';
import { AuthService } from './auth.service';
import { AuthController } from './auth.controller';
import { JwtStrategy } from './jwt.strategy';
import { UsersModule } from '../users/users.module';

@Module({
  imports: [
    UsersModule,
    PassportModule,
    JwtModule.register({
      secret: process.env.JWT_SECRET || 'change-this-secret',
      signOptions: { expiresIn: '1d' },
    }),
  ],
  controllers: [AuthController],
  providers: [AuthService, JwtStrategy],
  exports: [AuthService],
})
export class AuthModule {}
```

```typescript
// src/auth/auth.service.ts
import { Injectable, UnauthorizedException } from '@nestjs/common';
import { JwtService } from '@nestjs/jwt';
import * as bcrypt from 'bcrypt';
import { UsersService } from '../users/users.service';

@Injectable()
export class AuthService {
  constructor(
    private usersService: UsersService,
    private jwtService: JwtService,
  ) {}

  async validateUser(email: string, password: string) {
    const user = this.usersService.findAll().find((u) => u.email === email) as any;
    if (user && (await bcrypt.compare(password, user.password))) {
      const { password: _pw, ...result } = user;
      return result;
    }
    throw new UnauthorizedException('Invalid email or password');
  }

  async login(user: { id: number; email: string }) {
    const payload = { sub: user.id, email: user.email };
    return {
      access_token: this.jwtService.sign(payload),
    };
  }
}
```

```typescript
// src/auth/jwt.strategy.ts
import { Injectable } from '@nestjs/common';
import { PassportStrategy } from '@nestjs/passport';
import { ExtractJwt, Strategy } from 'passport-jwt';

@Injectable()
export class JwtStrategy extends PassportStrategy(Strategy) {
  constructor() {
    super({
      jwtFromRequest: ExtractJwt.fromAuthHeaderAsBearerToken(),
      ignoreExpiration: false,
      secretOrKey: process.env.JWT_SECRET || 'change-this-secret',
    });
  }

  // Runs after the JWT signature is verified
  async validate(payload: { sub: number; email: string }) {
    return { userId: payload.sub, email: payload.email };
  }
}
```

```typescript
// src/auth/jwt-auth.guard.ts
import { Injectable } from '@nestjs/common';
import { AuthGuard } from '@nestjs/passport';

@Injectable()
export class JwtAuthGuard extends AuthGuard('jwt') {}
```

```typescript
// src/auth/auth.controller.ts
import { Body, Controller, Post, UseGuards, Get, Request } from '@nestjs/common';
import { AuthService } from './auth.service';
import { JwtAuthGuard } from './jwt-auth.guard';

@Controller('auth')
export class AuthController {
  constructor(private authService: AuthService) {}

  @Post('login')
  async login(@Body() body: { email: string; password: string }) {
    const user = await this.authService.validateUser(body.email, body.password);
    return this.authService.login(user);
  }

  // Protected route example
  @UseGuards(JwtAuthGuard)
  @Get('profile')
  getProfile(@Request() req) {
    return req.user; // set by JwtStrategy.validate()
  }
}
```

**English:** Apply the guard on any controller/route you want to protect:
**ខ្មែរ:** អនុវត្ត guard លើ controller/route ណាមួយដែលអ្នកចង់ការពារ៖

```typescript
@UseGuards(JwtAuthGuard)
@Get('secure-data')
getSecureData() {
  return { message: 'This is protected data' };
}
```

### Role-based Guard / Guard តាមតួនាទី

```typescript
// src/auth/roles.guard.ts
import { CanActivate, ExecutionContext, Injectable } from '@nestjs/common';
import { Reflector } from '@nestjs/core';
import { ROLES_KEY } from './roles.decorator';

@Injectable()
export class RolesGuard implements CanActivate {
  constructor(private reflector: Reflector) {}

  canActivate(context: ExecutionContext): boolean {
    const requiredRoles = this.reflector.getAllAndOverride<string[]>(ROLES_KEY, [
      context.getHandler(),
      context.getClass(),
    ]);
    if (!requiredRoles) return true;

    const { user } = context.switchToHttp().getRequest();
    return requiredRoles.some((role) => user?.role === role);
  }
}
```

---

## 12. Interceptors

**English:** Interceptors can transform the result returned from a route handler, log execution time, or add extra logic before/after the handler runs (similar to AOP / middleware but with access to the return value).

**ខ្មែរ:** Interceptor អាច transform លទ្ធផលដែលត្រឡប់ពី route handler, log ពេលវេលាដំណើរការ ឬបន្ថែម logic មុន/ក្រោយ handler ដំណើរការ (ស្រដៀង AOP ប៉ុន្តែអាចចូលដំណើរការទិន្នន័យត្រឡប់)។

```typescript
// src/common/interceptors/logging.interceptor.ts
import {
  CallHandler,
  ExecutionContext,
  Injectable,
  NestInterceptor,
} from '@nestjs/common';
import { Observable } from 'rxjs';
import { tap } from 'rxjs/operators';

@Injectable()
export class LoggingInterceptor implements NestInterceptor {
  intercept(context: ExecutionContext, next: CallHandler): Observable<any> {
    const request = context.switchToHttp().getRequest();
    const now = Date.now();
    return next.handle().pipe(
      tap(() =>
        console.log(`${request.method} ${request.url} - ${Date.now() - now}ms`),
      ),
    );
  }
}
```

```typescript
// src/common/interceptors/transform.interceptor.ts
import { CallHandler, ExecutionContext, Injectable, NestInterceptor } from '@nestjs/common';
import { Observable } from 'rxjs';
import { map } from 'rxjs/operators';

export interface Response<T> {
  data: T;
  success: true;
  timestamp: string;
}

@Injectable()
export class TransformInterceptor<T> implements NestInterceptor<T, Response<T>> {
  intercept(context: ExecutionContext, next: CallHandler): Observable<Response<T>> {
    return next.handle().pipe(
      map((data) => ({
        data,
        success: true,
        timestamp: new Date().toISOString(),
      })),
    );
  }
}
```

**Usage / ការប្រើប្រាស់:**

```typescript
@UseInterceptors(LoggingInterceptor, TransformInterceptor)
@Controller('users')
export class UsersController { /* ... */ }
```

---

## 13. Exception Filters

**English:** Exception filters catch unhandled exceptions and format a clean error response. NestJS has a built-in exception layer, but you can customize it.

**ខ្មែរ:** Exception filter ចាប់យក exception ដែលមិនត្រូវបានគ្រប់គ្រង ហើយធ្វើទ្រង់ទ្រាយ error response ឲ្យស្អាត។ NestJS មាន exception layer built-in ប៉ុន្តែអ្នកអាចប្តូរតាមចិត្តបាន។

```typescript
// src/common/filters/http-exception.filter.ts
import {
  ExceptionFilter,
  Catch,
  ArgumentsHost,
  HttpException,
  HttpStatus,
} from '@nestjs/common';
import { Request, Response } from 'express';

@Catch(HttpException)
export class HttpExceptionFilter implements ExceptionFilter {
  catch(exception: HttpException, host: ArgumentsHost) {
    const ctx = host.switchToHttp();
    const response = ctx.getResponse<Response>();
    const request = ctx.getRequest<Request>();
    const status = exception.getStatus();
    const exceptionResponse = exception.getResponse();

    response.status(status).json({
      success: false,
      statusCode: status,
      timestamp: new Date().toISOString(),
      path: request.url,
      message:
        typeof exceptionResponse === 'string'
          ? exceptionResponse
          : (exceptionResponse as any).message,
    });
  }
}
```

**Register globally / ចុះឈ្មោះជា global:**

```typescript
// src/main.ts
app.useGlobalFilters(new HttpExceptionFilter());
```

---

## 14. Custom Decorators

**English:** Create your own parameter decorators to extract data cleanly, e.g., getting the current authenticated user.

**ខ្មែរ:** បង្កើត parameter decorator ផ្ទាល់ខ្លួនដើម្បីទាញយកទិន្នន័យបានស្អាត ឧ. ការទាញយក user ដែលបាន login រួច។

```typescript
// src/common/decorators/current-user.decorator.ts
import { createParamDecorator, ExecutionContext } from '@nestjs/common';

export const CurrentUser = createParamDecorator(
  (data: unknown, ctx: ExecutionContext) => {
    const request = ctx.switchToHttp().getRequest();
    return request.user;
  },
);
```

```typescript
// src/common/decorators/roles.decorator.ts
import { SetMetadata } from '@nestjs/common';

export const ROLES_KEY = 'roles';
export const Roles = (...roles: string[]) => SetMetadata(ROLES_KEY, roles);
```

**Usage / ការប្រើប្រាស់:**

```typescript
@UseGuards(JwtAuthGuard, RolesGuard)
@Roles('admin')
@Get('profile')
getProfile(@CurrentUser() user: any) {
  return user;
}
```

---

## 15. Configuration (.env)

**English:** Use `@nestjs/config` to manage environment variables cleanly across environments.

**ខ្មែរ:** ប្រើ `@nestjs/config` ដើម្បីគ្រប់គ្រង environment variable ឲ្យស្អាតលើគ្រប់ environment។

```bash
npm install @nestjs/config
```

```env
# .env
PORT=3000
DATABASE_HOST=localhost
DATABASE_PORT=5432
DATABASE_USER=postgres
DATABASE_PASSWORD=postgres
DATABASE_NAME=nest_app
JWT_SECRET=super-secret-key
```

```typescript
// src/app.module.ts
import { Module } from '@nestjs/common';
import { ConfigModule } from '@nestjs/config';

@Module({
  imports: [
    ConfigModule.forRoot({
      isGlobal: true,     // available everywhere without re-importing
      envFilePath: '.env',
    }),
  ],
})
export class AppModule {}
```

```typescript
// Usage in any service
import { Injectable } from '@nestjs/common';
import { ConfigService } from '@nestjs/config';

@Injectable()
export class DatabaseService {
  constructor(private configService: ConfigService) {
    const host = this.configService.get<string>('DATABASE_HOST');
    console.log(host);
  }
}
```

> ⚠️ **Important / សំខាន់:** Add `.env` to `.gitignore` — never commit secrets to GitHub.
> កុំដាក់ `.env` ចូល GitHub ជាដាច់ខាត — ត្រូវដាក់វាក្នុង `.gitignore`។

---

## 16. Database with TypeORM (PostgreSQL)

**English:** TypeORM is the most common ORM used with NestJS. Install the required packages:

**ខ្មែរ:** TypeORM ជា ORM ដែលគេប្រើញឹកញាប់បំផុតជាមួយ NestJS។ ដំឡើង package ចាំបាច់៖

```bash
npm install @nestjs/typeorm typeorm pg
```

```typescript
// src/app.module.ts
import { Module } from '@nestjs/common';
import { TypeOrmModule } from '@nestjs/typeorm';
import { ConfigModule, ConfigService } from '@nestjs/config';
import { UsersModule } from './users/users.module';

@Module({
  imports: [
    ConfigModule.forRoot({ isGlobal: true }),
    TypeOrmModule.forRootAsync({
      imports: [ConfigModule],
      inject: [ConfigService],
      useFactory: (config: ConfigService) => ({
        type: 'postgres',
        host: config.get('DATABASE_HOST'),
        port: config.get<number>('DATABASE_PORT'),
        username: config.get('DATABASE_USER'),
        password: config.get('DATABASE_PASSWORD'),
        database: config.get('DATABASE_NAME'),
        entities: [__dirname + '/**/*.entity{.ts,.js}'],
        synchronize: true, // ⚠️ development only — never use in production
      }),
    }),
    UsersModule,
  ],
})
export class AppModule {}
```

```typescript
// src/users/entities/user.entity.ts
import { Entity, Column, PrimaryGeneratedColumn, CreateDateColumn } from 'typeorm';

@Entity('users')
export class User {
  @PrimaryGeneratedColumn()
  id: number;

  @Column({ length: 100 })
  name: string;

  @Column({ unique: true })
  email: string;

  @Column()
  password: string;

  @Column({ default: 'user' })
  role: string;

  @CreateDateColumn()
  createdAt: Date;
}
```

```typescript
// src/users/users.module.ts (updated with TypeORM)
import { Module } from '@nestjs/common';
import { TypeOrmModule } from '@nestjs/typeorm';
import { User } from './entities/user.entity';
import { UsersController } from './users.controller';
import { UsersService } from './users.service';

@Module({
  imports: [TypeOrmModule.forFeature([User])],
  controllers: [UsersController],
  providers: [UsersService],
  exports: [UsersService],
})
export class UsersModule {}
```

```typescript
// src/users/users.service.ts (updated with Repository pattern)
import { Injectable, NotFoundException } from '@nestjs/common';
import { InjectRepository } from '@nestjs/typeorm';
import { Repository } from 'typeorm';
import { User } from './entities/user.entity';
import { CreateUserDto } from './dto/create-user.dto';
import { UpdateUserDto } from './dto/update-user.dto';

@Injectable()
export class UsersService {
  constructor(
    @InjectRepository(User)
    private usersRepository: Repository<User>,
  ) {}

  findAll(): Promise<User[]> {
    return this.usersRepository.find();
  }

  async findOne(id: number): Promise<User> {
    const user = await this.usersRepository.findOneBy({ id });
    if (!user) {
      throw new NotFoundException(`User with ID ${id} not found`);
    }
    return user;
  }

  create(dto: CreateUserDto): Promise<User> {
    const user = this.usersRepository.create(dto);
    return this.usersRepository.save(user);
  }

  async update(id: number, dto: UpdateUserDto): Promise<User> {
    const user = await this.findOne(id);
    Object.assign(user, dto);
    return this.usersRepository.save(user);
  }

  async remove(id: number): Promise<void> {
    const result = await this.usersRepository.delete(id);
    if (result.affected === 0) {
      throw new NotFoundException(`User with ID ${id} not found`);
    }
  }
}
```

---

## 17. Relationships (One-to-Many, Many-to-Many)

**English:** Example: a `User` can have many `Post`s (one-to-many), and a `Post` can have many `Tag`s (many-to-many).

**ខ្មែរ:** ឧទាហរណ៍៖ `User` ម្នាក់អាចមាន `Post` ច្រើន (one-to-many) ហើយ `Post` មួយអាចមាន `Tag` ច្រើន (many-to-many)។

```typescript
// src/posts/entities/post.entity.ts
import {
  Entity, Column, PrimaryGeneratedColumn, ManyToOne, ManyToMany, JoinTable,
} from 'typeorm';
import { User } from '../../users/entities/user.entity';
import { Tag } from './tag.entity';

@Entity('posts')
export class Post {
  @PrimaryGeneratedColumn()
  id: number;

  @Column()
  title: string;

  @Column('text')
  content: string;

  @ManyToOne(() => User, (user) => user.posts, { onDelete: 'CASCADE' })
  author: User;

  @ManyToMany(() => Tag, (tag) => tag.posts, { cascade: true })
  @JoinTable() // owning side creates the join table
  tags: Tag[];
}
```

```typescript
// src/users/entities/user.entity.ts (add relation)
import { OneToMany } from 'typeorm';
import { Post } from '../../posts/entities/post.entity';
// ...inside the User class:
@OneToMany(() => Post, (post) => post.author)
posts: Post[];
```

```typescript
// src/posts/entities/tag.entity.ts
import { Entity, Column, PrimaryGeneratedColumn, ManyToMany } from 'typeorm';
import { Post } from './post.entity';

@Entity('tags')
export class Tag {
  @PrimaryGeneratedColumn()
  id: number;

  @Column({ unique: true })
  name: string;

  @ManyToMany(() => Post, (post) => post.tags)
  posts: Post[];
}
```

**Querying with relations / ការសួរជាមួយ relation:**

```typescript
// Load a post together with its author and tags
this.postsRepository.find({ relations: ['author', 'tags'] });
```

---

## 18. Swagger / OpenAPI Documentation

**English:** NestJS integrates directly with Swagger to auto-generate interactive API documentation.

**ខ្មែរ:** NestJS ភ្ជាប់ជាមួយ Swagger ដោយផ្ទាល់ ដើម្បីបង្កើត API documentation ដោយស្វ័យប្រវត្តិ។

```bash
npm install @nestjs/swagger
```

```typescript
// src/main.ts
import { NestFactory } from '@nestjs/core';
import { SwaggerModule, DocumentBuilder } from '@nestjs/swagger';
import { AppModule } from './app.module';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);

  const config = new DocumentBuilder()
    .setTitle('Task Manager API')
    .setDescription('API documentation for the Task Manager application')
    .setVersion('1.0')
    .addBearerAuth() // enables JWT auth in Swagger UI
    .build();

  const document = SwaggerModule.createDocument(app, config);
  SwaggerModule.setup('api-docs', app, document); // available at /api-docs

  await app.listen(3000);
}
bootstrap();
```

```typescript
// Annotate DTOs and controllers for richer docs
import { ApiProperty } from '@nestjs/swagger';
import { IsEmail, IsString, MinLength } from 'class-validator';

export class CreateUserDto {
  @ApiProperty({ example: 'Sophea Chan', minLength: 2 })
  @IsString()
  @MinLength(2)
  name: string;

  @ApiProperty({ example: 'sophea@example.com' })
  @IsEmail()
  email: string;

  @ApiProperty({ example: 'strongPassword123', minLength: 6 })
  @IsString()
  @MinLength(6)
  password: string;
}
```

```typescript
import { ApiTags, ApiOperation, ApiBearerAuth } from '@nestjs/swagger';

@ApiTags('users')
@Controller('users')
export class UsersController {
  @ApiOperation({ summary: 'Get all users' })
  @Get()
  findAll() { /* ... */ }

  @ApiBearerAuth()
  @UseGuards(JwtAuthGuard)
  @Get('profile')
  getProfile(@Request() req) { /* ... */ }
}
```

---

## 19. Testing (Jest)

**English:** NestJS uses **Jest** by default. There are two kinds of tests: **unit tests** (`.spec.ts`) and **end-to-end tests** (`.e2e-spec.ts`).

**ខ្មែរ:** NestJS ប្រើ **Jest** ជាលំនាំដើម។ មាន test ពីរប្រភេទគឺ **unit test** (`.spec.ts`) និង **end-to-end test** (`.e2e-spec.ts`)។

```typescript
// src/users/users.service.spec.ts
import { Test, TestingModule } from '@nestjs/testing';
import { UsersService } from './users.service';
import { getRepositoryToken } from '@nestjs/typeorm';
import { User } from './entities/user.entity';
import { NotFoundException } from '@nestjs/common';

describe('UsersService', () => {
  let service: UsersService;
  const mockRepository = {
    find: jest.fn(),
    findOneBy: jest.fn(),
    create: jest.fn(),
    save: jest.fn(),
    delete: jest.fn(),
  };

  beforeEach(async () => {
    const module: TestingModule = await Test.createTestingModule({
      providers: [
        UsersService,
        { provide: getRepositoryToken(User), useValue: mockRepository },
      ],
    }).compile();

    service = module.get<UsersService>(UsersService);
  });

  it('should be defined', () => {
    expect(service).toBeDefined();
  });

  it('should throw NotFoundException when user does not exist', async () => {
    mockRepository.findOneBy.mockResolvedValue(null);
    await expect(service.findOne(999)).rejects.toThrow(NotFoundException);
  });

  it('should return all users', async () => {
    const users = [{ id: 1, name: 'Dara' }];
    mockRepository.find.mockResolvedValue(users);
    expect(await service.findAll()).toEqual(users);
  });
});
```

```typescript
// test/users.e2e-spec.ts
import { Test, TestingModule } from '@nestjs/testing';
import { INestApplication } from '@nestjs/common';
import * as request from 'supertest';
import { AppModule } from './../src/app.module';

describe('UsersController (e2e)', () => {
  let app: INestApplication;

  beforeAll(async () => {
    const moduleFixture: TestingModule = await Test.createTestingModule({
      imports: [AppModule],
    }).compile();

    app = moduleFixture.createNestApplication();
    await app.init();
  });

  it('/users (GET)', () => {
    return request(app.getHttpServer())
      .get('/users')
      .expect(200);
  });

  it('/users (POST) - should validate input', () => {
    return request(app.getHttpServer())
      .post('/users')
      .send({ name: 'A' }) // missing required fields
      .expect(400);
  });

  afterAll(async () => {
    await app.close();
  });
});
```

```bash
npm run test          # unit tests
npm run test:watch    # watch mode
npm run test:cov      # coverage report
npm run test:e2e      # end-to-end tests
```

---

## 20. WebSockets Gateway

**English:** NestJS supports real-time communication via WebSockets using `@WebSocketGateway()`.

**ខ្មែរ:** NestJS គាំទ្រការទំនាក់ទំនងជាបន្ទាន់តាមរយៈ WebSocket ដោយប្រើ `@WebSocketGateway()`។

```bash
npm install @nestjs/websockets @nestjs/platform-socket.io socket.io
```

```typescript
// src/chat/chat.gateway.ts
import {
  WebSocketGateway,
  WebSocketServer,
  SubscribeMessage,
  MessageBody,
  ConnectedSocket,
} from '@nestjs/websockets';
import { Server, Socket } from 'socket.io';

@WebSocketGateway({ cors: { origin: '*' } })
export class ChatGateway {
  @WebSocketServer()
  server: Server;

  @SubscribeMessage('sendMessage')
  handleMessage(
    @MessageBody() data: { room: string; message: string },
    @ConnectedSocket() client: Socket,
  ) {
    // Broadcast to everyone in the room
    this.server.to(data.room).emit('newMessage', data.message);
  }

  @SubscribeMessage('joinRoom')
  handleJoinRoom(
    @MessageBody() room: string,
    @ConnectedSocket() client: Socket,
  ) {
    client.join(room);
    client.emit('joinedRoom', room);
  }
}
```

```typescript
// src/chat/chat.module.ts
import { Module } from '@nestjs/common';
import { ChatGateway } from './chat.gateway';

@Module({
  providers: [ChatGateway],
})
export class ChatModule {}
```

---

## 21. Microservices (Overview)

**English:** NestJS can build microservices communicating over TCP, Redis, RabbitMQ, Kafka, gRPC, and more. Basic TCP example:

**ខ្មែរ:** NestJS អាចសាងសង់ microservice ដែលទំនាក់ទំនងតាម TCP, Redis, RabbitMQ, Kafka, gRPC ជាដើម។ ឧទាហរណ៍មូលដ្ឋានតាម TCP៖

```bash
npm install @nestjs/microservices
```

```typescript
// src/main.ts (microservice entry point)
import { NestFactory } from '@nestjs/core';
import { Transport, MicroserviceOptions } from '@nestjs/microservices';
import { AppModule } from './app.module';

async function bootstrap() {
  const app = await NestFactory.createMicroservice<MicroserviceOptions>(AppModule, {
    transport: Transport.TCP,
    options: { host: '127.0.0.1', port: 4000 },
  });
  await app.listen();
}
bootstrap();
```

```typescript
// Handling a message pattern
import { Controller } from '@nestjs/common';
import { MessagePattern, Payload } from '@nestjs/microservices';

@Controller()
export class MathController {
  @MessagePattern({ cmd: 'sum' })
  sum(@Payload() numbers: number[]): number {
    return numbers.reduce((a, b) => a + b, 0);
  }
}
```

---

## 22. Task Scheduling & Queues

**English:** Use `@nestjs/schedule` for cron jobs and `@nestjs/bull` (with Redis) for background job queues.

**ខ្មែរ:** ប្រើ `@nestjs/schedule` សម្រាប់ cron job និង `@nestjs/bull` (ជាមួយ Redis) សម្រាប់ job queue ក្នុងផ្ទៃខាងក្រោយ។

```bash
npm install @nestjs/schedule
```

```typescript
// src/tasks/tasks.service.ts
import { Injectable, Logger } from '@nestjs/common';
import { Cron, CronExpression } from '@nestjs/schedule';

@Injectable()
export class TasksService {
  private readonly logger = new Logger(TasksService.name);

  @Cron(CronExpression.EVERY_DAY_AT_MIDNIGHT)
  handleDailyCleanup() {
    this.logger.log('Running daily cleanup task...');
  }
}
```

```bash
npm install @nestjs/bull bull
```

```typescript
// src/queue/email.processor.ts
import { Process, Processor } from '@nestjs/bull';
import { Job } from 'bull';

@Processor('email')
export class EmailProcessor {
  @Process('send-welcome')
  async handleSendWelcome(job: Job<{ email: string }>) {
    console.log(`Sending welcome email to ${job.data.email}`);
  }
}
```

---

## 23. Deployment (Docker)

**English:** A production-ready Dockerfile using multi-stage builds:

**ខ្មែរ:** Dockerfile សម្រាប់ production ដោយប្រើ multi-stage build៖

```dockerfile
# Dockerfile
FROM node:20-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

FROM node:20-alpine AS production
WORKDIR /app
ENV NODE_ENV=production
COPY package*.json ./
RUN npm ci --omit=dev
COPY --from=build /app/dist ./dist
EXPOSE 3000
CMD ["node", "dist/main"]
```

```yaml
# docker-compose.yml
version: '3.8'
services:
  api:
    build: .
    ports:
      - '3000:3000'
    environment:
      - DATABASE_HOST=db
      - DATABASE_PORT=5432
    depends_on:
      - db
  db:
    image: postgres:16-alpine
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: postgres
      POSTGRES_DB: nest_app
    volumes:
      - pgdata:/var/lib/postgresql/data
    ports:
      - '5432:5432'
volumes:
  pgdata:
```

```bash
docker compose up --build
```

---

## 24. Best Practices

**English:**
- **Organize by feature module**, not by file type.
- Keep controllers **thin** — put logic in services.
- Always use **DTOs + ValidationPipe** for input validation.
- Never expose raw entities directly — use response DTOs when needed.
- Use **environment variables** for all secrets and config.
- Wrap all async DB operations with proper error handling.
- Write **unit tests** for services and **e2e tests** for endpoints.
- Use `class-transformer`'s `@Exclude()` to hide sensitive fields (like `password`) from responses.

**ខ្មែរ:**
- **រៀបចំតាម feature module** មិនមែនតាមប្រភេទ file ទេ។
- តម្កល់ controller ឲ្យ **ស្តើង** — ដាក់ logic ទៅក្នុង service វិញ។
- ត្រូវប្រើ **DTO + ValidationPipe** ជានិច្ចសម្រាប់ validate input។
- កុំបង្ហាញ entity ដើមដោយផ្ទាល់ — ប្រើ response DTO នៅពេលចាំបាច់។
- ប្រើ **environment variable** សម្រាប់ secret និង config ទាំងអស់។
- ត្រូវគ្រប់គ្រង error សម្រាប់ operation database async ទាំងអស់។
- សរសេរ **unit test** សម្រាប់ service និង **e2e test** សម្រាប់ endpoint។
- ប្រើ `@Exclude()` ពី `class-transformer` ដើម្បីលាក់ field រសើប (ដូចជា `password`) ពី response។

```typescript
// Example: hiding password field automatically
import { Exclude } from 'class-transformer';

export class User {
  id: number;
  name: string;
  email: string;

  @Exclude()
  password: string;
}
```

---

## 25. Full Example: Task Manager API

**English:** A minimal but complete feature module putting everything together — module, controller, service, DTOs, entity, and guard.

**ខ្មែរ:** feature module តូចមួយប៉ុន្តែពេញលេញ ដែលរួមបញ្ចូលអ្វីៗទាំងអស់ — module, controller, service, DTO, entity និង guard។

```typescript
// src/tasks/entities/task.entity.ts
import { Entity, PrimaryGeneratedColumn, Column, CreateDateColumn } from 'typeorm';

export enum TaskStatus {
  TODO = 'todo',
  IN_PROGRESS = 'in_progress',
  DONE = 'done',
}

@Entity('tasks')
export class Task {
  @PrimaryGeneratedColumn()
  id: number;

  @Column()
  title: string;

  @Column({ type: 'enum', enum: TaskStatus, default: TaskStatus.TODO })
  status: TaskStatus;

  @Column()
  ownerId: number;

  @CreateDateColumn()
  createdAt: Date;
}
```

```typescript
// src/tasks/dto/create-task.dto.ts
import { IsString, MinLength, IsEnum, IsOptional } from 'class-validator';
import { ApiProperty } from '@nestjs/swagger';
import { TaskStatus } from '../entities/task.entity';

export class CreateTaskDto {
  @ApiProperty({ example: 'Finish NestJS guide' })
  @IsString()
  @MinLength(3)
  title: string;

  @ApiProperty({ enum: TaskStatus, required: false })
  @IsOptional()
  @IsEnum(TaskStatus)
  status?: TaskStatus;
}
```

```typescript
// src/tasks/tasks.service.ts
import { Injectable, NotFoundException, ForbiddenException } from '@nestjs/common';
import { InjectRepository } from '@nestjs/typeorm';
import { Repository } from 'typeorm';
import { Task } from './entities/task.entity';
import { CreateTaskDto } from './dto/create-task.dto';

@Injectable()
export class TasksService {
  constructor(
    @InjectRepository(Task) private taskRepo: Repository<Task>,
  ) {}

  findAllForUser(ownerId: number): Promise<Task[]> {
    return this.taskRepo.find({ where: { ownerId } });
  }

  async findOne(id: number, ownerId: number): Promise<Task> {
    const task = await this.taskRepo.findOneBy({ id });
    if (!task) throw new NotFoundException(`Task ${id} not found`);
    if (task.ownerId !== ownerId) throw new ForbiddenException('Access denied');
    return task;
  }

  create(dto: CreateTaskDto, ownerId: number): Promise<Task> {
    const task = this.taskRepo.create({ ...dto, ownerId });
    return this.taskRepo.save(task);
  }

  async remove(id: number, ownerId: number): Promise<void> {
    await this.findOne(id, ownerId); // ensures ownership + existence
    await this.taskRepo.delete(id);
  }
}
```

```typescript
// src/tasks/tasks.controller.ts
import {
  Controller, Get, Post, Delete, Body, Param, ParseIntPipe, UseGuards,
} from '@nestjs/common';
import { ApiTags, ApiBearerAuth } from '@nestjs/swagger';
import { TasksService } from './tasks.service';
import { CreateTaskDto } from './dto/create-task.dto';
import { JwtAuthGuard } from '../auth/jwt-auth.guard';
import { CurrentUser } from '../common/decorators/current-user.decorator';

@ApiTags('tasks')
@ApiBearerAuth()
@UseGuards(JwtAuthGuard)
@Controller('tasks')
export class TasksController {
  constructor(private tasksService: TasksService) {}

  @Get()
  findAll(@CurrentUser() user: { userId: number }) {
    return this.tasksService.findAllForUser(user.userId);
  }

  @Get(':id')
  findOne(
    @Param('id', ParseIntPipe) id: number,
    @CurrentUser() user: { userId: number },
  ) {
    return this.tasksService.findOne(id, user.userId);
  }

  @Post()
  create(@Body() dto: CreateTaskDto, @CurrentUser() user: { userId: number }) {
    return this.tasksService.create(dto, user.userId);
  }

  @Delete(':id')
  remove(
    @Param('id', ParseIntPipe) id: number,
    @CurrentUser() user: { userId: number },
  ) {
    return this.tasksService.remove(id, user.userId);
  }
}
```

```typescript
// src/tasks/tasks.module.ts
import { Module } from '@nestjs/common';
import { TypeOrmModule } from '@nestjs/typeorm';
import { Task } from './entities/task.entity';
import { TasksController } from './tasks.controller';
import { TasksService } from './tasks.service';

@Module({
  imports: [TypeOrmModule.forFeature([Task])],
  controllers: [TasksController],
  providers: [TasksService],
})
export class TasksModule {}
```

**English:** Register `TasksModule` and `AuthModule` in `app.module.ts`, run `npm run start:dev`, then visit `http://localhost:3000/api-docs` to test everything through Swagger UI.

**ខ្មែរ:** ចុះឈ្មោះ `TasksModule` និង `AuthModule` នៅក្នុង `app.module.ts` រត់ `npm run start:dev` រួចចូលទៅកាន់ `http://localhost:3000/api-docs` ដើម្បីសាកល្បងអ្វីៗទាំងអស់តាមរយៈ Swagger UI។

---

## 📖 References / ឯកសារយោង

- Official Docs: https://docs.nestjs.com
- TypeORM Docs: https://typeorm.io
- class-validator: https://github.com/typestack/class-validator

---

## 📝 License

MIT © Heng — Feel free to use this guide for learning and sharing with the Khmer developer community.
MIT © Heng — សូមប្រើប្រាស់មគ្គុទ្ទេសក៍នេះដោយសេរីសម្រាប់ការសិក្សា និងចែករំលែកជាមួយសហគមន៍ developer ខ្មែរ។
