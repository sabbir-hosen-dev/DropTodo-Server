



# DropTodo Backend

## Live Link

[Drop Todo](https://drop-todo.netlify.app/)

The backend for **DropTodo**, a task management application built with **Node.js**, **Express**, and **MongoDB**. This backend provides RESTful APIs for managing users and tasks, with real-time updates using **Socket.io**.

---

## **Features**
- **User Management**:
  - Add new users.
  - Authenticate users (if applicable).
- **Task Management**:
  - Create, read, update, and delete tasks.
  - Reorder tasks within categories.
- **Real-Time Updates**:
  - Real-time task updates using Socket.io.
- **Database**:
  - MongoDB for storing users and tasks.

---

## **Technologies Used**
- **Backend**: Node.js, Express
- **Database**: MongoDB (hosted on MongoDB Atlas)
- **Real-Time Communication**: Socket.io
- **Authentication**: (Optional, e.g., JWT, Firebase Auth)
- **Environment Management**: dotenv

---

## **Setup Instructions**

### **Prerequisites**
1. **Node.js**: Install Node.js (v16.x or higher) from [nodejs.org](https://nodejs.org/).
2. **MongoDB**: Create a free MongoDB Atlas cluster or use a local MongoDB instance.
3. **Git**: Install Git from [git-scm.com](https://git-scm.com/).

### **Installation**
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/droptodo-backend.git
   cd droptodo-backend
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Create a `.env` file in the root directory and add the following environment variables:
   ```env
   PORT=5000
   MONGODB_URI=your-mongodb-connection-string
   JWT_SECRET=your-jwt-secret (if using JWT authentication)
   ```
4. Start the server:
   ```bash
   npm start
   ```
   The server will start on `http://localhost:5000`.

---

## **API Endpoints**

### **User Routes**
- **POST `/api/users/add-user`**: Add a new user.
  ```json
  {
    "uid": "firebase-uid",
    "email": "user@example.com",
    "displayName": "John Doe"
  }
  ```

### **Task Routes**
- **GET `/api/tasks`**: Get all tasks for a user.
  ```json
  {
    "userId": "firebase-uid"
  }
  ```
- **POST `/api/tasks`**: Create a new task.
  ```json
  {
    "title": "Task Title",
    "description": "Task Description",
    "category": "To-Do",
    "userId": "firebase-uid"
  }
  ```
- **PUT `/api/tasks/:id`**: Update a task.
  ```json
  {
    "title": "Updated Title",
    "description": "Updated Description",
    "category": "In Progress"
  }
  ```
- **DELETE `/api/tasks/:id`**: Delete a task.
- **PATCH `/api/tasks/reorder`**: Reorder tasks.
  ```json
  [
    {
      "_id": "task-id-1",
      "order": 0,
      "category": "To-Do"
    },
    {
      "_id": "task-id-2",
      "order": 1,
      "category": "To-Do"
    }
  ]
  ```

---

## **Socket.io Events**
- **`taskCreated`**: Emitted when a new task is created.
- **`taskUpdated`**: Emitted when a task is updated.
- **`taskDeleted`**: Emitted when a task is deleted.
- **`tasksReordered`**: Emitted when tasks are reordered.

---

## **Environment Variables**
| Variable Name     | Description                          | Example Value                     |
|-------------------|--------------------------------------|-----------------------------------|
| `PORT`            | Port for the backend server          | `5000`                           |
| `MONGODB_URI`     | MongoDB connection string            | `mongodb+srv://user:pass@cluster`|
| `JWT_SECRET`      | Secret key for JWT authentication    | `your-secret-key`                |

---

## **Deployment**
### **Vercel**
1. Install Vercel CLI:
   ```bash
   npm install -g vercel
   ```
2. Deploy:
   ```bash
   vercel
   ```

### **Heroku**
1. Create a `Procfile` in the root directory:
   ```
   web: node index.js
   ```
2. Push your code to Heroku:
   ```bash
   git push heroku main
   ```

---

## **Contributing**
Contributions are welcome! Please follow these steps:
1. Fork the repository.
2. Create a new branch (`git checkout -b feature/your-feature`).
3. Commit your changes (`git commit -m 'Add some feature'`).
4. Push to the branch (`git push origin feature/your-feature`).
5. Open a pull request.

---



