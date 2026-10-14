# ⬡ VENOMX — Cyber Security Console

A full-stack **cybersecurity-themed web application** with an animated glitch-style UI, Matrix rain background, 4 interactive security tools, and a complete user profile system backed by a **Node.js + Express + MongoDB** API with JWT authentication.

![Tech](https://img.shields.io/badge/Stack-MERN-green) ![License](https://img.shields.io/badge/License-MIT-blue)

---

## ✨ Features

### 🖥️ Frontend (Animated Cyber Console)
- **Glitch-effect VENOMX title** with RGB-split animation & flicker
- **Matrix rain background** (canvas) + CRT scanlines + floating orbs
- **Animated hamburger menu** morphing into ✕ with slide-in security tools
- **Live threat ticker** — scrolling simulated alerts
- **4 Security Tools** (terminal-style simulated scans):
  | Tool | Description |
  |---|---|
  | 🔍 Scan System | Deep scan with live progress logs |
  | 🛡️ Security Level | Animated protection score (0–100) with verdict |
  | ✅ Antivirus Validity | Verify genuine vs fake antivirus |
  | ⚠️ Malicious Patterns | Detect & neutralize intrusion attempts |
- **"How it works" + Cybersecurity Awareness** sections with scroll-reveal animations
- **My Profile** — photo upload, personal details, bio (saved to database)

### ⚙️ Backend (REST API)
- User **register/login** with bcrypt-hashed passwords
- **JWT authentication** (7-day tokens)
- **Profile CRUD** — fetch & update name, username, phone, bio, photo
- CORS-protected, environment-based config

> ⚠️ **Disclaimer:** The security scans are realistic *simulations* running in the browser — a web page cannot scan a real system. They demonstrate UI/UX for a security console.

---

## 🧰 Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML5, CSS3, Vanilla JavaScript |
| Backend | Node.js, Express |
| Database | MongoDB (Mongoose) |
| Auth | JSON Web Tokens (JWT) + bcryptjs |
| Tools | nodemon, dotenv, cors |

---

## 📁 Project Structure

```
project/
├── backend/
│   ├── server.js           # Entry point
│   ├── .env                # Secrets (not committed)
│   ├── models/
│   │   └── User.js         # Mongoose user schema
│   ├── routes/
│   │   ├── auth.js         # Register / Login
│   │   └── profile.js      # Get / Update profile
│   ├── middleware/
│   │   └── auth.js         # JWT verifier
│   └── package.json
│
├── frontend/
│   └── index.html          # Complete single-page app
│
└── README.md
```

---

## 🚀 Getting Started

### 1️⃣ Clone the repository

```bash
git clone https://github.com/your-username/venomx.git
cd venomx
```

### 2️⃣ Backend setup

```bash
cd backend
npm install
```

Create a `.env` file inside `backend/`:

```env
PORT=5000
MONGO_URI=mongodb://127.0.0.1:27017/venomx
JWT_SECRET=your_very_long_random_secret_here
CLIENT_URL=http://localhost:5500
```

> 💡 Generate a strong secret: `node -e "console.log(require('crypto').randomBytes(48).toString('hex'))"`
>
> ☁️ No local MongoDB? Use [MongoDB Atlas](https://www.mongodb.com/atlas) (free) and paste its connection string as `MONGO_URI`.

Start the server:

```bash
npm run dev
```

✅ Expected output: `Server running on port 5000`

### 3️⃣ Frontend setup

The frontend must run on **port 5500** (matches `CLIENT_URL`):

- Open the project in **VS Code**
- Right-click `frontend/index.html` → **Open with Live Server**

### 4️⃣ Test it

| URL | Result |
|---|---|
| `http://localhost:5000/api/status` | `{"status":"VENOMX backend online"}` |
| `http://localhost:5500` | Website opens → Login/Register modal |

Register an account → fill your profile → save → data persists in MongoDB. 🎉

---

## 🔌 API Reference

Base URL: `http://localhost:5000/api`

| Method | Endpoint | Auth | Description |
|---|---|---|---|
| GET | `/status` | — | Health check |
| POST | `/auth/register` | — | Create account → returns JWT |
| POST | `/auth/login` | — | Login → returns JWT |
| GET | `/profile/me` | Bearer | Get current user profile |
| PUT | `/profile/update` | Bearer | Update profile + photo |

**Auth header:** `Authorization: Bearer <token>`

---

## 🔐 Security Notes

- Passwords are **bcrypt-hashed** (never stored in plain text)
- `.env` is **git-ignored** — never commit secrets
- JWT secret must be long & random in production
- For production, serve the frontend via the same Express app or a proper host (Render / Vercel) and update `CLIENT_URL`

---

## 📜 License

MIT — free to use, modify & learn from.

---

<p align="center">Stay alert. Stay encrypted. Stay secure. ⬡</p>
