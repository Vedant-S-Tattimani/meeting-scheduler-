# ⚡ HackHive (Lumina) — Intelligent Meeting Scheduler

<div align="center">

> **The next-generation, conflict-free scheduling and collaboration platform. Featuring atomic booking integrity, smart slot recommendations, interactive 3D visual experiences, instant video rooms, and real-time state synchronization.**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](../../LICENSE)
[![React 19](https://img.shields.io/badge/Frontend-React%2019%20%2B%20Vite-61dafb.svg)](https://react.dev/)
[![Three.js](https://img.shields.io/badge/3D%20Graphics-Three.js%20%2F%20Fiber-black.svg)](https://threejs.org/)
[![Node.js](https://img.shields.io/badge/Backend-Node.js%20%2B%20Express-339933.svg)](https://nodejs.org/)
[![Socket.io](https://img.shields.io/badge/Realtime-Socket.io%20v4-010101.svg)](https://socket.io/)
[![MongoDB](https://img.shields.io/badge/Database-MongoDB%20Atlas-47A248.svg)](https://www.mongodb.com/)

</div>

---

## 🌟 Quick Overview for Everyone

HackHive is an intelligent meeting scheduling platform designed to eliminate the back-and-forth of setting up meetings.

- **🛡️ 100% Conflict-Proof**: Guaranteed zero double bookings using atomic database locks.
- **🌍 Auto-Timezone**: Seamlessly converts times across participants worldwide.
- **📹 1-Click Video Calls**: Integrated in-app video conferencing powered by Jitsi Meet.
- **🏢 Team & Organization Workspaces**: Department-level scheduling and directory hubs.
- **🎨 3D Interactive UI**: Built with React 19, Three.js, React Three Fiber, and Framer Motion.

---

## ⚙️ For Developers & Architects

- **Atomic Locking**: MongoDB `findOneAndUpdate({ _id: slotId, isBooked: false })` prevents concurrent race conditions.
- **AI Recommendation Engine**: Multi-signal scoring (0-100) factoring in proximity, host preferences, biological peak hours, and buffer times.
- **Real-Time WebSockets**: Targeted Socket.io room broadcasts (`host_slots:<id>`, `user:<id>`, `meeting:<id>`).
- **Enterprise Security**: Helmet, Express Rate Limiting, Mongo Sanitize, HPP, JWT validation.

For the full architectural specification, see the root [`README.md`](../../README.md) and [`system_architecture.md`](../../system_architecture.md).

---

## 🚀 Quick Setup

### 1. Backend
```bash
cd backend
npm install
cp .env.example .env
npm run dev
```

### 2. Frontend
```bash
cd ../frontend/frontend/lumina-scheduler
npm install
npm run dev
```

### 3. Demo Credentials (`npm run seed:demo`)
- **Admin**: `admin@gmail.com` | `Password123`
- **Host**: `host@hackhive.demo` | `Password123`
- **Guest**: `guest@hackhive.demo` | `Password123`
