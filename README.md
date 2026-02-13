# AuthAPI

FastAPI-based authentication API using SQLite + SQLAlchemy and JWT.

## Run locally

1. Install dependencies

```bash
pip install -r requirements.txt
```

2. Start the server

```bash
uvicorn main:app --reload
```

3. Open Swagger UI

- http://127.0.0.1:8000/docs

## Screenshots

![Register](images/Register.png)
![Token Login](images/TokenLogin.png)
![JWT](images/JWT.png)
