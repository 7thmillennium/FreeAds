# installation

`dotnet new mvc --auth Individual --framework netcoreapp2.1`

# update db settings

>>> add nuget entity postgresql 

>>> add settings for connection of db


file: /home/looper/netcore/FreeAds/appsettings.json

```
  "ConnectionStrings": {
   "DefaultConnection":"Host=localhost;Database=freeads;Username=admin;Password=admin"
  },
```

>> update ef db

`sudo dotnet ef database update`

```
info: Microsoft.EntityFrameworkCore.Infrastructure[10403]
      Entity Framework Core 2.1.1-rtm-30846 initialized 'ApplicationDbContext' using provider 'Npgsql.EntityFrameworkCore.PostgreSQL' with options: None
info: Microsoft.EntityFrameworkCore.Database.Command[20101]
      Executed DbCommand (19ms) [Parameters=[], CommandType='Text', CommandTimeout='30']
      SELECT EXISTS (SELECT 1 FROM pg_catalog.pg_class c JOIN pg_catalog.pg_namespace n ON n.oid=c.relnamespace WHERE c.relname='__EFMigrationsHistory');
info: Microsoft.EntityFrameworkCore.Database.Command[20101]
      Executed DbCommand (26ms) [Parameters=[], CommandType='Text', CommandTimeout='30']
      CREATE TABLE "__EFMigrationsHistory" (
          "MigrationId" varchar(150) NOT NULL,
          "ProductVersion" varchar(32) NOT NULL,
          CONSTRAINT "PK___EFMigrationsHistory" PRIMARY KEY ("MigrationId")
      );
info: Microsoft.EntityFrameworkCore.Database.Command[20101]
      Executed DbCommand (1ms) [Parameters=[], CommandType='Text', CommandTimeout='30']
      SELECT EXISTS (SELECT 1 FROM pg_catalog.pg_class c JOIN pg_catalog.pg_namespace n ON n.oid=c.relnamespace WHERE c.relname='__EFMigrationsHistory');
info: Microsoft.EntityFrameworkCore.Database.Command[20101]
      Executed DbCommand (1ms) [Parameters=[], CommandType='Text', CommandTimeout='30']
      SELECT "MigrationId", "ProductVersion"
      FROM "__EFMigrationsHistory"
      ORDER BY "MigrationId";
info: Microsoft.EntityFrameworkCore.Migrations[20402]
      Applying migration '00000000000000_CreateIdentitySchema'.
Applying migration '00000000000000_CreateIdentitySchema'.
info: Microsoft.EntityFrameworkCore.Database.Command[20101]
      Executed DbCommand (11ms) [Parameters=[], CommandType='Text', CommandTimeout='30']
      CREATE TABLE "AspNetRoles" (
          "Id" text NOT NULL,
          "Name" varchar(256) NULL,
          "NormalizedName" varchar(256) NULL,
          "ConcurrencyStamp" text NULL,
          CONSTRAINT "PK_AspNetRoles" PRIMARY KEY ("Id")
      );
info: Microsoft.EntityFrameworkCore.Database.Command[20101]
      Executed DbCommand (17ms) [Parameters=[], CommandType='Text', CommandTimeout='30']
      CREATE TABLE "AspNetUsers" (
          "Id" text NOT NULL,
          "UserName" varchar(256) NULL,
          "NormalizedUserName" varchar(256) NULL,
          "Email" varchar(256) NULL,
          "NormalizedEmail" varchar(256) NULL,
          "EmailConfirmed" boolean NOT NULL,
          "PasswordHash" text NULL,
          "SecurityStamp" text NULL,
          "ConcurrencyStamp" text NULL,
          "PhoneNumber" text NULL,
          "PhoneNumberConfirmed" boolean NOT NULL,
          "TwoFactorEnabled" boolean NOT NULL,
          "LockoutEnd" timestamp with time zone NULL,
          "LockoutEnabled" boolean NOT NULL,
          "AccessFailedCount" integer NOT NULL,
          CONSTRAINT "PK_AspNetUsers" PRIMARY KEY ("Id")
      );
info: Microsoft.EntityFrameworkCore.Database.Command[20101]
      Executed DbCommand (26ms) [Parameters=[], CommandType='Text', CommandTimeout='30']
      CREATE TABLE "AspNetRoleClaims" (
          "Id" integer NOT NULL,
          "RoleId" text NOT NULL,
          "ClaimType" text NULL,
          "ClaimValue" text NULL,
          CONSTRAINT "PK_AspNetRoleClaims" PRIMARY KEY ("Id"),
          CONSTRAINT "FK_AspNetRoleClaims_AspNetRoles_RoleId" FOREIGN KEY ("RoleId") REFERENCES "AspNetRoles" ("Id") ON DELETE CASCADE
      );
info: Microsoft.EntityFrameworkCore.Database.Command[20101]
      Executed DbCommand (11ms) [Parameters=[], CommandType='Text', CommandTimeout='30']
      CREATE TABLE "AspNetUserClaims" (
          "Id" integer NOT NULL,
          "UserId" text NOT NULL,
          "ClaimType" text NULL,
          "ClaimValue" text NULL,
          CONSTRAINT "PK_AspNetUserClaims" PRIMARY KEY ("Id"),
          CONSTRAINT "FK_AspNetUserClaims_AspNetUsers_UserId" FOREIGN KEY ("UserId") REFERENCES "AspNetUsers" ("Id") ON DELETE CASCADE
      );
info: Microsoft.EntityFrameworkCore.Database.Command[20101]
      Executed DbCommand (17ms) [Parameters=[], CommandType='Text', CommandTimeout='30']
      CREATE TABLE "AspNetUserLogins" (
          "LoginProvider" varchar(128) NOT NULL,
          "ProviderKey" varchar(128) NOT NULL,
          "ProviderDisplayName" text NULL,
          "UserId" text NOT NULL,
          CONSTRAINT "PK_AspNetUserLogins" PRIMARY KEY ("LoginProvider", "ProviderKey"),
          CONSTRAINT "FK_AspNetUserLogins_AspNetUsers_UserId" FOREIGN KEY ("UserId") REFERENCES "AspNetUsers" ("Id") ON DELETE CASCADE
      );
info: Microsoft.EntityFrameworkCore.Database.Command[20101]
      Executed DbCommand (25ms) [Parameters=[], CommandType='Text', CommandTimeout='30']
      CREATE TABLE "AspNetUserRoles" (
          "UserId" text NOT NULL,
          "RoleId" text NOT NULL,
          CONSTRAINT "PK_AspNetUserRoles" PRIMARY KEY ("UserId", "RoleId"),
          CONSTRAINT "FK_AspNetUserRoles_AspNetRoles_RoleId" FOREIGN KEY ("RoleId") REFERENCES "AspNetRoles" ("Id") ON DELETE CASCADE,
          CONSTRAINT "FK_AspNetUserRoles_AspNetUsers_UserId" FOREIGN KEY ("UserId") REFERENCES "AspNetUsers" ("Id") ON DELETE CASCADE
      );
info: Microsoft.EntityFrameworkCore.Database.Command[20101]
      Executed DbCommand (11ms) [Parameters=[], CommandType='Text', CommandTimeout='30']
      CREATE TABLE "AspNetUserTokens" (
          "UserId" text NOT NULL,
          "LoginProvider" varchar(128) NOT NULL,
          "Name" varchar(128) NOT NULL,
          "Value" text NULL,
          CONSTRAINT "PK_AspNetUserTokens" PRIMARY KEY ("UserId", "LoginProvider", "Name"),
          CONSTRAINT "FK_AspNetUserTokens_AspNetUsers_UserId" FOREIGN KEY ("UserId") REFERENCES "AspNetUsers" ("Id") ON DELETE CASCADE
      );
info: Microsoft.EntityFrameworkCore.Database.Command[20101]
      Executed DbCommand (8ms) [Parameters=[], CommandType='Text', CommandTimeout='30']
      CREATE INDEX "IX_AspNetRoleClaims_RoleId" ON "AspNetRoleClaims" ("RoleId");
info: Microsoft.EntityFrameworkCore.Database.Command[20101]
      Executed DbCommand (8ms) [Parameters=[], CommandType='Text', CommandTimeout='30']
      CREATE UNIQUE INDEX "RoleNameIndex" ON "AspNetRoles" ("NormalizedName");
info: Microsoft.EntityFrameworkCore.Database.Command[20101]
      Executed DbCommand (8ms) [Parameters=[], CommandType='Text', CommandTimeout='30']
      CREATE INDEX "IX_AspNetUserClaims_UserId" ON "AspNetUserClaims" ("UserId");
info: Microsoft.EntityFrameworkCore.Database.Command[20101]
      Executed DbCommand (8ms) [Parameters=[], CommandType='Text', CommandTimeout='30']
      CREATE INDEX "IX_AspNetUserLogins_UserId" ON "AspNetUserLogins" ("UserId");
info: Microsoft.EntityFrameworkCore.Database.Command[20101]
      Executed DbCommand (8ms) [Parameters=[], CommandType='Text', CommandTimeout='30']
      CREATE INDEX "IX_AspNetUserRoles_RoleId" ON "AspNetUserRoles" ("RoleId");
info: Microsoft.EntityFrameworkCore.Database.Command[20101]
      Executed DbCommand (8ms) [Parameters=[], CommandType='Text', CommandTimeout='30']
      CREATE INDEX "EmailIndex" ON "AspNetUsers" ("NormalizedEmail");
info: Microsoft.EntityFrameworkCore.Database.Command[20101]
      Executed DbCommand (8ms) [Parameters=[], CommandType='Text', CommandTimeout='30']
      CREATE UNIQUE INDEX "UserNameIndex" ON "AspNetUsers" ("NormalizedUserName");
info: Microsoft.EntityFrameworkCore.Database.Command[20101]
      Executed DbCommand (0ms) [Parameters=[], CommandType='Text', CommandTimeout='30']
      INSERT INTO "__EFMigrationsHistory" ("MigrationId", "ProductVersion")
      VALUES ('00000000000000_CreateIdentitySchema', '2.1.1-rtm-30846');
Done.


```