# 🧠 Store Rating System (Fullstack)

A full-featured Store Rating Platform with **Role-Based Access**, built using **React.js**, **Node.js**, **Express.js**, and **PostgreSQL**.  
Users can rate stores, store owners can view dashboards, and admins can manage the entire system.

---

## 🧱 Tech Stack

| Layer      | Tech                             |
|------------|----------------------------------|
| Frontend   | React.js, Axios, React Router    |
| Backend    | Node.js, Express.js, JWT, bcrypt |
| Database   | PostgreSQL                       |
| Auth       | JWT + Role-based Access          |
| Styling    | Basic CSS (customizable)         |
| Dev Tools  | nodemon, dotenv                  |

---

## ✨ Features

- 🔐 Secure login for `user`, `store_owner`, `admin`

- ⭐ Rate stores from 1 to 5

- 🏪 Store owner dashboard: average ratings & reviewers

- 🧑‍💼 Admin: add users, add stores, view listings

- 🧱 Scalable architecture with clean separation

---

## 🗄️ Database Tables

### `users`

| Field         | Type               | Description                |
|---------------|--------------------|----------------------------|
| id            | SERIAL PRIMARY KEY | Unique user ID             |
| name          | VARCHAR(100)       | User’s name                |
| email         | VARCHAR(100)       | Unique email               |
| password_hash | TEXT               | Hashed password            |
| address       | TEXT               | User address               |
| role          | VARCHAR(20)        | user \ store_owner \ admin |

### `stores`

| Field     | Type               | Description                 |
|-----------|--------------------|-----------------------------|
| id        | SERIAL PRIMARY KEY | Store ID                    |
| name      | VARCHAR(100)       | Store name                  |
| address   | TEXT               | Store location              |
| email     | VARCHAR            | Contact email               |
| owner_id  | INTEGER            | FK → users(id)              |

### `ratings`

| Field     | Type     | Description                        |
|-----------|----------|------------------------------------|
| id        | SERIAL   | Unique rating ID                   |
| user_id   | INTEGER  | FK → users(id)                     |
| store_id  | INTEGER  | FK → stores(id)                    |
| rating    | INTEGER  | Must be between 1 and 5 (inclusive)|

---

## 🚀 Getting Started

### 🔧 Prerequisites

- Node.js (v18+)
- PostgreSQL (local or hosted)

---

## 📁 Folder Structure

    Store-rating/
    ├── backend/
    │ ├── db.js
    │ ├── middleware.js
    │ ├── server.js
    │ ├── .env
    │ └── package.json
    └── frontend/
    ├── src/
    │ ├── components/
    │ ├── pages/
    │ ├── App.js
    │ └── index.js
    ├── .env
    └── package.json

---

## 🔧 Backend Setup

1. **Navigate to the backend folder:**

    ```bash
    cd backend
    npm install

2. **Create .env:**

    PORT=5000
    DATABASE_URL=postgresql://username:password@localhost:5432/your_db
    JWT_SECRET=yourSuperSecretKey

3. **Start the backend server:**

    ```bash
    npm run dev    # with nodemon
    npm start      # production

### 🧠 API Endpoints

    | Method |         Endpoint        |           Description         |
    | ------ | ----------------------- | ----------------------------- |
    |  POST  | `/register`             |   Register new user           |
    |  POST  | `/login`                |   Login and get JWT           |
    |  POST  | `/admin/users`          |   Add user (admin-only)       |
    |  POST  | `/admin/stores`         |   Add Store (admin-only)      |
    |  GET   | `/admin/dashboard`      |   Dashboard stats(admin-only) |
    |  GET   | `/admin/users`          |   Route: Filter users         |
    |  GET   | `/admin/stores`         |   Route: Filter stores        |
    |  GET   | `/admin/users/:id`      |   User details                |
    |  GET   | `/stores`               |   List of Store for user      |
    |  POST  | `/stores/:storeId/rate` |   Store rating                |
    |  GET   | `/store/dashboard`      |   Store dashboard             |
    |  PUT   | `/password`             |   Update password             |

---

## 🎨 Frontend Setup

1. **Navigate to the frontend folder:**

    ```bash
    cd frontend
    npm install

2. **Start the React frontend:**

    ```bash
    npm start

Frontend runs at http://localhost:3000

### 🧠 Usage Flows

    ✅ User: Log in → View stores → Rate

    🛒 Store Owner: Log in → See ratings dashboard

    🧑‍💼 Admin: Log in → Add users/stores, monitor system

---

## 🧠 Author

Engineered with clarity by Deepak U