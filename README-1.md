# PostgreSQL Complete Guide with Docker & Flask Integration

Welcome to the **PostgreSQL Complete Guide**! This repository will help you learn PostgreSQL from **Basic to Advanced**, including:

* Manual Installation & Configuration
* PostgreSQL operations and tuning
* Running PostgreSQL in Docker
* Advanced Docker Compose setup
* Connecting PostgreSQL with Python Flask in Dockerized environments

---

## 📚 Table of Contents

1. [Introduction to PostgreSQL](#1-introduction-to-postgresql)
2. [Installation & Setup (Manual)](#2-installation--setup-manual)
3. [Basic SQL Operations](#3-basic-sql-operations)
4. [Advanced PostgreSQL Features](#4-advanced-postgresql-features)
5. [Running PostgreSQL with Docker](#5-running-postgresql-with-docker)
6. [Advanced Docker Compose Setup](#6-advanced-docker-compose-setup)
7. [Flask + PostgreSQL with Docker Compose](#7-flask--postgresql-with-docker-compose)
8. [Project Structure & File Setup](#8-project-structure--file-setup)
9. [Resources & References](#9-resources--references)
10. [To Do / Future Updates](#10-to-do--future-updates)

---

## 1. 📘 Introduction to PostgreSQL

PostgreSQL is a powerful, open-source object-relational database system with over 30 years of active development. It is known for its stability, standards compliance, and extensive feature set including:

* ACID compliance
* Full support for joins, views, stored procedures
* JSON & XML support
* Full-text search
* Extensibility (custom data types, operators, functions)

Official website: [https://www.postgresql.org](https://www.postgresql.org)

---

## 2. ⚙️ Installation & Setup (Manual)

### On Ubuntu:

```bash
sudo apt update
sudo apt install postgresql postgresql-contrib
sudo systemctl start postgresql
sudo systemctl enable postgresql
```

### Set PostgreSQL User Password:

```bash
sudo -u postgres psql
\password postgres
```

### Create Database & User:

```sql
CREATE DATABASE mydb;
CREATE USER suman WITH PASSWORD 'secret123';
GRANT ALL PRIVILEGES ON DATABASE mydb TO suman;
```

---

## 3. 📄 Basic SQL Operations

```sql
-- Create Table
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  name TEXT,
  email TEXT
);

-- Insert Data
INSERT INTO users (name, email) VALUES ('Suman', 'suman@example.com');

-- Select Data
SELECT * FROM users;

-- Update Data
UPDATE users SET name = 'Sumon Pal' WHERE id = 1;

-- Delete Data
DELETE FROM users WHERE id = 1;
```

---

## 4. 🧠 Advanced PostgreSQL Features

* Indexes & Constraints
* Triggers & Stored Procedures
* JSON & Array Data Types
* Role Management
* Performance Tuning
* Backups: `pg_dump`, `pg_restore`
* Logging & Query Analysis

---

## 5. 🚀 Running PostgreSQL with Docker

### Basic Docker Command:

```bash
docker run --name my_postgres \
  -e POSTGRES_USER=suman \
  -e POSTGRES_PASSWORD=secret123 \
  -e POSTGRES_DB=mydb \
  -p 5432:5432 \
  -v pgdata:/var/lib/postgresql/data \
  -d postgres
```

### Connect to PostgreSQL via CLI:

```bash
docker exec -it my_postgres psql -U suman -d mydb
```

---

## 6. 📦 Advanced Docker Compose Setup

### `docker-compose.yml`

```yaml
version: '3.8'
services:
  postgres:
    image: postgres:16
    container_name: my_postgres
    restart: always
    environment:
      POSTGRES_USER: suman
      POSTGRES_PASSWORD: secret123
      POSTGRES_DB: mydb
    volumes:
      - pgdata:/var/lib/postgresql/data
    ports:
      - "5432:5432"

  pgadmin:
    image: dpage/pgadmin4
    container_name: pgadmin
    restart: always
    environment:
      PGADMIN_DEFAULT_EMAIL: admin@example.com
      PGADMIN_DEFAULT_PASSWORD: admin123
    ports:
      - "5050:80"
    depends_on:
      - postgres

volumes:
  pgdata:
```

### Access pgAdmin:

* URL: [http://localhost:5050](http://localhost:5050)
* Email: [admin@example.com](mailto:admin@example.com)
* Password: admin123
* Host: postgres
* DB: mydb

---

## 7. 🌐 Flask + PostgreSQL with Docker Compose

### Folder Structure:

```
flask_postgres_app/
├── app.py
├── requirements.txt
├── Dockerfile
├── docker-compose.yml
```

### `app.py`

```python
from flask import Flask, request, jsonify
import psycopg2

app = Flask(__name__)

conn = psycopg2.connect(
    dbname="mydb",
    user="suman",
    password="secret123",
    host="postgres",
    port="5432"
)
cursor = conn.cursor()

@app.route("/users", methods=["GET"])
def get_users():
    cursor.execute("SELECT * FROM users")
    return jsonify(cursor.fetchall())

if __name__ == "__main__":
    app.run(host='0.0.0.0')
```

### `Dockerfile`

```dockerfile
FROM python:3.11-slim
WORKDIR /app
COPY . .
RUN pip install -r requirements.txt
CMD ["python", "app.py"]
```

### `requirements.txt`

```
Flask
psycopg2-binary
```

### `docker-compose.yml`

```yaml
version: '3.8'
services:
  flask:
    build: .
    ports:
      - "5000:5000"
    depends_on:
      - postgres

  postgres:
    image: postgres:16
    environment:
      POSTGRES_USER: suman
      POSTGRES_PASSWORD: secret123
      POSTGRES_DB: mydb
    ports:
      - "5432:5432"
    volumes:
      - pgdata:/var/lib/postgresql/data

volumes:
  pgdata:
```

Run with:

```bash
docker-compose up --build
```

---

## 8. 🛠 Project Structure & File Setup

Organize your repository like this for clarity:

```
postgresql-docker-flask-guide/
├── flask_postgres_app/
│   ├── app.py
│   ├── requirements.txt
│   ├── Dockerfile
│   └── docker-compose.yml
├── docs/
│   └── advanced_postgres.md
├── scripts/
│   └── init.sql
└── README.md
```

---

## 9. 📚 Resources & References

* [https://www.postgresql.org/docs/](https://www.postgresql.org/docs/)
* [https://hub.docker.com/\_/postgres](https://hub.docker.com/_/postgres)
* [https://www.pgadmin.org/](https://www.pgadmin.org/)
* [https://flask.palletsprojects.com/](https://flask.palletsprojects.com/)
* [https://realpython.com/](https://realpython.com/)

---

Feel free to contribute or raise an issue for improvements 🙌

> Made with ❤️ by [Suman Pal](https://github.com/SumonPaul18)
