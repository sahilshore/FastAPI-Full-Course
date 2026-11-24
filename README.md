# FastAPI for Machine Learning — Complete Study Guide

[![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-ASGI-009688?logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![Pydantic](https://img.shields.io/badge/Pydantic-validation-E92063)](https://docs.pydantic.dev/)
[![Uvicorn](https://img.shields.io/badge/Uvicorn-server-499848)](https://www.uvicorn.org/)
[![Pytest](https://img.shields.io/badge/Pytest-testing-0A9EDC?logo=pytest&logoColor=white)](https://pytest.org/)

This repository is a progressive, example-driven course for building HTTP APIs with Python and FastAPI, then connecting those APIs to relational databases, machine-learning models, authentication, tests, caches, profilers, load generators, and monitoring systems.

The guide below is designed to work in two ways:

- Read it from top to bottom as a beginner-to-advanced curriculum.
- Use the tables, diagrams, and cheat sheets as a quick reference while opening the linked examples.

The code is intentionally educational. It contains small, focused demos rather than one unified production application, so each example should be run from its own directory and its security, dependency versions, and deployment settings should be reviewed before reuse.

## Contents

- [Course at a glance](#course-at-a-glance)
- [Prerequisites](#prerequisites)
- [Technology stack](#technology-stack)
- [Learning path](#learning-path)
- [Repository map](#repository-map)
- [Setup and installation](#setup-and-installation)
- [Running the examples](#running-the-examples)
- [The API mental model](#the-api-mental-model)
- [Module 1 — Introduction to APIs](#module-1--introduction-to-apis)
- [Module 2 — Introduction to FastAPI](#module-2--introduction-to-fastapi)
- [Module 3 — Building APIs](#module-3--building-apis)
- [Module 4 — Database Integration](#module-4--database-integration)
- [Module 5 — Machine Learning Integration](#module-5--machine-learning-integration)
- [Module 6 — Advanced FastAPI Concepts](#module-6--advanced-fastapi-concepts)
- [Module 7 — Testing and Debugging](#module-7--testing-and-debugging)
- [Module 8 — Performance Optimization and Monitoring](#module-8--performance-optimization-and-monitoring)
- [Quick reference](#quick-reference)
- [Troubleshooting](#troubleshooting)
- [Suggested study workflow](#suggested-study-workflow)

## Course at a glance

The course moves through the same layers that a real API usually grows through:

1. Understand HTTP, REST, requests, responses, authentication, and authorization.
2. Create a FastAPI application and understand the ASGI stack.
3. Add routes, path and query parameters, Pydantic schemas, CRUD operations, validation, and errors.
4. Replace in-memory state with a SQLAlchemy-backed SQLite database.
5. Load serialized models and expose single-record and batch prediction endpoints.
6. Add middleware, dependency injection, API keys, password hashing, OAuth2-style bearer tokens, and JWTs.
7. Test pure logic, API endpoints, integrations, and model-backed routes; then debug failures with logs and handlers.
8. Improve response time and operability with Redis caching, profiling, load testing, Prometheus, Grafana, and Docker Compose.

By the end, a learner should be able to explain the complete path of a request:

~~~text
Client
  -> HTTP method + URL + headers + body
  -> Uvicorn / ASGI server
  -> FastAPI routing and dependency resolution
  -> Pydantic validation
  -> application logic
  -> database, model, cache, or external service
  -> serialized response + status code
~~~

## Prerequisites

| Prerequisite | What you should already know |
| --- | --- |
| Python | Functions, classes, imports, virtual environments, exceptions, and type hints |
| HTTP | URLs, methods, headers, JSON, status codes, and the request/response cycle |
| Command line | Changing directories, installing packages, and running Python commands |
| JSON | Objects, arrays, strings, numbers, booleans, and null |
| SQL basics | Tables, rows, columns, primary keys, and CRUD are helpful for Module 4 |
| Machine learning basics | Features, targets, training, inference, and serialization are helpful for Module 5 |
| Docker basics | Helpful, but optional until the Redis and monitoring examples |

If you are new to Python APIs, complete Modules 1–3 before starting the database or machine-learning examples. If you already build Python services, use Modules 4–8 as a focused reference for integration and operations.

## Technology stack

| Layer | Tools used in the repository | Why it appears |
| --- | --- | --- |
| Language | Python 3.10+ recommended | Type hints, async functions, data processing, and service code |
| API framework | FastAPI | Routing, dependency injection, validation, OpenAPI, and interactive docs |
| ASGI stack | Uvicorn and Starlette | Serving the application and handling the web layer |
| Validation | Pydantic and Pydantic Settings | Request/response schemas and environment-backed configuration |
| Persistence | SQLAlchemy ORM and SQLite | Relational models, sessions, and database CRUD |
| ML inference | NumPy, pandas, scikit-learn, joblib, TensorFlow/Keras | Train, serialize, load, and serve models |
| Security | OAuth2 helpers, Authlib, Passlib, bcrypt, API keys | Form login, bearer tokens, JWT signing, and password hashing |
| Testing | pytest, FastAPI TestClient, unittest.mock | Unit, integration, endpoint, and model-mocking tests |
| Caching and I/O | Redis, redis-py, httpx | Cache database results, external responses, and predictions |
| Performance | time, cProfile, line-profiler, Locust | Timing, call profiling, line profiling, and load generation |
| Observability | Prometheus instrumentator and Grafana | Request metrics, time series, dashboards, and alerts |
| Packaging/deployment | Docker and Docker Compose | Reproducible service images and multi-container monitoring demos |

There is no single root requirements.txt in this checkout. The commands below install a practical shared environment; individual modules can be installed more narrowly when desired.

## Learning path

| Module | Focus | Start here |
| --- | --- | --- |
| 1 | APIs, REST, HTTP, lifecycle, authentication, and authorization | [Module 1 notes](./1.%20Introduction%20to%20APIs/Module%201%20notes.pdf) |
| 2 | FastAPI, Starlette, Pydantic, Uvicorn, type hints, async support, and automatic docs | [Module 2 notes](./2.%20%20Introduction%20to%20FastAPI/Module%202%20notes.pdf) |
| 3 | Routes, CRUD, schemas, validation, errors, and synchronous versus asynchronous code | [Module 3 notes](./3.%20Building%20APIs/Module%203%20notes.pdf) |
| 4 | SQLAlchemy, SQLite, sessions, ORM models, schemas, and database CRUD | [Module 4 notes](./4.%20Database%20Integration/Module%204%20notes.pdf) |
| 5 | Model serialization, schemas for inference, single predictions, and batch predictions | [Module 5 notes](./5.%20Machine%20Learning%20Integration/Module%205%20notes.pdf) |
| 6 | Middleware, dependency injection, API keys, OAuth2-style flows, JWTs, and security practices | [Module 6 notes](./6.%20Advanced%20FastAPI%20Concepts/Module%206%20notes.pdf) |
| 7 | Unit, integration, endpoint, and model-mocking tests plus debugging | [Module 7 notes](./7.%20Testing%20%26%20Debugging/Module%207%20notes.pdf) |
| 8 | Redis caching, profiling, benchmarking, Locust, Prometheus, Grafana, and Docker | [Module 8 notes](./8.%20Performance%20Optimization%20and%20Monitoring/Module%208%20notes.pdf) |

## Repository map

The folders are numbered in learning order. Generated caches such as __pycache__ and .pytest_cache are intentionally omitted from this map.

~~~text
.
├── README.md
├── .gitignore
├── 1. Introduction to APIs/
│   └── Module 1 notes.pdf
├── 2.  Introduction to FastAPI/
│   ├── main.py
│   ├── practice.py
│   └── Module 2 notes.pdf
├── 3. Building APIs/
│   ├── basic-app.py
│   ├── main.py
│   ├── models.py
│   ├── models_val.py
│   ├── pydantic-demo.py
│   ├── sync-demo.py
│   ├── async-demo.py
│   ├── async_main.py
│   └── Module 3 notes.pdf
├── 4. Database Integration/
│   ├── Module 4 notes.pdf
│   └── crud-app/
│       ├── database.py
│       ├── models.py
│       ├── schemas.py
│       ├── crud.py
│       ├── main.py
│       ├── sqlite-demo.py
│       └── test.db
├── 5. Machine Learning Integration/
│   ├── Module 5 notes.pdf
│   ├── housing.csv
│   ├── ml-model/
│   │   ├── housing.csv
│   │   ├── train.py
│   │   ├── schemas.py
│   │   ├── predict.py
│   │   ├── main.py
│   │   └── model.joblib
│   ├── pickle_joblib_serialization.ipynb
│   ├── keras_serialization.ipynb
│   ├── model.pkl
│   ├── model.joblib
│   └── keras_model.keras
├── 6. Advanced FastAPI Concepts/
│   ├── Module 6 notes.pdf
│   ├── middleware/
│   │   ├── cors-middleware.py
│   │   ├── gzip-middleware.py
│   │   ├── https-middleware.py
│   │   └── custom-middleware.py
│   ├── dependency-injection/
│   │   ├── database-connection.py
│   │   ├── config_management.py
│   │   └── user_auth.py
│   ├── api-keys/
│   │   ├── headers.py
│   │   └── env-apikeys.py
│   └── jwt-authentication/
│       ├── auth.py
│       ├── models.py
│       ├── utils.py
│       └── main.py
├── 7. Testing & Debugging/
│   ├── Module 7 notes.pdf
│   ├── unit-testing/
│   │   ├── app/logic.py
│   │   └── tests/test_logic.py
│   ├── integration-testing/
│   │   ├── app/main.py
│   │   ├── app/logic.py
│   │   └── tests/test_main.py
│   ├── e2e-testing/
│   │   ├── app/main.py
│   │   └── tests/test_main.py
│   ├── mock-ml/
│   │   ├── main.py
│   │   ├── model.py
│   │   ├── test_main.py
│   │   ├── training.ipynb
│   │   ├── Iris.csv
│   │   └── model.joblib
│   └── debugging-techniques/
│       ├── logging-demo.py
│       └── exc-handling.py
└── 8. Performance Optimization and Monitoring/
    ├── Module 8 notes.pdf
    ├── redis-setup.py
    ├── prometheus_setup.py
    ├── caching/
    │   ├── db-caching/main.py
    │   ├── external-api-caching/main.py
    │   └── ml-caching/main.py
    ├── profiling/
    │   ├── time-demo.py
    │   ├── cprofile-demo.py
    │   ├── line-profiler-demo/app.py
    │   ├── line-profiler-demo/profiling_test.py
    │   └── profiles/
    ├── locust-demo/
    │   ├── main.py
    │   └── locustfile.py
    ├── demo1/
    │   ├── Dockerfile
    │   ├── docker-compose.yml
    │   ├── app/main.py
    │   └── prometheus/prometheus.yml
    └── demo2/
        ├── docker-compose.yml
        ├── requirements.txt
        ├── app/Dockerfile
        ├── app/main.py
        └── prometheus/prometheus.yml
~~~

## Setup and installation

### 1. Clone the repository

Replace <repository-url> with the URL of your checkout:

~~~bash
git clone <repository-url> fastapi-course
cd fastapi-course
~~~

### 2. Create and activate a virtual environment

Windows PowerShell:

~~~powershell
py -3.10 -m venv .venv
.\.venv\Scripts\Activate.ps1
~~~

If PowerShell blocks activation for the current user, use the documented Python/PowerShell execution-policy guidance or activate the environment through your IDE. On macOS/Linux:

~~~bash
python3 -m venv .venv
source .venv/bin/activate
~~~

### 3. Install the shared learning dependencies

~~~bash
python -m pip install --upgrade pip
python -m pip install fastapi "uvicorn[standard]" pydantic pydantic-settings
python -m pip install sqlalchemy email-validator python-multipart
python -m pip install numpy pandas scikit-learn joblib httpx redis
python -m pip install authlib "passlib[bcrypt]" pytest
python -m pip install prometheus-fastapi-instrumentator locust line-profiler snakeviz
~~~

The Keras notebook is optional and requires TensorFlow:

~~~bash
python -m pip install tensorflow
~~~

The database example uses the Pydantic 1-style orm_mode configuration, while several newer examples call Pydantic 2's model_dump(). If you see a version error, either use a separate virtual environment per module or update the database response schema to Pydantic 2 style:

~~~python
from pydantic import BaseModel, ConfigDict


class EmployeeOut(BaseModel):
    id: int
    name: str
    email: str

    model_config = ConfigDict(from_attributes=True)
~~~

The repository's Docker monitoring example has its own [requirements.txt](./8.%20Performance%20Optimization%20and%20Monitoring/demo2/requirements.txt). Installing only the packages needed by the module you are studying is also a good practice.

### 4. Start external services when needed

The Redis examples expect Redis on localhost:6379:

~~~bash
docker run --detach --name fastapi-course-redis --publish 6379:6379 redis
~~~

Stop it when finished:

~~~bash
docker stop fastapi-course-redis
docker rm fastapi-course-redis
~~~

Docker Compose is only needed for the monitoring demos in Module 8.

## Running the examples

### FastAPI development server

Run Uvicorn from the directory containing the target main.py. Several examples load local model files or import sibling modules with plain imports, so the working directory matters.

~~~bash
uvicorn main:app --reload
~~~

The application is normally available at:

- API root: http://127.0.0.1:8000/
- Swagger UI: http://127.0.0.1:8000/docs
- ReDoc: http://127.0.0.1:8000/redoc

Useful entry points:

| Example | Command |
| --- | --- |
| FastAPI greeting | cd "2.  Introduction to FastAPI" then uvicorn main:app --reload |
| In-memory employee CRUD | cd "3. Building APIs" then uvicorn main:app --reload |
| SQLAlchemy employee CRUD | cd "4. Database Integration\crud-app" then uvicorn main:app --reload |
| ML prediction API | cd "5. Machine Learning Integration\ml-model" then uvicorn main:app --reload |
| JWT demo | cd "6. Advanced FastAPI Concepts\jwt-authentication" then uvicorn main:app --reload |
| API-key demo | cd "6. Advanced FastAPI Concepts\api-keys" then uvicorn headers:app --reload |
| Timing demo | cd "8. Performance Optimization and Monitoring\profiling" then uvicorn time-demo:app --reload |
| Prometheus demo | cd "8. Performance Optimization and Monitoring" then uvicorn prometheus_setup:app --reload |

On PowerShell, use Set-Location if a path is easier to read as a command:

~~~powershell
Set-Location "5. Machine Learning Integration\ml-model"
uvicorn main:app --reload
~~~

### Calling an endpoint with curl

~~~bash
curl http://127.0.0.1:8000/

curl -X POST http://127.0.0.1:8000/employees \
  -H "Content-Type: application/json" \
  -d '{"name":"Ada Lovelace","email":"ada@example.com"}'
~~~

The interactive Swagger UI is often the fastest way to discover the exact request body for each example.

## The API mental model

Every module builds on the same request path:

~~~mermaid
flowchart LR
    Client[Client or browser] --> HTTP[HTTP request]
    HTTP --> Server[Uvicorn / ASGI]
    Server --> Router[FastAPI routing]
    Router --> Dependencies[Dependencies and security]
    Dependencies --> Validation[Pydantic validation]
    Validation --> Handler[Path operation function]
    Handler --> Data[(Database)]
    Handler --> Model[ML model]
    Handler --> External[External API]
    Data --> Response[Serialized response]
    Model --> Response
    External --> Response
    Response --> Client
~~~

The important design boundary is the handler. It should coordinate validated input and reusable services, while database access, model inference, authentication, caching, and monitoring remain explicit concerns that can be tested independently.

# Module 1 — Introduction to APIs

Source material: [Module 1 notes](./1.%20Introduction%20to%20APIs/Module%201%20notes.pdf).

### What an API is

An Application Programming Interface is a contract that lets one piece of software use data or behavior provided by another piece of software. A web API exposes that contract through HTTP or HTTPS. The client does not need to know how the server stores data or implements its business rules; it only needs to know the supported requests and response shapes.

The notes distinguish several API categories:

| Type | Meaning | Example |
| --- | --- | --- |
| Web API | Accessible over HTTP/HTTPS | A weather service returning JSON |
| Library API | Functions and classes exposed by a package | NumPy or TensorFlow |
| Remote API | A service reached over another network | A cloud provider API |
| Database API | Operations for reading and writing stored data | A SQL connector |
| Hardware API | An abstraction over physical devices | A GPU or sensor API |
| GUI API | Programmatic access to user-interface components | Tkinter |

### Protocol and architectural choices

- REST is an HTTP-oriented architectural style built around resources, URLs, stateless requests, and standard methods such as GET, POST, PUT, and DELETE.
- SOAP uses XML messages and a more formal protocol with enterprise-oriented extensions.
- GraphQL lets a client request a chosen shape of data through a query endpoint.
- gRPC uses Protocol Buffers and HTTP/2 for compact, high-performance remote procedure calls.
- WebSockets maintain a full-duplex connection for continuously exchanged data such as chat or live feeds.

FastAPI examples in this repository use REST-style HTTP endpoints and JSON bodies.

### Request and response anatomy

| Part | Client-to-server meaning | Server-to-client meaning |
| --- | --- | --- |
| Method | The intended operation, such as GET or POST | Usually reflected in the route contract |
| URL | The resource and its path/query parameters | Identifies the endpoint that handled the request |
| Headers | Metadata such as content type, credentials, and cache directives | Metadata such as content type and cache policy |
| Body | JSON or form data sent to the server | JSON, text, a file, or a stream returned to the client |
| Status code | Not sent by the client | Describes success, redirect, client error, or server error |

### Request lifecycle

~~~mermaid
sequenceDiagram
    participant C as Client
    participant A as API endpoint
    participant S as Service logic
    participant D as Database or model
    C->>A: HTTP request
    A->>A: Parse path, query, headers, body
    A->>S: Validate and authorize
    S->>D: Read or compute
    D-->>S: Result
    S-->>A: Response data
    A-->>C: Status code + headers + body
~~~

### API lifecycle and design habits

The course describes an API lifecycle of planning/design, development, deployment, monitoring/management, updates/versioning, and eventual retirement. Even a small learning endpoint benefits from:

- Stable, resource-oriented names.
- Consistent request and response shapes.
- Explicit validation and meaningful status codes.
- Authentication and authorization where data is protected.
- Rate limits and quotas for public or expensive operations.
- Documentation that is updated with the implementation.
- A migration path when a contract must change.

### Authentication versus authorization

Authentication answers “Who are you?” Authorization answers “What are you allowed to do?” API keys, bearer tokens, OAuth flows, and JWTs are authentication or credential mechanisms; role checks and permission policies are authorization mechanisms. The distinction becomes concrete in Module 6.

# Module 2 — Introduction to FastAPI

Source material: [Module 2 notes](./2.%20%20Introduction%20to%20FastAPI/Module%202%20notes.pdf).

### The smallest FastAPI application

The repository's [main.py](./2.%20%20Introduction%20to%20FastAPI/main.py) demonstrates the basic pattern:

~~~python
from fastapi import FastAPI

app = FastAPI()


@app.get("/")
def index():
    return {"message": "Hello, FastAPI!"}
~~~

The string main:app in uvicorn main:app --reload means:

1. Import the main Python module.
2. Find the object named app.
3. Serve it as an ASGI application.
4. Reload the process when source files change.

### FastAPI's architecture

The course presents three core pieces:

| Component | Responsibility |
| --- | --- |
| Starlette | ASGI web primitives, routing, middleware, and WebSocket support |
| Pydantic | Parse, validate, transform, and describe typed data |
| Uvicorn | Run the ASGI application and accept network traffic |

~~~mermaid
flowchart LR
    Request[HTTP request] --> Uvicorn[Uvicorn]
    Uvicorn --> Starlette[Starlette ASGI layer]
    Starlette --> FastAPI[FastAPI router]
    FastAPI --> Pydantic[Pydantic schemas]
    Pydantic --> Function[Typed Python function]
    Function --> JSON[JSON response]
~~~

FastAPI uses Python type hints as part of the API contract. A type annotation is not merely documentation: it can affect parsing, validation, generated JSON Schema, and editor support.

### Automatic documentation

After starting an application, open:

- /docs for Swagger UI, where requests can be explored interactively.
- /redoc for ReDoc, a documentation-focused view.
- /openapi.json for the generated OpenAPI document.

The generated schema is driven by the registered routes, type hints, Pydantic models, and response models.

### Synchronous and asynchronous handlers

The course compares a blocking function with an async function that awaits non-blocking work:

~~~python
import asyncio
from fastapi import FastAPI

app = FastAPI()


@app.get("/wait")
async def wait():
    await asyncio.sleep(3)
    return {"message": "Finished waiting!"}
~~~

Use async def when the work uses an async-compatible I/O library, such as an async HTTP client or async database driver. Use a normal def for CPU-bound work or blocking libraries unless that work is deliberately offloaded. An ML prediction call, image transformation, or synchronous database driver can block an event loop even when the route is declared async.

The standalone [async-demo.py](./3.%20Building%20APIs/async-demo.py) uses asyncio.gather() to run three sleeps concurrently, while [sync-demo.py](./3.%20Building%20APIs/sync-demo.py) runs three blocking sleeps one after another.

### Framework comparison

| Concern | FastAPI | Flask | Django | Falcon |
| --- | --- | --- | --- | --- |
| Async support | Native ASGI and async/await | Usually extension-based | Available in modern versions | Strong ASGI support |
| Validation/docs | Pydantic and OpenAPI built in | Usually added separately | Often supplied through Django REST Framework | Usually added separately |
| ORM | Choose SQLAlchemy or another tool | Choose a separate tool | Django ORM available | Choose a separate tool |
| Best fit in these notes | Typed APIs, async I/O, and ML services | Small services and prototypes | Full web applications and admin workflows | Lean, high-performance APIs |

# Module 3 — Building APIs

Source material: [Module 3 notes](./3.%20Building%20APIs/Module%203%20notes.pdf).

### Routes and path operations

A route connects an HTTP method and URL path to a Python function:

~~~python
@app.get("/employees/{emp_id}")
def get_employee(emp_id: int):
    ...
~~~

FastAPI reads emp_id: int from the URL, converts it to an integer, and returns a validation error if conversion fails. A path parameter identifies one resource; a query parameter modifies a collection or filters a result:

~~~python
from typing import Optional


@app.get("/employees")
def list_employees(
    department: Optional[str] = None,
    limit: int = 20,
):
    ...
~~~

The route above accepts requests such as /employees?department=platform&limit=10.

### Pydantic request and response models

The basic [models.py](./3.%20Building%20APIs/models.py) model declares typed fields:

~~~python
from pydantic import BaseModel


class Employee(BaseModel):
    id: int
    name: str
    department: str
    age: int
~~~

The validation-focused [models_val.py](./3.%20Building%20APIs/models_val.py) adds constraints:

~~~python
from pydantic import BaseModel, Field, StrictInt
from typing import Optional


class Employee(BaseModel):
    id: int = Field(..., gt=0, title="Employee ID")
    name: str = Field(..., min_length=3, max_length=30)
    department: str = Field(..., min_length=3, max_length=30)
    age: Optional[StrictInt] = Field(default=None, ge=21)
~~~

Important ideas:

- Field(...) marks a required value and can add bounds, length constraints, defaults, titles, and schema metadata.
- StrictInt prevents a value that merely looks numeric from being silently coerced in cases where strict input matters.
- Optional[...] = None makes a field optional and gives it a default.
- A request-body model validates incoming JSON before the handler runs.
- response_model=... validates and serializes the outgoing shape.

### In-memory CRUD example

The [main.py](./3.%20Building%20APIs/main.py) example keeps employees in a process-local list:

~~~python
employees_db: list[Employee] = []


@app.get("/employees", response_model=list[Employee])
def get_employees():
    return employees_db


@app.post("/add_employee", response_model=Employee)
def add_employee(new_emp: Employee):
    if any(employee.id == new_emp.id for employee in employees_db):
        raise HTTPException(status_code=400, detail="Employee already exists")
    employees_db.append(new_emp)
    return new_emp
~~~

The complete example also implements:

| Operation | Route | Behavior |
| --- | --- | --- |
| List | GET /employees | Return all in-memory employees |
| Read one | GET /employees/{emp_id} | Return one employee or 404 |
| Create | POST /add_employee | Add an employee or return 400 for a duplicate ID |
| Update | PUT /update_employee/{emp_id} | Replace the matching entry or return 404 |
| Delete | DELETE /delete_employee/{emp_id} | Remove the matching entry or return 404 |

This is a useful first CRUD exercise, but the list is lost whenever the process restarts and is not safe for multi-worker production use. Module 4 replaces it with persistent storage.

### Errors and HTTPException

Raise HTTPException when the request is understood but cannot be completed:

~~~python
from fastapi import HTTPException


raise HTTPException(
    status_code=404,
    detail="Employee Not Found",
)
~~~

Use validation for malformed input and explicit exceptions for domain conditions such as a missing record or duplicate identifier. Keep error bodies stable enough for clients to handle them.

### Response serialization

FastAPI can return dictionaries, Pydantic model instances, or specialized response classes. A response model provides a public contract and prevents accidental fields from leaking out of the handler's internal object.

# Module 4 — Database Integration

Source material: [Module 4 notes](./4.%20Database%20Integration/Module%204%20notes.pdf). The runnable example is in the [crud-app](./4.%20Database%20Integration/crud-app/) directory.

### Why persistence changes the design

An in-memory list is enough to learn routing, but real services need state that survives restarts, can be queried efficiently, and can enforce constraints. The module uses SQLite for storage and SQLAlchemy as the Python database toolkit and ORM.

SQLAlchemy has two related layers:

- SQLAlchemy Core builds SQL expressions directly.
- SQLAlchemy ORM maps Python classes to database tables and lets application code work with model objects.

### The example's layers

| File | Responsibility |
| --- | --- |
| [database.py](./4.%20Database%20Integration/crud-app/database.py) | SQLite URL, engine, session factory, and declarative base |
| [models.py](./4.%20Database%20Integration/crud-app/models.py) | SQLAlchemy Employee table with integer ID, name, and unique indexed email |
| [schemas.py](./4.%20Database%20Integration/crud-app/schemas.py) | Pydantic input and output contracts; EmailStr validates email input |
| [crud.py](./4.%20Database%20Integration/crud-app/crud.py) | Query, create, update, and delete functions |
| [main.py](./4.%20Database%20Integration/crud-app/main.py) | FastAPI routes, database dependency, table creation, and HTTP errors |
| [sqlite-demo.py](./4.%20Database%20Integration/crud-app/sqlite-demo.py) | Direct SQLite inspection of table names and rows |

The architecture is intentionally layered:

~~~mermaid
flowchart LR
    Route[FastAPI route] --> Dependency[get_db]
    Dependency --> Session[SQLAlchemy Session]
    Route --> CRUD[crud.py]
    CRUD --> ORM[models.py]
    ORM --> SQLite[(test.db)]
    Route --> Schema[schemas.py]
    Schema --> Response[Validated response]
~~~

### Session lifecycle with yield

The application creates a session per request:

~~~python
def get_db():
    db = SessionLocal()
    try:
        yield db
    finally:
        db.close()
~~~

Depends(get_db) injects the yielded session into a route. The finally block is important: it closes the session even when the route raises an exception.

The database module configures:

~~~python
SQLALCHEMY_DATABASE_URL = "sqlite:///./test.db"

engine = create_engine(
    SQLALCHEMY_DATABASE_URL,
    connect_args={"check_same_thread": False},
)

SessionLocal = sessionmaker(
    bind=engine,
    autoflush=False,
    autocommit=False,
)
~~~

check_same_thread=False is a SQLite-specific setting used by this learning example; production database configuration should be chosen for the actual deployment and concurrency model.

### ORM model and API schemas

The ORM model describes the database table:

~~~python
class Employee(Base):
    __tablename__ = "employees"

    id = Column(Integer, primary_key=True, index=True)
    name = Column(String, index=True)
    email = Column(String, unique=True, index=True)
~~~

The Pydantic layer separates client input from output:

~~~python
class EmployeeBase(BaseModel):
    name: str
    email: EmailStr


class EmployeeCreate(EmployeeBase):
    pass


class EmployeeOut(EmployeeBase):
    id: int

    class Config:
        orm_mode = True
~~~

That separation lets the database have an auto-generated ID while create requests do not need to provide one. The response schema can read ORM attributes and serialize them to JSON.

### CRUD route contract

The database-backed API exposes:

| Method | Path | Purpose |
| --- | --- | --- |
| POST | /employees | Create an employee |
| GET | /employees | Return all employees |
| GET | /employees/{emp_id} | Return one employee |
| PUT | /employees/{emp_id} | Replace the name and email |
| DELETE | /employees/{emp_id} | Delete an employee |

The route layer checks for None after a CRUD lookup and translates it into a 404. Database code stays in crud.py, so the same operations can be reused from another entry point or tested independently.

### Run and inspect the database example

~~~powershell
Set-Location "4. Database Integration\crud-app"
uvicorn main:app --reload
~~~

Then use Swagger UI to create and query employees. To inspect the SQLite file from the same directory:

~~~bash
python sqlite-demo.py
~~~

### Version note

This example uses the Pydantic 1-style Config.orm_mode. With Pydantic 2, use ConfigDict(from_attributes=True) as shown in the setup section. The ML examples use model_dump(), which is the Pydantic 2 spelling of model serialization.

# Module 5 — Machine Learning Integration

Source material: [Module 5 notes](./5.%20Machine%20Learning%20Integration/Module%205%20notes.pdf).

This module separates offline training from online inference:

~~~mermaid
flowchart LR
    CSV[Training CSV] --> Train[Training script or notebook]
    Train --> Artifact[Serialized model artifact]
    Artifact --> Load[FastAPI process loads model]
    Request[Validated JSON] --> Predict[Inference function]
    Load --> Predict
    Predict --> Result[Prediction response]
~~~

### Serialization workflows

The [pickle/joblib notebook](./5.%20Machine%20Learning%20Integration/pickle_joblib_serialization.ipynb) reads the housing data, removes missing rows, splits features from median_house_value, trains LinearRegression, evaluates with r2_score, and saves/loads the model with both Pickle and joblib.

The [Keras notebook](./5.%20Machine%20Learning%20Integration/keras_serialization.ipynb) loads MNIST, scales pixel values by 255, one-hot encodes labels, trains a small Sequential network with Flatten and dense layers, saves keras_model.keras, reloads it, and evaluates both model objects.

Serialization is useful because training can happen offline while inference processes load a known artifact quickly. Treat serialized model files as trusted inputs: Pickle and joblib are not safe formats for arbitrary untrusted files.

### Training script

The [train.py](./5.%20Machine%20Learning%20Integration/ml-model/train.py) example:

1. Reads housing.csv.
2. Drops the final non-numeric ocean_proximity column and rows with missing values.
3. Uses median_house_value as the target.
4. Trains sklearn.linear_model.LinearRegression.
5. Writes model.joblib.

Run it from the ml-model directory if you want to regenerate the artifact:

~~~powershell
Set-Location "5. Machine Learning Integration\ml-model"
python train.py
~~~

### Input and output schemas

The [schemas.py](./5.%20Machine%20Learning%20Integration/ml-model/schemas.py) contract mirrors the eight numeric features used by predict.py:

~~~python
class InputSchema(BaseModel):
    longitude: float
    latitude: float
    housing_median_age: int = Field(..., gt=0)
    total_rooms: StrictInt = Field(..., gt=0)
    total_bedrooms: StrictInt = Field(..., gt=0)
    population: int = Field(..., gt=0)
    households: StrictInt = Field(..., gt=0)
    median_income: float = Field(..., gt=0)


class OutputSchema(BaseModel):
    predicted_price: float
~~~

This is more than convenience. It keeps invalid or incomplete input away from the model and gives clients a machine-readable API contract.

### Prediction endpoints

The [main.py](./5.%20Machine%20Learning%20Integration/ml-model/main.py) application exposes:

| Method | Path | Body | Response |
| --- | --- | --- | --- |
| GET | / | None | Welcome message |
| POST | /prediction | One InputSchema object | One predicted_price |
| POST | /batch_prediction | A JSON list of input objects | A JSON list of predictions |

Single prediction example:

~~~json
{
  "longitude": -122.23,
  "latitude": 37.88,
  "housing_median_age": 41,
  "total_rooms": 880,
  "total_bedrooms": 129,
  "population": 322,
  "households": 126,
  "median_income": 8.3252
}
~~~

The response is shaped as:

~~~json
{
  "predicted_price": 452600.0
}
~~~

The exact value depends on the serialized model artifact. The batch endpoint sends a NumPy matrix to model.predict() once, then returns one validated response object per row. Vectorization avoids repeatedly calling the model for each record and is the key performance lesson in this module.

Start it from the directory containing model.joblib:

~~~powershell
Set-Location "5. Machine Learning Integration\ml-model"
uvicorn main:app --reload
~~~

### ML-serving checklist

- Validate every feature and its units.
- Keep feature order stable between training and inference.
- Version the model and preprocessing logic together.
- Load the artifact once per process rather than once per request.
- Return a stable response schema.
- Add tests for malformed input, one prediction, batches, and model-load failures.
- Never load arbitrary user-uploaded Pickle/joblib files.

# Module 6 — Advanced FastAPI Concepts

Source material: [Module 6 notes](./6.%20Advanced%20FastAPI%20Concepts/Module%206%20notes.pdf).

## Middleware

Middleware wraps the request/response path. It can inspect or modify a request before routing, and inspect or modify the response after the route returns. Middleware is useful for cross-cutting concerns that should apply to many routes:

- CORS headers.
- GZip compression.
- HTTPS redirects.
- Request timing and access logging.
- Global response or error processing.

The repository demonstrates:

- [CORS middleware](./6.%20Advanced%20FastAPI%20Concepts/middleware/cors-middleware.py) with explicit origins, credentials, methods, and headers.
- [GZip middleware](./6.%20Advanced%20FastAPI%20Concepts/middleware/gzip-middleware.py) for responses larger than 1,000 bytes.
- [HTTPS redirect middleware](./6.%20Advanced%20FastAPI%20Concepts/middleware/https-middleware.py).
- [Custom timing middleware](./6.%20Advanced%20FastAPI%20Concepts/middleware/custom-middleware.py) implemented with BaseHTTPMiddleware.

Custom middleware follows this shape:

~~~python
class TimerMiddleware(BaseHTTPMiddleware):
    async def dispatch(self, request: Request, call_next):
        start_time = time.time()
        response = await call_next(request)
        duration = time.time() - start_time
        print(f"Request: {request.url.path} processed in {duration:.5f} seconds")
        return response


app.add_middleware(TimerMiddleware)
~~~

Middleware is ordered. Keep that ordering intentional when one layer depends on headers or state added by another.

## Dependency injection

FastAPI's Depends() lets a route declare what it needs while the framework constructs or retrieves it:

~~~python
@app.get("/profile")
def get_profile(user=Depends(get_current_user)):
    return {"username": user["name"]}
~~~

The repository uses dependencies for:

| Dependency example | What it teaches |
| --- | --- |
| [database-connection.py](./6.%20Advanced%20FastAPI%20Concepts/dependency-injection/database-connection.py) | Yield a resource before the request and clean it up afterward |
| [config_management.py](./6.%20Advanced%20FastAPI%20Concepts/dependency-injection/config_management.py) | Centralize settings and inject them into a handler |
| [user_auth.py](./6.%20Advanced%20FastAPI%20Concepts/dependency-injection/user_auth.py) | Extract a bearer token and resolve the current user |

The same pattern scales to database sessions, settings, permissions, service objects, and test overrides.

The database-connection file uses a dictionary as a mock connection and then calls close() during cleanup. That finalizer is intentionally illustrative rather than a production database implementation; use an object with a real close method in a real dependency.

## API keys

The [headers.py](./6.%20Advanced%20FastAPI%20Concepts/api-keys/headers.py) example compares an incoming api-key header against a demo value:

~~~python
def get_api_key(api_key: str = Header(...)):
    if api_key != API_KEY:
        raise HTTPException(status_code=403, detail="Unauthorized")
    return api_key


@app.get("/get-data")
def get_data(api_key: str = Depends(get_api_key)):
    return {"output": "Access Granted!"}
~~~

Because FastAPI converts the Python api_key parameter to the HTTP header spelling api-key, call it as:

~~~bash
curl -H "api-key: my-secret-key" http://127.0.0.1:8000/get-data
~~~

The [env-apikeys.py](./6.%20Advanced%20FastAPI%20Concepts/api-keys/env-apikeys.py) example loads api_key from a .env file with Pydantic Settings:

~~~text
api_key=my-secret-key
~~~

Keep real keys out of source control, rotate them, use HTTPS, and prefer a secrets manager for deployed systems.

## OAuth2-style form login and JWT

The simpler [user_auth.py](./6.%20Advanced%20FastAPI%20Concepts/dependency-injection/user_auth.py) example demonstrates the dependency chain:

~~~mermaid
flowchart LR
    Login[POST /token] --> Token[Bearer token]
    Token --> Header[Authorization: Bearer ...]
    Header --> OAuth[OAuth2PasswordBearer]
    OAuth --> Decode[decode_token / get_current_user]
    Decode --> Protected[GET /profile]
~~~

The full [JWT example](./6.%20Advanced%20FastAPI%20Concepts/jwt-authentication/) separates responsibilities:

| File | Responsibility |
| --- | --- |
| [auth.py](./6.%20Advanced%20FastAPI%20Concepts/jwt-authentication/auth.py) | Create and verify signed JWTs |
| [models.py](./6.%20Advanced%20FastAPI%20Concepts/jwt-authentication/models.py) | Public user fields and the internal hashed-password model |
| [utils.py](./6.%20Advanced%20FastAPI%20Concepts/jwt-authentication/utils.py) | Fake user lookup and bcrypt password verification |
| [main.py](./6.%20Advanced%20FastAPI%20Concepts/jwt-authentication/main.py) | Login route and protected route |

The flow is:

1. POST /token receives form fields username and password.
2. get_user() locates the user in the demo dictionary.
3. verify_password() compares the plain password with the bcrypt hash.
4. create_access_token() signs a token with a subject claim.
5. The client sends Authorization: Bearer <token> to GET /users.
6. verify_token() validates the token and returns the username.

The demo credentials embedded in the sample are johndoe and secret123. They are for local learning only.

JWTs have three conceptual parts:

| Part | Purpose |
| --- | --- |
| Header | Algorithm and token metadata |
| Payload | Claims such as subject and expiry |
| Signature | Integrity check made with the signing secret |

Security practices from the module:

- Store signing keys and API keys in environment variables or a secrets vault.
- Use HTTPS in every deployed environment.
- Hash passwords with a dedicated password-hashing library.
- Give tokens an appropriate expiry and support refresh/revocation as needed.
- Return generic authentication errors so attackers cannot enumerate users.
- Add roles or permissions when identity alone is not enough.
- Configure CORS narrowly and understand CSRF risks when browser credentials are involved.

Code-reading note: [auth.py](./6.%20Advanced%20FastAPI%20Concepts/jwt-authentication/auth.py) contains a hard-coded demo secret and passes the expiry value positionally to timedelta. In production code, keep the secret outside the source tree and use an explicit unit such as timedelta(minutes=...).

# Module 7 — Testing and Debugging

Source material: [Module 7 notes](./7.%20Testing%20%26%20Debugging/Module%207%20notes.pdf).

Testing is a confidence system: it catches logic errors, protects against regressions, makes refactoring safer, and provides a gate for continuous integration.

## Test levels

| Level | Scope | Repository example | Typical speed |
| --- | --- | --- | --- |
| Unit | One function or class with no external service | unit-testing/tests/test_logic.py | Fast |
| Integration | Multiple application components together | integration-testing/tests/test_main.py | Medium |
| Endpoint/API | HTTP request through a FastAPI app | e2e-testing/tests/test_main.py | Medium |
| Model-mocking | Endpoint contract without real inference | mock-ml/test_main.py | Fast and deterministic |

The course labels the e2e-testing directory as end-to-end testing, but the included tests use FastAPI's in-process TestClient. They are valuable API-level tests; a true deployed-system E2E suite would run against separately started services.

## Unit testing

The [unit-testing logic function](./7.%20Testing%20%26%20Debugging/unit-testing/app/logic.py) decides loan eligibility from income, age, and employment status. Its tests cover success, underage, low income, unemployment, and the exact boundary case of income 50,000 and age 21.

Run it from its project directory:

~~~powershell
Set-Location "7. Testing & Debugging\unit-testing"
pytest -q
~~~

The test naming convention matters: pytest discovers files such as test_logic.py and functions beginning with test_.

## Integration and endpoint testing

The integration app splits business logic into [logic.py](./7.%20Testing%20%26%20Debugging/integration-testing/app/logic.py) and request handling into [main.py](./7.%20Testing%20%26%20Debugging/integration-testing/app/main.py). Its test uses TestClient to POST JSON to /loan-eligibility, then asserts both the HTTP status and response body.

~~~python
from fastapi.testclient import TestClient
from app.main import app

client = TestClient(app)


def test_eligibility_pass():
    response = client.post(
        "/loan-eligibility",
        json={
            "income": 60000,
            "age": 25,
            "employment_status": "employed",
        },
    )
    assert response.status_code == 200
    assert response.json() == {"eligible": True}
~~~

Run the integration suite:

~~~powershell
Set-Location "7. Testing & Debugging\integration-testing"
pytest -q
~~~

The endpoint-level suite in [e2e-testing/tests/test_main.py](./7.%20Testing%20%26%20Debugging/e2e-testing/tests/test_main.py) follows the same pattern against a self-contained FastAPI app.

## Mocking an ML model

The [mock-ml app](./7.%20Testing%20%26%20Debugging/mock-ml/main.py) loads a serialized classifier and exposes /predict. Its test replaces model.model.predict with a mock returning [99]:

~~~python
with patch("model.model.predict") as mock_predict:
    mock_predict.return_value = [99]
    response = client.post("/predict", json=payload)
    assert response.json() == {"prediction": 99}
~~~

This test checks the endpoint contract and feature plumbing without depending on the model's mathematical accuracy, file size, training time, or runtime environment. Keep separate model-quality tests for the real artifact.

Run it from the mock-ml directory:

~~~powershell
Set-Location "7. Testing & Debugging\mock-ml"
pytest -q
~~~

## Debugging techniques

### Structured logging

The [logging demo](./7.%20Testing%20%26%20Debugging/debugging-techniques/logging-demo.py) configures Python logging with a timestamp, source line, level, and message:

~~~python
logging.basicConfig(
    level=logging.INFO,
    format="[%(asctime)s] (line %(lineno)d) - %(levelname)s - %(message)s",
)
~~~

Useful levels are DEBUG, INFO, WARNING, ERROR, and CRITICAL. Prefer logging over scattered print() calls once an application has more than one route.

### Exception handlers

The [exception demo](./7.%20Testing%20%26%20Debugging/debugging-techniques/exc-handling.py) registers a global handler that turns an unhandled exception into a JSON response:

~~~python
@app.exception_handler(Exception)
async def general_exception_handler(request: Request, exc: Exception):
    return JSONResponse(
        status_code=500,
        content={"error": str(exc)},
    )
~~~

This is useful for learning response shaping, but do not expose raw exception messages in a production API. Log the detailed exception internally and return a safe public message.

### Common errors

| Status | Meaning | First checks |
| --- | --- | --- |
| 401 | Credentials are missing or invalid | Authorization header, token expiry, or bearer format |
| 403 | The identity is known or the request is understood but access is denied | API key, role, or permission check |
| 404 | Route or resource does not exist | URL, HTTP method, and lookup result |
| 422 | Input does not match the declared schema | Required fields, types, field constraints, and JSON shape |
| 500 | Unhandled server-side failure | Traceback, configuration, dependencies, model files, and database |

The module also introduces curl for isolating server behavior from a frontend and documents uvicorn main:app --reload --debug as a development command. --reload is intended for development only; verify the available flags for the installed Uvicorn version before using --debug.

# Module 8 — Performance Optimization and Monitoring

Source material: [Module 8 notes](./8.%20Performance%20Optimization%20and%20Monitoring/Module%208%20notes.pdf).

Performance work should be evidence-driven. First measure latency, throughput, concurrency, error rate, and resource use; then optimize the bottleneck and measure again.

## Caching

Caching stores a result near the consumer so repeated requests avoid repeated work. The notes cover:

- Client-side caching with headers such as Cache-Control.
- Server-side caching with Redis, Memcached, or process-local structures.
- CDN caching for geographically distributed static content.
- Database query, external API, ML prediction, and session caching.
- Invalidation, eviction policies such as LRU/LFU/FIFO, and consistency.

Redis is used here as an in-memory key-value store. It can also provide persistence, pub/sub, streams, queues, rate limiting, sessions, and analytics.

### Redis setup

The [redis-setup.py](./8.%20Performance%20Optimization%20and%20Monitoring/redis-setup.py) script pings Redis, stores FastAPI under the key framework, reads it back, and prints the value. Start Redis before running it:

~~~powershell
Set-Location "8. Performance Optimization and Monitoring"
python redis-setup.py
~~~

### Three cache examples

| Example | File | Endpoint | Cache key and TTL |
| --- | --- | --- | --- |
| ML predictions | [ml-caching/main.py](./8.%20Performance%20Optimization%20and%20Monitoring/caching/ml-caching/main.py) | POST /predict | SHA-256 of sorted input JSON; 3,600 seconds |
| SQLite query | [db-caching/main.py](./8.%20Performance%20Optimization%20and%20Monitoring/caching/db-caching/main.py) | POST /get-user | SHA-256 of user:<id>; 3,600 seconds |
| External API | [external-api-caching/main.py](./8.%20Performance%20Optimization%20and%20Monitoring/caching/external-api-caching/main.py) | POST /get-post | SHA-256 of external_api:post_<id>; 600 seconds |

The common read-through pattern is:

~~~mermaid
flowchart TD
    Request[Request] --> Key[Build deterministic cache key]
    Key --> Lookup{Redis hit?}
    Lookup -- Yes --> Return[Deserialize and return]
    Lookup -- No --> Source[Query database, API, or model]
    Source --> Store[Serialize and store with TTL]
    Store --> Return
~~~

The ML cache sorts the serialized input fields before hashing, so the key is stable for the same logical payload. The database cache uses parameterized SQL for the user ID. The external API example calls JSONPlaceholder through httpx.AsyncClient.

These are teaching examples. Their route functions use the synchronous Redis client, including from async def handlers. In a production async service, use an async Redis client or move blocking calls off the event loop. Also design invalidation deliberately when the underlying data can change.

## Profiling

The module introduces three levels of measurement:

| Tool | Best for | Example |
| --- | --- | --- |
| time | A quick duration around a function or route | [time-demo.py](./8.%20Performance%20Optimization%20and%20Monitoring/profiling/time-demo.py) |
| cProfile | Function-call counts and cumulative time | [cprofile-demo.py](./8.%20Performance%20Optimization%20and%20Monitoring/profiling/cprofile-demo.py) |
| line_profiler | Line-by-line hotspots in isolated functions | [line-profiler-demo](./8.%20Performance%20Optimization%20and%20Monitoring/profiling/line-profiler-demo/) |

The timing demo logs each route duration and provides /slow and /fast endpoints. The cProfile middleware writes one .prof file per request under profiles/; inspect a file with:

~~~bash
snakeviz profiles/<profile-name>.prof
~~~

The line-profiler example decorates process_data() and runs it from a separate script:

~~~bash
kernprof -l -v profiling_test.py
~~~

@profile is supplied by kernprof, not by normal Python execution. The module notes also point out that line-profiler should measure isolated functions rather than an ASGI server process directly.

One deliberate warning in the demos: time.sleep() inside an async def route blocks the event loop. It is useful for showing a slow endpoint, not a recommended async implementation.

## Benchmarking and load testing

Benchmarking asks how an API behaves under specified load. Track:

- Latency, including tail latency.
- Throughput, such as requests per second.
- Concurrent requests and degradation under load.
- 4xx/5xx error rate.
- CPU, memory, and I/O usage.

The notes compare wrk, ApacheBench, Locust, and k6. The repository includes a Python-based [Locust demo](./8.%20Performance%20Optimization%20and%20Monitoring/locust-demo/):

~~~powershell
Set-Location "8. Performance Optimization and Monitoring\locust-demo"
uvicorn main:app --reload
~~~

In another terminal:

~~~bash
locust -f locustfile.py
~~~

Open http://localhost:8089/, set the host to http://127.0.0.1:8000, and choose a user count and spawn rate. The included locustfile.py sends POST requests to /predict with feature1 and feature2, and GET requests to /.

Good benchmark habits:

- Warm up the service.
- Test endpoints separately.
- Increase concurrency gradually.
- Use production-like data.
- Compare local, staging, and cloud environments.
- Correlate load results with metrics and resource usage.

## Prometheus and Grafana

The [prometheus_setup.py](./8.%20Performance%20Optimization%20and%20Monitoring/prometheus_setup.py) example instruments a FastAPI app and exposes /metrics:

~~~python
Instrumentator().instrument(app).expose(app)
~~~

The instrumentator records request counts, durations, methods, paths, and statuses in a Prometheus-compatible format. Prometheus pulls those metrics on a schedule defined in prometheus.yml; Grafana queries Prometheus and turns the time series into panels and alerts.

The monitoring topology is:

~~~mermaid
flowchart LR
    Client[API clients] --> API[FastAPI container :8000]
    API --> Metrics[/metrics]
    Prom[Prometheus :9090] -->|scrapes| Metrics
    Graf[Grafana :3000] -->|PromQL queries| Prom
~~~

### Docker Compose demo 1: FastAPI and Prometheus

~~~powershell
Set-Location "8. Performance Optimization and Monitoring\demo1"
docker compose up --build
~~~

Open:

- FastAPI: http://localhost:8000/
- Metrics: http://localhost:8000/metrics
- Prometheus: http://localhost:9090/

The [demo1 Prometheus configuration](./8.%20Performance%20Optimization%20and%20Monitoring/demo1/prometheus/prometheus.yml) scrapes the service name fastapi every 15 seconds.

### Docker Compose demo 2: FastAPI, Prometheus, and Grafana

~~~powershell
Set-Location "8. Performance Optimization and Monitoring\demo2"
docker compose up --build
~~~

This composition adds Grafana and uses the [demo2 requirements](./8.%20Performance%20Optimization%20and%20Monitoring/demo2/requirements.txt). Open:

- FastAPI: http://localhost:8000/
- Metrics: http://localhost:8000/metrics
- Prometheus: http://localhost:9090/
- Grafana: http://localhost:3000/

The notes use the initial Grafana credentials admin / admin; change them immediately in any non-local environment. Add a Prometheus data source in Grafana with the container URL http://prometheus:9090, then build panels from request count and duration metrics.

Stop the composition with:

~~~powershell
docker compose down
~~~

## Quick reference

### HTTP methods

| Method | Typical meaning | Common success status |
| --- | --- | --- |
| GET | Read a resource or collection | 200 |
| POST | Create a resource or trigger an action | 200 or 201 |
| PUT | Replace a resource | 200 |
| PATCH | Partially update a resource | 200 |
| DELETE | Remove a resource | 200 or 204 |

### Status codes

| Code | Meaning | Typical FastAPI use in this course |
| --- | --- | --- |
| 200 | OK | Successful reads and JSON responses |
| 201 | Created | A successful creation in a REST-style contract |
| 204 | No Content | Successful operation with no response body |
| 400 | Bad Request | Duplicate employee or invalid login in the demos |
| 401 | Unauthorized | Missing or invalid bearer credentials |
| 403 | Forbidden | Invalid API key or denied access |
| 404 | Not Found | Missing employee or missing route/resource |
| 422 | Unprocessable Entity | Pydantic request validation failure |
| 500 | Internal Server Error | Unhandled server-side exception |

### FastAPI building blocks

| Pattern | Purpose |
| --- | --- |
| app = FastAPI() | Create the application |
| @app.get("/path") | Register a GET path operation |
| @app.post("/path") | Register a POST path operation |
| @app.put("/path/{id}") | Register a replacement/update operation |
| @app.delete("/path/{id}") | Register a delete operation |
| response_model=Model | Validate and document the response shape |
| Depends(provider) | Resolve a dependency and inject its result |
| HTTPException(status_code=..., detail=...) | Return a deliberate HTTP error |
| Header(...) | Read and validate a request header |
| Form(...) | Read form fields such as an OAuth2 login |
| @app.middleware("http") | Add request/response middleware |
| app.add_middleware(...) | Register a Starlette or custom middleware class |

### Pydantic patterns

~~~python
class Payload(BaseModel):
    name: str = Field(..., min_length=3)
    count: StrictInt = Field(..., gt=0)
    note: str | None = None
~~~

- Use Field for constraints and schema metadata.
- Use strict types when coercion would hide client mistakes.
- Use a separate input model and output model when the public contract differs from storage.
- Use model_dump() with Pydantic 2; use .dict() in older Pydantic examples.

### Common commands

~~~bash
# Start a FastAPI app
uvicorn main:app --reload

# Run tests
pytest -q

# Start Redis
docker run --detach --publish 6379:6379 redis

# Start a monitoring composition
docker compose up --build

# Run a Locust scenario
locust -f locustfile.py

# Inspect a cProfile artifact
snakeviz profiles/<profile-name>.prof
~~~

## Troubleshooting

| Symptom | Likely cause | Fix |
| --- | --- | --- |
| ModuleNotFoundError for a sibling file | Uvicorn was started from the repository root | Change into the example directory, then run uvicorn main:app --reload |
| FileNotFoundError: model.joblib | The model path is relative to the current working directory | Start the ML or cache demo from the folder containing its artifact |
| HTTP 422 | Body, path, query, or header does not match the schema | Open /docs, compare required fields and types, and inspect the validation detail |
| EmailStr import/runtime error | email-validator is missing | Install email-validator |
| Form login fails to parse | Multipart form support is missing | Install python-multipart |
| Redis connection refused | Redis is not listening on port 6379 | Start the Redis container and check docker ps |
| @profile is undefined | The script was run with normal Python | Run it through kernprof -l -v |
| Pydantic configuration warning | The example uses a different major-version API | Use the compatibility pattern in the setup section or isolate the module environment |
| Port 8000/9090/3000 is busy | Another local service is using the port | Stop it or change the published Docker port |
| Grafana cannot query Prometheus | The data source uses a host URL from inside the container network | Configure Grafana with http://prometheus:9090 |
| Tests import the wrong app package | Multiple test projects use the same package names | Run pytest from the individual test project directory |

## Suggested study workflow

For each module:

1. Read the linked module notes before opening the implementation.
2. Identify the application object, entry point, route list, inputs, outputs, and external services.
3. Run the smallest example from its own directory.
4. Exercise the route in /docs and with one deliberate invalid request.
5. Read the source again and connect the response to the framework feature being taught.
6. Change one behavior and add a test or manual verification for it.
7. Record what state is in memory, what state is persistent, and what happens after a restart.

Suggested progression:

- **Beginner:** Build the greeting app, then add a typed employee route and inspect /openapi.json.
- **Core API skills:** Add validation, 404/400 errors, query parameters, and a complete CRUD contract.
- **Backend integration:** Run the SQLAlchemy app, inspect test.db, and separate schema, CRUD, and route responsibilities.
- **ML serving:** Re-run model training, compare one prediction with a batch prediction, and test invalid feature values.
- **Security:** Replace demo secrets with environment variables, trace the dependency chain, and inspect the Authorization header.
- **Testing:** Break the loan rule intentionally, run the unit and endpoint suites, then repair the failing assertion.
- **Performance:** Compare a cache hit with a cache miss, profile a slow route, and correlate a Locust run with Prometheus metrics.
- **Production thinking:** Review every hard-coded secret, blocking call, startup side effect, missing timeout, and unbounded input before deploying any example.

The central lesson is that a FastAPI service is not only a set of routes. It is a typed contract surrounded by persistence, inference, security, tests, performance controls, and operational feedback.
