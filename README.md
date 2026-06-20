📚 Task Management App — Full Stack
A full-stack task management application with secure authentication, a Java Spring Boot REST API, MySQL persistence, and real-time sync across devices via WebSocket.

Live demo (frontend): https://pradeeshkumars2006.github.io/Task-Mangement/ Source code: this repository


✨ Features
🔐 User authentication — signup & login with JWT, passwords hashed with BCrypt
⚙️ Backend REST API — built with Java Spring Boot 3
🗄️ Database integration — MySQL via Spring Data JPA / Hibernate
⚡ Real-time sync — WebSocket (STOMP over SockJS); tasks update instantly across every open tab/device for the same account
🎨 Clean UI/UX — minimal card-based design, no clutter
📱 Mobile responsive — fluid layout, tested down to 360px width
📄 Documented & ready to deploy


🏗️ Architecture
Browser (HTML/CSS/JS, GitHub Pages)

        │  REST (fetch) + WebSocket (STOMP/SockJS)

        ▼

Spring Boot API  ── JWT filter ── Spring Security

        │

        ▼

   MySQL Database

Layer
Technology
Frontend
HTML5, CSS3, Vanilla JS, SockJS + STOMP.js
Backend
Java 17, Spring Boot 3 (Web, Security, JPA, WebSocket)
Auth
JWT (jjwt), BCrypt password hashing
Database
MySQL 8
Real-time
STOMP over WebSocket (SockJS fallback)



📁 Project Structure
task-management-fullstack/

├── backend/

│   ├── pom.xml

│   └── src/main/java/com/pradeesh/taskmanager/

│       ├── TaskManagerApplication.java

│       ├── config/        (SecurityConfig, WebSocketConfig)

│       ├── security/      (JwtUtil, JwtAuthFilter)

│       ├── model/         (User, Task)

│       ├── repository/    (UserRepository, TaskRepository)

│       ├── dto/           (RegisterRequest, LoginRequest, AuthResponse, TaskDto)

│       ├── service/       (UserDetailsServiceImpl)

│       └── controller/    (AuthController, TaskController)

└── frontend/

    ├── index.html

    ├── login.html

    ├── signup.html

    ├── dashboard.html

    ├── css/style.css

    └── js/ (api.js, dashboard.js)


🚀 Getting Started
1. Database
Create a MySQL database:

CREATE DATABASE taskmanager_db;
2. Backend
Edit backend/src/main/resources/application.properties with your MySQL username/password, then:

cd backend

mvn spring-boot:run

The API starts on http://localhost:8080. Tables are auto-created by Hibernate on first run.
3. Frontend
Open frontend/login.html in a browser (or serve the folder with any static server / GitHub Pages). By default it calls the API at http://localhost:8080/api — update API_BASE_URL in js/api.js once you deploy the backend (e.g. Render, Railway) to point at the live URL.


🔌 API Reference
Method
Endpoint
Auth required
Description
POST
/api/auth/signup
No
Register a new user
POST
/api/auth/login
No
Log in, returns JWT
GET
/api/tasks
Yes
List the logged-in user's tasks
POST
/api/tasks
Yes
Create a task
PUT
/api/tasks/{id}
Yes
Update a task
DELETE
/api/tasks/{id}
Yes
Delete a task


Send the JWT as Authorization: Bearer <token> on every /api/tasks/** request.

Real-time channel: connect via SockJS to /ws, subscribe to /topic/tasks/{userEmail} to receive live CREATED / UPDATED / DELETED events.


🛣️ Roadmap / Ideas for extension
Task priorities & categories/tags
Email reminders for due dates
Shared/team task lists
Dark mode
Deploy backend to Render + frontend already on GitHub Pages


👤 Author
Pradeesh Kumar S — B.Sc Computer Science, SRM Arts and Science College GitHub: @pradeeshkumarS2006

