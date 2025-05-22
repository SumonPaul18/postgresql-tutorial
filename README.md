# 📘 PostgreSQL Tutorial with Projects 🚀

Welcome to the ultimate beginner-friendly PostgreSQL tutorial repository!  
This repo is designed to teach you PostgreSQL step-by-step — starting from installation to advanced integration with Docker and Python Flask, including real-world mini projects.

---

## 📚 Table of Contents

- [🎯 Who Is This For?](#-who-is-this-for)
- [⚙️ Step-by-Step Learning Path](#️-step-by-step-learning-path)
- [📦 PostgreSQL with Docker](#-postgresql-with-docker)
- [🐍 Connect PostgreSQL with Python Flask](#-connect-postgresql-with-python-flask)
- [🛠️ Real-World Projects](#️-real-world-projects)
- [📁 Folder Structure](#-folder-structure)
- [💡 Tips & Resources](#-tips--resources)
- [🤝 Contributing](#-contributing)
- [📜 License](#-license)

---

## 🎯 Who Is This For?

This tutorial is perfect for:

- 🔰 Beginners in SQL and PostgreSQL
- 🐍 Python or Flask developers looking to integrate databases
- 🐳 Developers who want to use PostgreSQL with Docker
- 🧠 Anyone interested in building real-world backend projects

---

## ⚙️ Step-by-Step Learning Path

| Step | Topic                              | Folder / Path          |
|------|------------------------------------|-------------------------|
| 1️⃣   | PostgreSQL Installation (Ubuntu/Windows) | `docs/install/`     |
| 2️⃣   | PostgreSQL Basic SQL Commands      | `basic/`               |
| 3️⃣   | Run PostgreSQL using Docker        | `docker/`              |
| 4️⃣   | Connect PostgreSQL with Python Flask | `flask-postgres/`   |
| 5️⃣   | Mini Projects with CRUD Operations | `projects/`            |

---

## 📦 PostgreSQL with Docker

In the [`docker/`](docker/) directory, you’ll find a `docker-compose.yml` that sets up:

- PostgreSQL Server
- pgAdmin (GUI interface for managing PostgreSQL)

### 🛠️ Start Docker Setup:

```bash
docker-compose up -d
````

* PostgreSQL: `localhost:5432`
* pgAdmin: `http://localhost:5050`

Use the credentials set in your `docker-compose.yml` to login to pgAdmin and manage your DB visually.

---

## 🐍 Connect PostgreSQL with Python Flask

In the [`flask-postgres/`](flask-postgres/) folder, you'll learn how to:

* Connect Flask to PostgreSQL using `psycopg2`
* Create REST API endpoints
* Perform basic CRUD operations

### Example APIs:

| Method | Endpoint            | Action             |
| ------ | ------------------- | ------------------ |
| POST   | `/add_user`         | Add a new user     |
| GET    | `/users`            | Retrieve all users |
| PUT    | `/update_user/<id>` | Update a user      |
| DELETE | `/delete_user/<id>` | Delete a user      |

---

## 🛠️ Real-World Projects

| Project         | Description                              | Folder                |
| --------------- | ---------------------------------------- | --------------------- |
| 🧾 CRUD API     | Basic user management system             | `projects/crud/`      |
| ✅ ToDo App      | Task management REST API                 | `projects/todo/`      |
| 🎓 Student DB   | Manage student records (add/edit/delete) | `projects/student/`   |
| 📦 Inventory DB | Product inventory management app         | `projects/inventory/` |

These projects are designed for hands-on practice and real-world learning.

---

## 📁 Folder Structure

```
postgresql-tutorial-with-projects/
├── README.md
├── docker/
│   └── docker-compose.yml
├── flask-postgres/
│   └── app.py
├── projects/
│   ├── crud/
│   ├── todo/
│   ├── student/
│   └── inventory/
├── docs/
│   └── install.md
├── basic/
│   └── sample_queries.sql
```

---

## 💡 Tips & Resources

* Use **pgAdmin** for managing tables, data, and relationships visually.
* Practice basic SQL queries on sites like:

  * [SQLBolt](https://sqlbolt.com/)
  * [Mode Analytics SQL Tutorial](https://mode.com/sql-tutorial/)
* Flask documentation: [https://flask.palletsprojects.com/](https://flask.palletsprojects.com/)
* PostgreSQL official docs: [https://www.postgresql.org/docs/](https://www.postgresql.org/docs/)

---

## 🤝 Contributing

Contributions are welcome!
If you’d like to improve this tutorial or add more project ideas, feel free to fork this repo and submit a pull request.

---


**Made with ❤️ by Suman Pal**

---

