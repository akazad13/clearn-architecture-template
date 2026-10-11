# 🏛️ Enterprise Clean Architecture Solution Template

[![.NET](https://img.shields.io/badge/.NET-Core-512BD4?style=flat&logo=dotnet)](https://dotnet.microsoft.com/)
[![CQRS](https://img.shields.io/badge/Pattern-CQRS%20%2B%20MediatR-blueviolet?style=flat)](#)
[![Entity Framework Core](https://img.shields.io/badge/ORM-EF%20Core-blue?style=flat)](https://learn.microsoft.com/ef/core/)
[![PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL-336791?style=flat&logo=postgresql)](https://www.postgresql.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

An enterprise-ready **Clean Architecture** solution template built for **ASP.NET Core**, following Domain-Driven Design (DDD) principles, CQRS pattern, and strict architectural layer boundaries.

---

## 🏗️ Architectural Layers

`	ext
┌────────────────────────────────────────────────────────┐
│                   Presentation / API                   │
└───────────────────────────┬────────────────────────────┘
                            │
┌───────────────────────────▼────────────────────────────┐
│                    Application Layer                   │
│   (CQRS Commands & Queries, Behaviors, Validation)     │
└─────────────┬────────────────────────────┬─────────────┘
              │                            │
┌─────────────▼──────────┐      ┌──────────▼─────────────┐
│      Domain Layer      │      │  Infrastructure Layer  │
│  (Entities, ValueObjs, │      │ (EF Core, PostgreSQL,  │
│   Domain Events, DDD)  │      │  Auth, Serilog, Seq)   │
└────────────────────────┘      └────────────────────────┘
`

---

## 📦 What's Included in the Template?

- **SharedKernel**: Reusable Domain-Driven Design base primitives (Entities, AggregateRoots, ValueObjects, DomainEvents).
- **Domain Layer**: Pure business logic and domain models with zero external dependencies.
- **Application Layer**:
  - **CQRS Implementation**: Structured request pipelines with MediatR.
  - **Cross-Cutting Pipelines**: FluentValidation behaviors, performance profiling, and error handling.
- **Infrastructure Layer**:
  - **Persistence**: Entity Framework Core with PostgreSQL migrations.
  - **Security**: JWT Authentication & Permission-based fine-grained Authorization.
  - **Observability**: Structured logging with Serilog & Seq integration (available at http://localhost:8081).
  - **Resilience**: Outbox pattern support for reliable event publishing.
- **Testing Suites**:
  - Architecture unit tests enforcing layer boundary rules using NetArchTest.
  - Unit tests & functional tests.

---

## 🚀 Getting Started

### Prerequisites
- [.NET SDK](https://dotnet.microsoft.com/download)
- Docker Desktop (for running PostgreSQL and Seq)

### 1. Start Infrastructure via Docker
`ash
docker run -d --name postgres -p 5432:5432 -e POSTGRES_PASSWORD=postgres postgres:latest
docker run -d --name seq -p 8081:80 -e ACCEPT_EULA=Y datalust/seq:latest
`

### 2. Build and Run
`ash
dotnet restore
dotnet build
dotnet test
dotnet run --project src/Presentation.Api
`

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.