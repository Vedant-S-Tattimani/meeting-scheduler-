# ⚡ HackHive (Lumina) — Intelligent Meeting Scheduler

<div align="center">

> **The next-generation, conflict-free scheduling and collaboration platform. Featuring atomic booking integrity, smart slot recommendations, interactive 3D visual experiences, instant video rooms, and real-time state synchronization.**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![React 19](https://img.shields.io/badge/Frontend-React%2019%20%2B%20Vite-61dafb.svg)](https://react.dev/)
[![Three.js](https://img.shields.io/badge/3D%20Graphics-Three.js%20%2F%20Fiber-black.svg)](https://threejs.org/)
[![Node.js](https://img.shields.io/badge/Backend-Node.js%20%2B%20Express-339933.svg)](https://nodejs.org/)
[![Socket.io](https://img.shields.io/badge/Realtime-Socket.io%20v4-010101.svg)](https://socket.io/)
[![MongoDB](https://img.shields.io/badge/Database-MongoDB%20Atlas-47A248.svg)](https://www.mongodb.com/)

[**Explore For Everyone**](#-part-1-the-big-picture--for-everyone) • 
[**Explore For Developers**](#-part-2-under-the-hood--for-engineers--architects) • 
[**System Architecture**](#-system-architecture) • 
[**Quickstart Guide**](#-quickstart-guide) • 
[**Demo Accounts**](#-instant-demo-credentials)

</div>

---

## 📖 Table of Contents
- [🌟 Part 1: The Big Picture — For Everyone](#-part-1-the-big-picture--for-everyone)
  - [The Problem We Solve](#-the-problem-we-solve)
  - [How It Works (In 3 Simple Steps)](#-how-it-works-in-3-simple-steps)
  - [Key User Benefits](#-key-user-benefits)
- [⚙️ Part 2: Under the Hood — For Engineers & Architects](#-part-2-under-the-hood--for-engineers--architects)
  - [System Architecture](#-system-architecture)
  - [Atomic Conflict-Free Booking Engine](#-atomic-conflict-free-booking-engine)
  - [Intelligent Multi-Signal Slot Recommendation Algorithm](#-intelligent-multi-signal-slot-recommendation-algorithm)
  - [Real-Time Socket State Engine](#-real-time-socket-state-engine)
  - [Enterprise Security & Resilience](#-enterprise-security--resilience)
- [🛠️ Tech Stack Matrix](#-tech-stack-matrix)
- [📁 Repository Structure](#-repository-structure)
- [🚀 Quickstart Guide](#-quickstart-guide)
  - [Prerequisites](#prerequisites)
  - [1. Backend Setup](#1-backend-setup)
  - [2. Frontend Setup](#2-frontend-setup)
  - [3. Instant Demo Data](#3-instant-demo-data)
- [🔑 Instant Demo Credentials](#-instant-demo-credentials)
- [📡 API Reference Overview](#-api-reference-overview)
- [📄 License & Authors](#-license--authors)

---

## 🌟 Part 1: The Big Picture — For Everyone

> *"No more calendar back-and-forth. No more awkward timezone calculations. No more accidental double-bookings."*

### 🛑 The Problem We Solve
Scheduling a meeting across modern teams is surprisingly painful:
1. **The Email Ping-Pong**: Endless messages asking *"Does Tuesday at 3 PM work? No? What about Thursday at 11 AM?"*
2. **Double Booking Accidents**: Two people book the exact same slot at the same time because traditional calendars update slowly.
3. **Time Zone Headaches**: Calculating whether 4:00 PM in London conflicts with 9:30 PM in Mumbai or 8:00 AM in San Francisco.
4. **Third-Party Video Friction**: Having to generate and copy separate Zoom or Teams links every single time.

### ✨ What HackHive Does
**HackHive (Lumina)** is a smart, automated meeting assistant. You configure your available hours once, share your personal booking link, and let guests pick a time that works for them. 

The system guarantees that **no slot is ever double-booked**, automatically detects everyone's local timezone, sends instant email and calendar confirmations, and provides a built-in video room with one click.

---

### 🔄 How It Works (In 3 Simple Steps)

```mermaid
flowchart LR
    A["1️⃣ Set Working Hours<br>Define weekly slots & buffers"] --> B["2️⃣ Share Booking Link<br>Guests view live interactive calendar"]
    B --> C["3️⃣ Conflict-Free Booking<br>Instant video room & email invites"]
```

1. **Set Your Availability**: Choose what days and hours you want to take calls, set buffer times between meetings to prevent burnout, and block out personal time.
2. **Share Your Link**: Send your booking page to clients, candidates, or teammates. The page automatically translates your hours into the guest’s local timezone.
3. **Confirmed in One Click**: As soon as a guest picks a slot, it is locked instantly across all screens in real-time. Both parties receive an email confirmation, Google Calendar event, and a built-in video conferencing link.

---

### 🎁 Key User Benefits

| Feature | What It Does For You |
| :--- | :--- |
| **🛡️ 100% Conflict-Proof** | Two people can never book the same time slot, even if they click at the exact same millisecond. |
| **🌍 Automatic Timezone Detection** | Your guest in Tokyo sees Tokyo time; you see your local time. No mental math required. |
| **📹 Built-in Video Conferencing** | Click "Join Meeting" directly inside the web app via integrated Jitsi Meet — no Zoom download required. |
| **🏢 Team & Organization Workspaces** | Organize meetings across multiple team members, departments, and shared group calendars. |
| **🔔 Instant Notifications** | A real-time notification bell immediately alerts hosts when meetings are scheduled, rescheduled, or cancelled. |
| **🎨 Modern 3D Visual Experience** | Fluid motion graphics, 3D interactive scheduling visuals, and dark-mode elegance powered by Three.js and Framer Motion. |

---

## ⚙️ Part 2: Under the Hood — For Engineers & Architects

For developers, technical leads, and system reviewers, here is how HackHive is architected for scalability, concurrency safety, and low-latency interaction.

---

### 🏗️ System Architecture

HackHive is structured as a **modular service-oriented full-stack application**, decoupling business logic into specialized services and utilizing WebSocket rooms for targeted state broadcasting.

```mermaid
graph TD
    subgraph "Client Layer (React 19 + Vite)"
        Canvas["Three.js / React Three Fiber Canvas"]
        Views["Dashboard, Booking & Admin Views"]
        SocketHook["Socket.io Client Hook"]
        AxiosClient["Axios REST Client (v1)"]
    end

    subgraph "Security & API Gateway (Express.js)"
        SecLayer["Helmet • RateLimit • MongoSanitize • HPP • XSS Clean"]
        AuthMiddleware["JWT Auth Guard & Role Verifier"]
        Router["Express v1 Router"]
    end

    subgraph "Service Layer (Business & Scheduling Logic)"
        AIService["AI Scheduler (Multi-Signal Scoring)"]
        SlotService["Slot Engine (Atomic Lock & Allocation)"]
        AnalyticsService["Analytics Pipeline (MongoDB $facet)"]
        SocketService["Socket.io Event Dispatcher"]
        CalendarService["Google Calendar & Nodemailer"]
    end

    subgraph "Data & Persistence Layer"
        MongoCluster[("MongoDB Atlas<br>(Compound Indexed)")]
        RedisCache["In-Memory Cache (TTL Buffer)"]
    end

    Canvas --> Views
    Views --> AxiosClient
    Views --> SocketHook
    AxiosClient --> SecLayer
    SecLayer --> AuthMiddleware
    AuthMiddleware --> Router
    Router --> AIService
    Router --> SlotService
    Router --> AnalyticsService
    SocketHook <--> SocketService
    SlotService --> MongoCluster
    SlotService --> SocketService
    AIService --> MongoCluster
    AnalyticsService --> MongoCluster
    AnalyticsService --> RedisCache
    SlotService --> CalendarService
```

---

### 🛡️ Atomic Conflict-Free Booking Engine

In high-concurrency environments (e.g. popular webinar or interview bookings), standard "check-then-insert" logic creates race conditions resulting in catastrophic double-bookings.

HackHive solves this at the database engine level by employing **atomic conditional mutations** via MongoDB's `findOneAndUpdate`:

```mermaid
sequenceDiagram
    autonumber
    actor G1 as Guest 1 (0.000s)
    actor G2 as Guest 2 (0.001s)
    participant API as Slot Controller
    participant Svc as Slot Service
    participant DB as MongoDB Cluster
    participant Sock as Socket.io Server

    G1->>API: POST /api/v1/meetings (Slot #101)
    G2->>API: POST /api/v1/meetings (Slot #101)
    
    Note over Svc,DB: Atomic Test-and-Set Lock
    API->>Svc: lockSlot(slotId=101)
    Svc->>DB: findOneAndUpdate({ _id: 101, isBooked: false }, { $set: { isBooked: true } })
    
    alt Guest 1 Acquired Mutex
        DB-->>Svc: Returns Modified Document (Locked)
        Svc->>DB: Insert Meeting Record
        Svc->>Sock: Broadcast "slot:locked" to host room
        Sock-->>G2: UI instantly disables Slot #101
        Svc-->>API: 201 Created + Video Room URL
        API-->>G1: 201 Success Confirmation
    else Guest 2 Race Lost
        DB-->>Svc: Returns null (Condition Failed)
        Svc-->>API: 409 Conflict Error
        API-->>G2: 409 Conflict: "Slot already taken"
    end
```

```javascript
// backend/services/slotService.js (Atomic Lock Pattern)
const slot = await TimeSlot.findOneAndUpdate(
  { _id: slotId, isBooked: false },
  { $set: { isBooked: true } },
  { new: true }
);

if (!slot) {
  throw new AppError("This slot was secured by another attendee. Please choose another time.", 409);
}
```

---

### 🧠 Intelligent Multi-Signal Slot Recommendation Algorithm

Located in [`backend/services/aiSchedulerService.js`](file:///d:/hackproject/meeting%20schedule/hackhive-meeting-scheduler/backend/services/aiSchedulerService.js), HackHive features an analytical scheduling engine that ranks open slots using a multi-signal scoring model from **0 to 100**:

```
Score = Base (50) + S1(Proximity) + S2(Preferred) + S3(Peak Focus) + S4(Duration) - S5(Fatigue Buffer) - S6(Edge of Day)
```

| Signal | Evaluation Criteria | Scoring Weight |
| :--- | :--- | :--- |
| **S1: Proximity to Now** | Prioritizes sooner openings (Today: `+15`, Tomorrow: `+12`, Within 3 days: `+8`). | `+0 to +15 pts` |
| **S2: Preferred Host Hours** | Matches designated deep-work/call preference windows defined by host. | `+10 to +15 pts` |
| **S3: Cognitive Peak Sweetspot** | Centers around biological peak collaboration hours (`10:00 AM` & `2:30 PM`). | `+0 to +12 pts` |
| **S4: Duration Fit** | Rewards slots that match duration closely without leaving awkward 10-minute micro gaps. | `+4 to +8 pts` |
| **S5: Meeting Fatigue Penalty** | Detects if slot starts `< 15 minutes` after an existing meeting (protects mental health). | `-10 pts` |
| **S6: Edge-of-Day Penalty** | Discourages bookings before `08:00 AM` or after `06:00 PM` to protect personal boundaries. | `-5 to -15 pts` |

---

### 📡 Real-Time Socket State Engine

State synchronization across organizer and guest views is powered by targeted **Socket.io Rooms**, eliminating polling overhead and reducing client-server bandwidth by over 80%:

- `host_slots:<hostId>`: Delivers `slot:locked` and `slot:released` events so guests currently viewing a host's calendar see slots update live.
- `user:<userId>`: Broadcasts user notifications and dashboard badges.
- `meeting:<meetingId>`: Dispatches video room states, participant join/leave events, and live status changes.

---

### 🔐 Enterprise Security & Resilience

- **Anti-NoSQL Injection**: `express-mongo-sanitize` strips `$` and `.` operators from incoming payload keys.
- **Header Hardening**: `helmet` enforces strict HTTP Content-Security-Policy, HSTS, frameguard, and DNS prefetch controls.
- **Parameter Pollution Guard**: `hpp` protects query parsers from array manipulation exploits.
- **Abuse Prevention**: Rate-limited per IP using `express-rate-limit` with customizable windows for sensitive auth routes.
- **Aggregation Optimization**: Dashboard analytics utilize MongoDB `$facet` pipelines in [`analyticsService.js`](file:///d:/hackproject/meeting%20schedule/hackhive-meeting-scheduler/backend/services/analyticsService.js) to execute multi-dimensional count, status, and timeline aggregations in a single query roundtrip.

---

## 🛠️ Tech Stack Matrix

| Domain | Technology | Purpose |
| :--- | :--- | :--- |
| **Frontend Framework** | **React 19 + Vite** | High-performance reactive rendering with instant HMR |
| **3D & Visual Graphics**| **Three.js, React Three Fiber, GSAP** | Dynamic particle pillars, lighting effects, and canvas visuals |
| **UI Motion & Icons** | **Framer Motion, Lucide React** | Fluid page transitions, modal animations, and crisp iconography |
| **Backend Runtime** | **Node.js 18+ & Express.js** | Production-ready RESTful API gateway and controllers |
| **Database & Modeling**| **MongoDB Atlas & Mongoose** | Distributed document persistence with compound indexes |
| **In-Memory Cache** | **Redis / In-Memory Adapter** | High-throughput sub-10ms response caching for analytics |
| **Realtime Engine** | **Socket.io v4** | Bidirectional low-latency room-based event broadcasting |
| **Video Conferencing** | **Jitsi Meet API** | Embedded in-browser WebRTC video calls |
| **External APIs** | **Google Calendar API, Nodemailer** | Two-way calendar sync and automated email dispatch |
| **API Documentation** | **Swagger UI (`/api-docs`)** | Interactive OpenAPI 3.0 specification |
| **Testing Suite** | **Jest, Supertest, MongoMemoryServer** | Automated unit and integration testing |

---

## 📁 Repository Structure

```
.
├── README.md                                  # Dual-audience project documentation
├── system_architecture.md                     # Deep technical architecture specification
├── LICENSE                                    # Open-source MIT License
├── .gitignore                                 # Protection for keys, node_modules & build artifacts
│
└── hackhive-meeting-scheduler/
    ├── backend/                               # Express REST API & WebSocket Server
    │   ├── config/                            # Database connection, Redis & Swagger configuration
    │   ├── controllers/                       # HTTP request orchestration & validation
    │   ├── middleware/                        # Auth guards, security headers & error handlers
    │   ├── models/                            # Mongoose Schemas (User, Meeting, TimeSlot, Org)
    │   ├── routes/                            # Versioned API routes (/api/v1/...)
    │   ├── services/                          # Core business logic (AI Scheduler, Sockets, Analytics)
    │   ├── seeds/                             # Synthetic test dataset generator
    │   ├── scripts/                           # Database seeding CLI scripts
    │   ├── tests/                             # Automated test suites
    │   ├── server.js                          # Application bootstrap entry point
    │   └── package.json
    │
    └── frontend/frontend/lumina-scheduler/    # React 19 + Three.js Client
        ├── public/                            # Static assets and 3D frame sequences
        ├── src/
        │   ├── components/                    # Reusable 3D Canvas, Particles & UI components
        │   ├── context/                       # Authentication and global state providers
        │   ├── hooks/                         # Custom hooks (Auth, Sockets, Notifications)
        │   ├── pages/                         # Core views (Landing, Booking, Management, Video)
        │   ├── services/                      # Axios API client and Socket.io subscriptions
        │   └── App.jsx                        # React Router v7 navigation tree
        ├── package.json
        └── vite.config.js
```

---

## 🚀 Quickstart Guide

Follow these steps to run HackHive locally on your machine.

### Prerequisites
- **Node.js**: `v18.x` or higher installed ([Download Node.js](https://nodejs.org/))
- **MongoDB**: Local MongoDB instance or free cloud cluster on [MongoDB Atlas](https://www.mongodb.com/atlas)
- **Git**

---

### 1. Backend Setup

```bash
# Navigate to the backend directory
cd hackhive-meeting-scheduler/backend

# Install dependencies
npm install

# Create environment configuration
cp .env.example .env
```

Ensure your `.env` contains at least the required keys:
```env
PORT=5000
NODE_ENV=development
MONGO_URI=mongodb://localhost:27017/hackhive_scheduler
JWT_SECRET=super_secret_jwt_key_change_in_production
CLIENT_URL=http://localhost:5173
```

Start the backend API server:
```bash
npm run dev
```
> The API server boots on **`http://localhost:5000`**.  
> Explore interactive Swagger API documentation at: **`http://localhost:5000/api-docs`**

---

### 2. Frontend Setup

In a new terminal window:

```bash
# Navigate to the React application directory
cd hackhive-meeting-scheduler/frontend/frontend/lumina-scheduler

# Install frontend packages
npm install

# Start Vite development server
npm run dev
```
> The web application is now live at: **`http://localhost:5173`**

---

### 3. Instant Demo Data

Populate your database with realistic hosts, meetings, slots, and organization records with one command:

```bash
cd hackhive-meeting-scheduler/backend
npm run seed:demo
```

---

## 🔑 Instant Demo Credentials

Use these pre-seeded accounts to explore different roles inside the platform:

| Role | Email Address | Password | Permissions & Features |
| :--- | :--- | :--- | :--- |
| **👑 Admin** | `admin@gmail.com` | `Password123` | Platform oversight, analytics inspection, user & org management |
| **📅 Host (Organizer)** | `host@hackhive.demo` | `Password123` | Availability configuration, booking link sharing, meeting management |
| **👤 Member (Guest)** | `guest@hackhive.demo` | `Password123` | Book meetings, browse host availability, join video calls |

---

## 📡 API Reference Overview

The backend exposes a clean REST API under `/api/v1`:

| Method | Endpoint | Description | Access |
| :--- | :--- | :--- | :--- |
| `POST` | `/api/v1/auth/register` | Register new user account with timezone detection | Public |
| `POST` | `/api/v1/auth/login` | Authenticate user and receive JWT session bearer | Public |
| `GET` | `/api/v1/slots/available/:hostId` | Retrieve available conflict-free time slots for host | Public |
| `POST` | `/api/v1/meetings` | Atomically acquire slot and confirm meeting | Authenticated |
| `GET` | `/api/v1/meetings/my-meetings` | Fetch user’s upcoming and historical meetings | Authenticated |
| `PATCH` | `/api/v1/meetings/:id/cancel` | Cancel meeting, release slot, and notify attendees | Authenticated |
| `GET` | `/api/v1/analytics/overview` | Platform metrics (cached via in-memory TTL) | Admin |
| `GET` | `/api/v1/organizations` | List team workspaces and shared directories | Authenticated |

---

## 🧪 Running Automated Tests

Run the complete test suite verifying controllers, authentication guards, and the conflict-prevention booking engine:

```bash
cd hackhive-meeting-scheduler/backend
npm test
```

---

## 📄 License & Authors

Distributed under the **MIT License**. See [`LICENSE`](file:///d:/hackproject/meeting%20schedule/LICENSE) for complete details.

Built with ❤️ by **Vedant S Tattimani & HackHive Team**.
