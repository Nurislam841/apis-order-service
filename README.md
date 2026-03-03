# Order Service (Go + Clean Architecture + REST)

## Overview

This project is a standalone **Order Service** implemented in **Go**, following **Clean Architecture principles**.

The service is responsible for handling order-related operations and exposes RESTful HTTP endpoints.
Its structure separates domain logic, use cases, data access, and HTTP delivery layers to ensure scalability and maintainability.

---

## Architecture

The project follows Clean Architecture layering:

```text
cmd → adapter → usecase → repository → entity
```

### Layer Responsibilities

* **entity/**
  Core business models and domain rules.

* **usecase/**
  Application business logic and orchestration.

* **repository/**
  Data persistence abstraction.

* **adapter/http/**
  HTTP handlers and routing.

* **cmd/**
  Application entry point.

This ensures:

* Clear separation of concerns
* Dependency inversion
* High testability
* Maintainable service design

---

## Project Structure

```text
apis-order-service-main/
│
├── cmd/
│   └── main.go
│
├── internal/
│   ├── adapter/
│   │   └── http/
│   │       ├── handler.go
│   │       └── router.go
│   │
│   ├── entity/
│   │   └── order.go
│   │
│   ├── repository/
│   │   └── order_repository.go
│   │
│   └── usecase/
│       └── order_usecase.go
│
├── go.mod
└── go.sum
```

---

## Domain Model

### Order Entity

The core domain entity is:

* `Order`

Typical fields include:

* ID
* ProductID
* Quantity
* Status
* CreatedAt

Business rules related to order creation and management are encapsulated in the `usecase` layer.

---

## API Endpoints

The service exposes REST endpoints for managing orders.

Typical operations:

```text
POST   /orders
GET    /orders
GET    /orders/{id}
PUT    /orders/{id}
DELETE /orders/{id}
```

These endpoints are implemented in:

```text
internal/adapter/http/
```

---

## How to Run

### 1. Clone repository

```bash
git clone <your-repository-url>
cd apis-order-service-main
```

### 2. Install dependencies

```bash
go mod tidy
```

### 3. Run the service

```bash
go run cmd/main.go
```

The HTTP server starts on the port configured inside `main.go`.

---

## Design Principles

* Clean Architecture
* Repository pattern
* Layered structure
* Interface-based abstraction
* Minimal external dependencies

---

## What This Project Demonstrates

* REST API development in Go
* Clean Architecture implementation
* Order management service design
* Proper separation of business logic and infrastructure
* Scalable backend service structure
