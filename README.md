# 🎥 VidLinker

A full-stack video collaboration platform that connects **freelancers and clients** for video sharing, review, approval, and publishing through the **YouTube API**.

---

## 📌 Overview

**VidLinker** is a video collaboration platform designed to simplify the workflow between freelancers and clients.

Freelancers can upload videos and share them with clients. Clients can review the submitted videos and either approve or reject them. Approved videos can then be published to the client's YouTube account using the YouTube API.

The application provides separate dashboards and permissions for **Freelancers** and **Clients** using role-based access control.

---

## ✨ Features

### 🔐 Authentication

- Google Authentication using Firebase
- Secure user authentication
- Role-based authorization
- Freelancer and Client roles
- Protected dashboard routes
- Server-side access-token verification
- Persistent authentication state

### 👨‍💻 Freelancer Features

- Freelancer registration/login
- Freelancer profile
- Upload videos
- View uploaded videos
- Manage clients
- Send videos to clients for review
- Track video approval status
- Publish approved videos using YouTube API

### 👥 Client Features

- Client registration/login
- Client profile
- View associated freelancers
- Receive submitted videos
- Review videos
- Approve videos
- Reject videos
- Request changes/revisions

### 🎬 Video Management

- Video uploading
- Video listing
- Video review workflow
- Approval/rejection system
- Client-freelancer video association
- Video status tracking

### 📺 YouTube Integration

- YouTube API integration
- OAuth-based authorization
- Upload approved videos
- Connect application workflow with YouTube

### 🎨 UI

- Responsive design
- Tailwind CSS
- Flowbite React
- React Icons
- Dashboard-based interface
- Role-specific navigation

---

# 🛠️ Tech Stack

## Frontend

| Technology | Purpose |
|---|---|
| React.js | Frontend framework |
| JavaScript | Programming language |
| Vite | Development/build tool |
| Redux Toolkit | State management |
| Redux Persist | Persistent Redux state |
| React Router | Client-side routing |
| Tailwind CSS | Styling |
| Flowbite React | UI components |
| React Icons | Icons |

## Backend

| Technology | Purpose |
|---|---|
| Node.js | Runtime environment |
| Express.js | Backend framework |
| REST APIs | Client-server communication |

## Database

| Technology | Purpose |
|---|---|
| MongoDB | Database |
| Mongoose | MongoDB object modeling |

## Authentication & APIs

| Technology | Purpose |
|---|---|
| Firebase Authentication | Google authentication |
| YouTube Data API | YouTube integration |

## Development Tools

- Git
- GitHub
- npm
- VS Code
- Vite

---

# 🏗️ Architecture

```text
                         ┌─────────────────┐
                         │      USER       │
                         └────────┬────────┘
                                  │
                                  ▼
                         ┌─────────────────┐
                         │ React Frontend  │
                         │     + Vite      │
                         └────────┬────────┘
                                  │
                  ┌───────────────┼───────────────┐
                  │               │               │
                  ▼               ▼               ▼
           ┌────────────┐  ┌────────────┐  ┌─────────────┐
           │  Firebase  │  │   Redux    │  │   React     │
           │    Auth    │  │  Toolkit   │  │   Router    │
           └────────────┘  └────────────┘  └─────────────┘
                                  │
                                  ▼
                         ┌─────────────────┐
                         │  Express Server │
                         │    REST APIs    │
                         └────────┬────────┘
                                  │
                    ┌─────────────┴─────────────┐
                    │                           │
                    ▼                           ▼
             ┌──────────────┐           ┌──────────────┐
             │    MongoDB   │           │  YouTube API │
             │   Database   │           │    OAuth     │
             └──────────────┘           └──────────────┘
```

---

# 📂 Project Structure

```text
VidLinker/
│
├── client/
│   │
│   ├── public/
│   │
│   ├── src/
│   │   │
│   │   ├── assets/
│   │   ├── components/
│   │   ├── pages/
│   │   │   ├── Home.jsx
│   │   │   ├── About.jsx
│   │   │   ├── ContactUs.jsx
│   │   │   ├── AuthPage.jsx
│   │   │   └── PrivateDash.jsx
│   │   │
│   │   ├── dashboard/
│   │   │   ├── Profile.jsx
│   │   │   ├── VideoUpload.jsx
│   │   │   ├── Videos.jsx
│   │   │   ├── Clients.jsx
│   │   │   ├── ReviewVideos.jsx
│   │   │   └── Freelancers.jsx
│   │   │
│   │   ├── redux/
│   │   │   ├── store.js
│   │   │   └── user/
│   │   │
│   │   ├── App.jsx
│   │   ├── main.jsx
│   │   └── index.css
│   │
│   ├── package.json
│   ├── vite.config.js
│   └── .env
│
├── server/
│   │
│   ├── controllers/
│   ├── models/
│   ├── routes/
│   ├── middleware/
│   ├── utils/
│   ├── index.js
│   ├── package.json
│   └── .env
│
├── .gitignore
└── README.md
```

