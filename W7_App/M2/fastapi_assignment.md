## Student Assignment: Building a Modular API with FastAPI

### Project Overview

In this assignment, you will develop a **Task Management System** backend using FastAPI. This project focuses on structuring a professional-grade API using modern Python type hinting, modular routing, and robust data validation with Pydantic.

---

### Learning Objectives

By the end of this project, you will be able to:

* Organize code into logical modules using `APIRouter`.
* Enforce data integrity using Pydantic `BaseModel` and `@field_validator`.
* Implement complex data structures with **Nested Models**, `Literal`, and `Annotated`.
* Handle various HTTP methods and parameter types.

---

### Project Structure

To maintain scalability, follow this directory structure:

```text
task_manager/
├── main.py
├── routers/
│   ├── users.py
│   └── tasks.py
└── schemas/
    └── models.py

```

---

### Phase 1: Data Modeling (Schemas)

In `schemas/models.py`, define the data shapes. You must use `Annotated` for metadata and `@field_validator` for custom logic.

```python
from pydantic import BaseModel, Field, field_validator
from typing import List, Literal, Annotated

class Profile(__BLANK__):
    __BLANK__

class UserCreate(__BLANK__):
    __BLANK__

class TaskCreate(__BLANK__):
    __BLANK__

    @field_validator('title')
    @classmethod
    def title_must_be_capitalized(cls, v: str) -> str:
        __BLANK__
```

*Source: [Pydantic Documentation on Validators*](https://docs.pydantic.dev/latest/concepts/validators/)

---

### Phase 2: Modular Routing

Create separate routers for `users` and `tasks`. Use `APIRouter` to group these endpoints.

**Example: `routers/tasks.py**`

```python
from fastapi import APIRouter, Query
from typing import Annotated
from schemas.models import TaskCreate

router = __BLANK__

@router.get("/")
async def __BLANK_

@router.post("/")
async def __BLANK__

```

*Source: [FastAPI Documentation on Bigger Applications*](https://fastapi.tiangolo.com/tutorial/bigger-applications/)

---

### Phase 3: Application Assembly

In `main.py`, initialize the FastAPI app and include your routers.

```python
from fastapi import FastAPI
from routers import users, tasks

app = __BLANK__

# Include the routers
app.__BLANK__
app.__BLANK__

@app.get("/")
async def root():
    return {"message": "Welcome to the Task API"}

```

---

### Submission Requirements

1. **Codebase:** A GitHub link containing the completed modules.
2. **Validation Test:** Provide a screenshot of the `/docs` (Swagger UI) showing a successful `POST` request to `/tasks` that passes the `@field_validator` logic.
3. **Error Handling:** Provide a screenshot of the 422 Unprocessable Entity error when the `Literal` role or `Annotated` priority constraints are violated.
