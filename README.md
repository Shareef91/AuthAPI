# Auth API (FastAPI)

A lightweight authentication API built with **FastAPI**, backed by **SQLite + SQLAlchemy**, and secured with **JWT**.

Data is stored in a local SQLite file (`users.db`) created automatically on first run.

## Features

- User registration (password hashing)
- User login (JWT access token)
- Protected route example (Bearer token)
- Interactive API docs (Swagger UI / ReDoc)

## Tech Stack

- Python 3.9+
- FastAPI
- Pydantic
- SQLAlchemy
- SQLite
- passlib (bcrypt)
- python-jose (JWT)
- Uvicorn

## Project Structure

```
AuthAPI/
├── main.py          # FastAPI application and routes
├── requirements.txt # Python dependencies
├── images/          # Screenshots used in this README
└── README.md        # Project documentation
```

## Getting Started

### 1) Create and activate a virtual environment (recommended)

Windows (PowerShell):

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

### 2) Install dependencies

```bash
pip install -r requirements.txt
```

### 3) Run the API

```bash
uvicorn main:app --reload
```

When running, FastAPI exposes interactive documentation automatically:

- Swagger UI: `/docs`
- ReDoc: `/redoc`

## API Reference

### `GET /`

Health-check style endpoint.

### `POST /register`

Register a new user.

Request body:

```json
{ "username": "alice", "password": "strong_password" }
```

Response:

```json
{ "status": "user registered" }
```

### `POST /login`

Authenticate and receive a JWT access token.

Request body:

```json
{ "username": "alice", "password": "strong_password" }
```

Response:

```json
{ "access_token": "<token>", "token_type": "bearer" }
```

### `GET /protected`

Example protected endpoint. Requires an `Authorization: Bearer <token>` header.

Response:

```json
{ "message": "JWT validated successfully", "user": "alice" }
```

## Screenshots

### Register

Example request/response for user registration.

![Register](images/Register.png)

### Token Login

Example login returning a JWT token.

![Token Login](images/TokenLogin.png)

### JWT

Example of a JWT being used to call a protected route.

![JWT](images/JWT.png)

## Notes / Limitations

- Uses a local SQLite database file named `users.db`.
- `SECRET_KEY` is currently hard-coded in `main.py` (rotate/move to environment variables for production).
- Minimal validation/error handling; intended as a learning/demo project.

## Next Improvements (Optional)

- Move secrets/config to environment variables
- Add refresh tokens + logout/denylist
- Add tests with `pytest`
- Add database migrations (Alembic)
