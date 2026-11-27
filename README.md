# TaskBoard v0.1

## Purpose

TaskBoard is a lightweight CRUD REST API built with FastAPI to create, list, read, update and delete tasks. It is the starting point of the DevSecOps CI/CD pipeline built in the next sessions.

## Requirements

- Python 3.11+
- Git

## Installation

```bash
git clone https://github.com/datyaaas/Taskboard.git
cd Taskboard
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

## Run

```bash
uvicorn app.main:app --reload
```

The API is then available at http://127.0.0.1:8000 and the interactive documentation (Swagger UI) at http://127.0.0.1:8000/docs.

## Endpoints

| Method | Path | Description |
| --- | --- | --- |
| GET | `/health` | Health check |
| POST | `/tasks` | Create a task (201) |
| GET | `/tasks` | List all tasks |
| GET | `/tasks/{task_id}` | Get one task (404 if unknown) |
| PATCH | `/tasks/{task_id}` | Update only the fields sent (404 if unknown) |
| DELETE | `/tasks/{task_id}` | Delete a task (204, 404 if unknown) |

## Tests

```bash
pytest
```

## Environment variables

Copy `.env.example` to `.env` and adapt the values locally:

```bash
cp .env.example .env
```

Never commit `.env`: it is ignored by `.gitignore`. `.env.example` must only contain placeholder values, never a real secret.

## Project structure

```
Taskboard/
├── app/
│   ├── __init__.py
│   ├── main.py          # FastAPI application and /health
│   ├── schemas.py       # Pydantic models
│   └── routers/
│       ├── __init__.py
│       └── tasks.py     # /tasks CRUD endpoints (in-memory storage)
├── tests/
│   ├── __init__.py
│   └── test_tasks.py
├── docs/
├── .gitignore
├── .env.example
├── README.md
└── requirements.txt
```
