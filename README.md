# Leos Club EventFlow

[![Ask DeepWiki](https://devin.ai/assets/askdeepwiki.png)](https://deepwiki.com/nesdan40/Leo-s-Club-Project)

EventFlow is a full-stack web application designed for the Leos Club of Samruddhi (NGO under Lions Club International) to streamline event and volunteer management. Built with a Node.js backend and a React frontend, it provides a centralized platform for creating events, importing volunteers, assigning tasks, and monitoring progress with role-based access control.

## Key Features

*   **Role-Based Access Control**: Delineated permissions for Admins, Event Managers, and Team Members (volunteers).
*   **Event Management**: Event Managers can create, view, and manage event details.
*   **Task Management**: Assign tasks to volunteers, track completion percentages, and manage deadlines. Volunteers can view and update their assigned tasks.
*   **Volunteer Import**: Event Managers can bulk-import volunteers from an Excel (`.xlsx`) file. New volunteers automatically have accounts created and receive their login credentials via email.
*   **Admin Dashboard**: Admins have access to a system-wide dashboard with analytics on event status and task completion rates.
*   **Modern UI**: A responsive, clean, and minimal dashboard built with React, TypeScript, and Tailwind CSS.
*   **RESTful API**: A well-structured backend API built with Express.js and Mongoose.

## Tech Stack

| Component | Technologies                                                                          |
| :-------- | :------------------------------------------------------------------------------------ |
| **Backend**   | Node.js, Express, MongoDB, Mongoose, JWT (Authentication), Nodemailer, Multer, ExcelJS |
| **Frontend**  | React, TypeScript, Vite, Tailwind CSS, React Query, Zustand, Axios, Recharts            |

## Getting Started

### Prerequisites

*   Node.js (v18+ recommended)
*   npm (v9+ recommended)
*   MongoDB Atlas account or a local MongoDB instance
*   Git

### Backend Setup

1.  Navigate to the `backend` directory:
    ```sh
    cd backend
    ```

2.  Install the required dependencies:
    ```sh
    npm install
    ```

3.  Create a `.env` file in the `backend/` directory and populate it with your environment variables. Use the following template:
    ```env
    # Server Configuration
    PORT=5000

    # MongoDB Connection (use your Atlas string or local URI)
    MONGO_URI=mongodb+srv://<username>:<password>@cluster-url.mongodb.net/your-db-name

    # JWT Secret (generate a long, random string)
    JWT_SECRET=your_super_secret_jwt_key

    # Email Configuration (Optional - for sending volunteer credentials)
    EMAIL_HOST=smtp.gmail.com
    EMAIL_PORT=587
    EMAIL_USER=your-email@gmail.com
    EMAIL_PASS=your-16-character-gmail-app-password
    EMAIL_FROM="NGO EventFlow <your-email@gmail.com>"
    FRONTEND_URL=http://localhost:5173
    ```
    > **Note:** For detailed instructions on setting up MongoDB and email credentials, refer to the `backend/SETUP_GUIDE.md`.

4.  Start the development server:
    ```sh
    npm run dev
    ```
    The backend will be running on `http://localhost:5000`.

### Frontend Setup

1.  Navigate to the `frontend` directory:
    ```sh
    cd frontend
    ```

2.  Install the required dependencies:
    ```sh
    npm install
    ```

3.  The frontend is configured to proxy API requests from `/api` to `http://localhost:5000` (the backend server) during development. No `.env` file is required for this default setup.

4.  Start the development server:
    ```sh
    npm run dev
    ```
    The frontend will be running on `http://localhost:5173`.

## Roles & Permissions

The application features three distinct user roles with specific permissions:

| Role            | Permissions                                                                                                                                                             |
| :-------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Admin**       | Has full access to the system. Can view the admin dashboard with comprehensive analytics, manage all events, and all tasks.                                           |
| **Event Manager** | Can create new events, import volunteers for events they manage, and create, assign, and delete tasks within their events.                                                 |
| **Team Member** | (Volunteer) Can view events they are a part of, see tasks assigned to them, and update the status and completion percentage of their own tasks.                               |

## Project Structure

The repository is organized into two main directories: `backend` and `frontend`.

```
.
├── backend/
│   ├── src/
│   │   ├── controllers/  # Request handling logic
│   │   ├── middleware/   # Auth, roles, error handling
│   │   ├── models/       # Mongoose schemas
│   │   ├── routes/       # API endpoint definitions
│   │   └── utils/        # Email service, password generator
│   ├── API_TESTING_GUIDE.md
│   └── SETUP_GUIDE.md
│
└── frontend/
    ├── src/
    │   ├── components/   # Reusable UI components
    │   ├── layouts/      # Main application layouts
    │   ├── pages/        # Route-specific page components
    │   ├── services/     # API interaction layer (axios)
    │   └── store/        # Global state management (Zustand)
    └── vite.config.ts    # Vite configuration with API proxy
```

## API Documentation

For a complete guide on all available API endpoints, request/response formats, and how to test them using tools like Postman, please refer to the **[API Testing Guide](./backend/API_TESTING_GUIDE.md)** located in the `backend` directory.