---

# 🔄 Application Workflow

## 👤 Authentication Flow

```text
                    User
                     │
                     ▼
              Google Login
                     │
                     ▼
          Firebase Authentication
                     │
                     ▼
              User Information
                     │
                     ▼
              Backend Server
                     │
                     ▼
          Token Verification
                     │
                     ▼
             Role Detection
                /       \
               /         \
              ▼           ▼
        Freelancer      Client
        Dashboard      Dashboard
```

---

# 👨‍💻 Freelancer Workflow

```text
             Freelancer Login
                    │
                    ▼
          Freelancer Dashboard
                    │
          ┌─────────┼──────────┐
          │         │          │
          ▼         ▼          ▼
       Profile   Upload     Clients
                  Video
                    │
                    ▼
              Select Client
                    │
                    ▼
              Submit Video
                    │
                    ▼
             Client Reviews
                    │
             ┌──────┴──────┐
             │             │
             ▼             ▼
          Approved       Rejected
             │             │
             ▼             ▼
       YouTube Upload   Revision
```

---

# 👥 Client Workflow

```text
                Client Login
                     │
                     ▼
              Client Dashboard
                     │
                     ▼
             Review Videos
                     │
              ┌──────┴──────┐
              │             │
              ▼             ▼
           Approve        Reject
              │             │
              ▼             ▼
        Ready for YouTube  Revision
```

---

# 🎬 Video Lifecycle

```text
        UPLOADED
            │
            ▼
        SUBMITTED
            │
            ▼
         REVIEW
        /      \
       /        \
      ▼          ▼
  APPROVED    REJECTED
      │           │
      │           ▼
      │        REVISION
      │           │
      │           └──────► REVIEW
      │
      ▼
YOUTUBE PUBLISH
```

---

# 🔐 Role-Based Access Control

| Feature | Freelancer | Client |
|---|:---:|:---:|
| Register | ✅ | ✅ |
| Login | ✅ | ✅ |
| Google Authentication | ✅ | ✅ |
| Manage Profile | ✅ | ✅ |
| Upload Video | ✅ | ❌ |
| View Videos | ✅ | ✅ |
| Submit Video | ✅ | ❌ |
| Review Video | ❌ | ✅ |
| Approve Video | ❌ | ✅ |
| Reject Video | ❌ | ✅ |
| Manage Clients | ✅ | ❌ |
| Manage Freelancers | ❌ | ✅ |
| YouTube Publishing | ✅ | ❌ |

---

# 🧭 Application Routes

## Public Routes

```text
/
├── Home
├── About
├── Contact
└── Authentication
```

## Authentication

```text
/auth
├── Client Login
├── Client Signup
├── Freelancer Login
└── Freelancer Signup
```

## Dashboard

```text
/dashboard
├── profile
├── video-upload
├── videos
├── clients
├── review-videos
└── freelancers
```

---

# 🔗 REST API

The frontend communicates with the Express backend through REST APIs.

```text
React
  │
  │ HTTP Request
  ▼
Express.js
  │
  ├───────────────► MongoDB
  │
  └───────────────► YouTube API
```

Example API operations include:

```text
POST   /server/user/signup
POST   /server/user/signin
GET    /server/user/access-token-check

POST   /server/video/upload
GET    /server/video/videos
PUT    /server/video/approve
PUT    /server/video/reject

GET    /server/client
GET    /server/freelancer
```

> API routes may vary depending on the final backend implementation.

---

# 🔥 Firebase Authentication

VidLinker uses Firebase Authentication for Google login.

```text
User
 │
 ▼
Google Sign In
 │
 ▼
Firebase
 │
 ▼
Authentication Result
 │
 ▼
User Information
 │
 ▼
Backend Verification
 │
 ▼
Authorized User
```

This allows users to authenticate securely without storing their Google password inside the application.

---

# 📺 YouTube API Integration

VidLinker integrates with the YouTube API to support video publishing.

```text
Freelancer
     │
     ▼
Client Approves Video
     │
     ▼
YouTube Authorization
     │
     ▼
YouTube API
     │
     ▼
Video Published
```

The integration uses OAuth authorization so that the application can perform authorized YouTube operations on behalf of the connected account.

---

# 🗄️ Database

MongoDB is used to store application data.

Example entities include:

```text
User
 ├── name
 ├── email
 ├── profileImage
 ├── role
 └── createdAt

Video
 ├── title
 ├── description
 ├── videoUrl
 ├── freelancer
 ├── client
 ├── status
 └── createdAt
```

Possible video statuses:

```text
pending
approved
rejected
published
```

---

# 📦 Installation

## Prerequisites

Install the following:

- Node.js
- npm
- MongoDB
- Git

You also need:

- Firebase project
- Google Authentication
- YouTube Data API credentials

---

## 1. Clone Repository

