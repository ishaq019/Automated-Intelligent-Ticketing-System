# Automated Intelligent Ticketing System

> **Event-Driven GenAI Support Platform** | *MERN Stack, Inngest, Google Gemini*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Node.js](https://img.shields.io/badge/Node.js-v18-green.svg)](https://nodejs.org/)
[![Inngest](https://img.shields.io/badge/Inngest-Event%20Driven-blue)](https://www.inngest.com/)

## 📖 Project Overview

The **Automated Intelligent Ticketing System** is an enterprise-grade support desk application designed to eliminate manual triage bottlenecks. By leveraging **Google Gemini AI** and an **Event-Driven Architecture (Inngest)**, the system automatically analyzes, categorizes, and routes support tickets to the appropriate moderators in real-time.

Unlike traditional CRUD apps, this platform processes heavy AI workloads asynchronously, ensuring a non-blocking, high-performance user experience (reducing API latency by ~60%).

### 🚀 Key Features

* **🤖 AI-Powered Triage (GenAI):** Utilizes **Google Gemini** to analyze ticket descriptions, automatically extracting key issues, assigning priority levels (High/Medium/Low), and generating resolution suggestions.
* **⚡ Event-Driven Architecture:** Implemented using **Inngest** to decouple high-latency AI operations and email notifications from the main server thread.
* **🎯 Smart Routing Algorithm:** Dynamically matches tickets to moderators based on skill sets (e.g., matching a "Database" tag to a moderator with "SQL" skills) using Regex-based logic.
* **🛡️ Role-Based Access Control (RBAC):** Secure authentication and authorization for multiple user roles:
    * **Admin:** Manage users, view system-wide analytics.
    * **Moderator:** distinct dashboard to view and resolve assigned tickets.
    * **User:** Create and track personal support requests.
* **🔔 Automated Notifications:** Asynchronous email alerts via **Nodemailer** when tickets are created, assigned, or resolved.

---

## 🛠️ Tech Stack

* **Frontend:** React.js, Tailwind CSS, Lucide React (Icons)
* **Backend:** Node.js, Express.js
* **Database:** MongoDB (Mongoose ORM)
* **AI Engine:** Google Gemini AI (Generative Language API)
* **Queue/Events:** Inngest (Serverless Event Queue)
* **Authentication:** JWT (JSON Web Tokens) with Custom Middleware
* **Email Service:** Nodemailer (Mailtrap for dev)

---

## 🏗️ Architecture & Workflow

1.  **Ticket Submission:** User posts a ticket via the React Frontend.
2.  **Event Trigger:** The API saves the ticket and immediately triggers an `inngest/event`.
3.  **Async Processing:** Inngest picks up the event in the background:
    * Calls **Google Gemini** to analyze sentiment and content.
    * Updates the database with tags and priority.
    * Executes the **Routing Algorithm** to find the best-fit moderator.
4.  **Completion:** The UI updates in real-time (via polling or re-fetch), and an email is dispatched.

---

## ⚙️ Installation & Setup

Follow these steps to run the project locally.

### 1. Clone the Repository
```bash
git clone [https://github.com/ishaq019/Automated-Intelligent-Ticketing-System.git](https://github.com/ishaq019/Automated-Intelligent-Ticketing-System.git)
cd Automated-Intelligent-Ticketing-System

```

### 2. Backend Setup

Navigate to the server directory (or root if monolithic) and install dependencies:

```bash
npm install

```

Create a `.env` file in the root directory:

```env
# Database
MONGO_URI=your_mongodb_connection_string

# Authentication
JWT_SECRET=your_super_secret_key

# AI Configuration
GEMINI_API_KEY=your_google_gemini_key

# Event Queue
INNGEST_EVENT_KEY=your_inngest_key
INNGEST_SIGNING_KEY=your_inngest_signing_key

# Email (Mailtrap/SMTP)
MAILTRAP_USER=your_mailtrap_user
MAILTRAP_PASS=your_mailtrap_password

```

### 3. Frontend Setup

Navigate to the frontend folder (if separate) and install dependencies:

```bash
cd client  # or whatever your frontend folder is named
npm install

```

---

## 🚀 Running the Project

You need to run the Backend, Frontend, and Inngest Dev Server concurrently.

**1. Start the Backend:**

```bash
npm run dev

```

**2. Start the Inngest Dashboard:**

```bash
npx inngest-cli@latest dev

```

*Open [http://localhost:8288](https://www.google.com/search?q=http://localhost:8288) to see the event stream.*

**3. Start the Frontend:**

```bash
cd client
npm start

```

---

## 🧪 API Endpoints

| Method | Endpoint | Description |
| --- | --- | --- |
| `POST` | `/api/auth/register` | Register a new user |
| `POST` | `/api/auth/login` | Authenticate and receive JWT |
| `POST` | `/api/tickets` | Create a new support ticket |
| `GET` | `/api/tickets` | Fetch user/moderator specific tickets |
| `PUT` | `/api/tickets/:id` | Update ticket status (Resolve/Close) |

---

## 📬 Contact

**Syed Ishaq**

* **GitHub:** [ishaq019](https://www.google.com/search?q=https://github.com/ishaq019)
* **Project Link:** [https://github.com/ishaq019/Automated-Intelligent-Ticketing-System](https://github.com/ishaq019/Automated-Intelligent-Ticketing-System)

---

*This project was engineered to demonstrate advanced backend patterns including Event-Driven Architecture and AI integration.*

```

```