```bash
git clone https://github.com/your-username/VidLinker.git
cd VidLinker
```

---

## 2. Install Frontend

```bash
cd client
npm install
```

---

## 3. Install Backend

Open a new terminal:

```bash
cd server
npm install
```

---

# 🔑 Environment Variables

## Backend `.env`

Create:

```text
server/.env
```

Example:

```env
PORT=5000

MONGO_URI=your_mongodb_connection_string

FIREBASE_PROJECT_ID=your_project_id
FIREBASE_CLIENT_EMAIL=your_client_email
FIREBASE_PRIVATE_KEY=your_private_key

YOUTUBE_CLIENT_ID=your_client_id
YOUTUBE_CLIENT_SECRET=your_client_secret
YOUTUBE_REDIRECT_URI=your_redirect_uri
```

---

## Frontend `.env`

Example:

```env
VITE_FIREBASE_API_KEY=your_api_key
VITE_FIREBASE_AUTH_DOMAIN=your_auth_domain
VITE_FIREBASE_PROJECT_ID=your_project_id
VITE_FIREBASE_STORAGE_BUCKET=your_storage_bucket
VITE_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
VITE_FIREBASE_APP_ID=your_app_id
```

> Never upload `.env` files containing real credentials to GitHub.

---

# ▶️ Running the Application

## Start Backend

```bash
cd server
npm run dev
```

The backend will run on:

```text
http://localhost:5000
```

---

## Start Frontend

Open another terminal:

```bash
cd client
npm run dev
```

Vite will provide the frontend URL, usually:

```text
http://localhost:5173
```

---

# 🧰 Available Scripts

## Frontend

```bash
npm run dev
```

Start development server.

```bash
npm run build
```

Create production build.

```bash
npm run preview
```

Preview production build.

---

## Backend

```bash
npm run dev
```

Start backend using development mode.

```bash
npm start
```

Start backend server.

---

# 🧠 Technical Concepts Demonstrated

VidLinker demonstrates practical implementation of:

- React component architecture
- React Hooks
- Redux Toolkit
- Redux Persist
- React Router
- Protected routes
- Role-based access control
- Firebase Authentication
- Google OAuth
- REST API development
- Express.js
- Node.js
- MongoDB
- Mongoose
- CRUD operations
- API integration
- YouTube API
- Asynchronous JavaScript
- State management
- Client-server architecture
- Responsive UI
- Authentication and authorization

---

# 🎯 Project Objectives

The main objectives of VidLinker are:

1. Simplify communication between freelancers and clients.
2. Provide a centralized video collaboration platform.
3. Allow freelancers to submit videos for client review.
4. Allow clients to approve or reject submitted videos.
5. Provide separate dashboards based on user roles.
6. Integrate YouTube API for video publishing.
7. Build a scalable full-stack web application.
8. Implement secure authentication and authorization.

---

# 📸 Screenshots

Add your project screenshots inside:

```text
screenshots/
├── home.png
├── login.png
├── freelancer-dashboard.png
├── client-dashboard.png
├── video-upload.png
└── video-review.png
```

Then add them to the README:

```markdown
## Home Page

![Home Page](screenshots/home.png)

## Authentication

![Authentication](screenshots/login.png)

## Freelancer Dashboard

![Freelancer Dashboard](screenshots/freelancer-dashboard.png)

## Client Dashboard

![Client Dashboard](screenshots/client-dashboard.png)

## Video Upload

![Video Upload](screenshots/video-upload.png)

## Video Review

![Video Review](screenshots/video-review.png)
```

---

# 🚀 Future Improvements

Future versions of VidLinker can include:

- 💬 Real-time chat
- 🔔 Real-time notifications
- 📝 Video comments
- 📈 Analytics dashboard
- ☁️ Cloud video storage
- 📧 Email notifications
- 🎥 Video streaming optimization
- 🗂️ Video version management
- 🔐 Advanced permissions
- 🚀 CI/CD deployment
- 📱 Mobile application

---

# 💡 Why VidLinker?

Video collaboration can require multiple tools for:

```text
Video Upload
     +
Client Communication
     +
Video Review
     +
Approval
     +
Publishing
```

VidLinker combines these workflows into one platform.

```text
                  VIDLINKER
                      │
       ┌──────────────┼──────────────┐
       │              │              │
       ▼              ▼              ▼
   Freelancer      Client         YouTube
       │              │              │
       └─────── Video Workflow ──────┘
```

The platform provides a structured workflow where freelancers can submit content, clients can review it, and approved content can be published through the YouTube API.

---

# 👩‍💻 Author

## Pooja

B.Tech Electrical Engineering  
National Institute of Technology, Manipur

### Connect With Me

- GitHub: https://github.com/starnge641
- LinkedIn: https://linkedin.com/in/pooja-pooja-6s60922
- LeetCode: https://leetcode.com/u/pk001/

---

# ⭐ Support

If you like this project, consider giving the repository a ⭐ on GitHub.

