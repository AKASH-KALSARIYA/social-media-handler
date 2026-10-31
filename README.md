<div align="center">

# 🌐 SocialEcho

### A Next-Generation Social Networking Platform

**AI-Powered Content Moderation** · **Context-Based Authentication** · **Community Management**

[![Node.js](https://img.shields.io/badge/Node.js-18+-339933?style=for-the-badge&logo=node.js&logoColor=white)](https://nodejs.org/)
[![React](https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://reactjs.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-6+-47A248?style=for-the-badge&logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![Express.js](https://img.shields.io/badge/Express.js-4.18-000000?style=for-the-badge&logo=express&logoColor=white)](https://expressjs.com/)
[![Flask](https://img.shields.io/badge/Flask-ML_Server-000000?style=for-the-badge&logo=flask&logoColor=white)](https://flask.palletsprojects.com/)
[![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-3.2-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=for-the-badge)](http://makeapullrequest.com)

[📺 Watch Demo](https://youtu.be/Tmncayg7FeU) · [🐛 Report Bug](https://github.com/AKASH-KALSARIYA/social-media-handler/issues) · [💡 Request Feature](https://github.com/AKASH-KALSARIYA/social-media-handler/issues)

</div>

---

<div align="center">

![SocialEcho Platform](https://raw.githubusercontent.com/nz-m/SocialEcho/main/resources/UI-community.png)

</div>

---

## 📑 Table of Contents

- [About The Project](#-about-the-project)
- [Key Features](#-key-features)
- [System Architecture](#-system-architecture)
- [Tech Stack](#-tech-stack)
- [Database Schema](#-database-schema)
- [Getting Started](#-getting-started)
- [Environment Variables](#-environment-variables)
- [API Endpoints](#-api-endpoints)
- [User Roles & Permissions](#-user-roles--permissions)
- [Content Moderation Pipeline](#-content-moderation-pipeline)
- [Context-Based Authentication](#-context-based-authentication)
- [Project Structure](#-project-structure)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🎯 About The Project

**SocialEcho** is a full-stack social networking platform built on the **MERN stack** (MongoDB, Express.js, React.js, Node.js) that goes beyond traditional social media platforms by integrating:

- 🤖 **AI-powered content moderation** using NLP models (Google Perspective API, TextRazor, Hugging Face BART) to automatically detect spam, toxicity, harassment, and categorize content
- 🔐 **Context-based authentication** that monitors login context (device, IP, geolocation) and alerts users of suspicious activity via email
- 👥 **Community-driven architecture** with role-based access control (Admin, Moderator, User)

> Built with scalability, security, and user experience at its core.

---

## ✨ Key Features

<table>
<tr>
<td width="50%">

### 🛡️ Security & Auth
- ✅ JWT-based authentication with refresh tokens
- ✅ Context-based login verification (IP, device, geo)
- ✅ AES-encrypted context data storage
- ✅ Suspicious login email alerts
- ✅ Device trust management
- ✅ Rate limiting protection

</td>
<td width="50%">

### 🤖 AI Content Moderation
- ✅ Spam & toxicity detection (Perspective API)
- ✅ Automated content categorization
- ✅ Multi-provider support (TextRazor / HuggingFace / Flask)
- ✅ Community-specific content filtering
- ✅ Manual post review system
- ✅ Admin-configurable API switching

</td>
</tr>
<tr>
<td width="50%">

### 👥 Social Features
- ✅ User profile creation & management
- ✅ Post creation with media uploads
- ✅ Commenting & liking system
- ✅ Follow/unfollow users
- ✅ Community-based content feeds
- ✅ Post saving & bookmarks

</td>
<td width="50%">

### ⚙️ Administration
- ✅ Admin dashboard with full control
- ✅ Moderator dashboard & assignment
- ✅ Community creation & management
- ✅ Content moderation API toggling
- ✅ User activity monitoring
- ✅ Post report management

</td>
</tr>
</table>

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                         CLIENT (Port 3000)                         │
│                    React 18 + Redux + Tailwind CSS                 │
└──────────────────────────────┬──────────────────────────────────────┘
                               │ REST API (HTTP/JSON)
                               ▼
┌─────────────────────────────────────────────────────────────────────┐
│                    PRIMARY SERVER (Port 4000)                       │
│                     Node.js + Express.js                            │
│                                                                     │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌────────────────────────┐ │
│  │  Auth    │ │  Posts   │ │Community │ │   Content Moderation   │ │
│  │ (JWT +   │ │  CRUD   │ │  Mgmt   │ │   Service Layer        │ │
│  │ Passport)│ │         │ │         │ │                        │ │
│  └──────────┘ └──────────┘ └──────────┘ └────────┬───────────────┘ │
└──────────┬──────────────────────────────────────┬─┼────────────────┘
           │                                      │ │
           ▼                                      │ ▼
┌─────────────────────┐                    ┌──────────────────────────┐
│     MongoDB         │                    │   External NLP APIs      │
│  (Mongoose ODM)     │                    │  • Perspective API       │
│                     │                    │  • TextRazor API         │
│  17 Collections     │                    │  • HuggingFace API       │
│  (Users, Posts,     │                    └──────────────────────────┘
│   Communities...)   │                           │ OR
└─────────────────────┘                           ▼
                                     ┌────────────────────────────────┐
                                     │  CLASSIFIER SERVER (Port 5000) │
                                     │     Python Flask + PyTorch     │
                                     │  facebook/bart-large-mnli      │
                                     │  (Self-hosted alternative)     │
                                     └────────────────────────────────┘
```

---

## 🛠️ Tech Stack

### Backend (Primary Server)

| Technology | Purpose |
|:---|:---|
| **Node.js** | JavaScript runtime |
| **Express.js** `v4.18` | Web framework & REST API |
| **MongoDB** + **Mongoose** `v6.9` | Database & ODM |
| **Passport.js** + **JWT** | Authentication & authorization |
| **bcrypt** | Password hashing |
| **crypto-js** | AES encryption for context data |
| **Nodemailer** | Email notifications |
| **Multer** | File upload handling |
| **Morgan** | HTTP request logging |
| **express-rate-limit** | API rate limiting |
| **geoip-lite** | IP geolocation lookup |
| **express-useragent** | Device/browser detection |
| **Axios** | HTTP client for external APIs |

### Backend (ML Classifier Server)

| Technology | Purpose |
|:---|:---|
| **Python** + **Flask** | ML API server |
| **Hugging Face Transformers** | NLP model pipeline |
| **PyTorch** | Deep learning framework |
| **BART Large MNLI** | Zero-shot text classification model |

### Frontend

| Technology | Purpose |
|:---|:---|
| **React** `v18` | UI library |
| **Redux Toolkit** | State management |
| **React Router** `v6` | Client-side routing |
| **Tailwind CSS** `v3.2` | Utility-first CSS framework |
| **Headless UI** | Accessible UI components |
| **Axios** | HTTP client |
| **jwt-decode** | Token decoding |
| **animate.css** | CSS animations |
| **react-helmet** | SEO meta management |

---

## 🗄️ Database Schema

The application uses **17 MongoDB collections** to manage all data:

<div align="center">

![Schema Diagram](https://raw.githubusercontent.com/nz-m/SocialEcho/main/resources/Schema-Diagram.png)

</div>

<details>
<summary><b>📋 Collection Overview (Click to expand)</b></summary>

| Collection | Description |
|:---|:---|
| `User` | User profiles, credentials, avatar, role, interests, followers/following |
| `Post` | User posts with content, media URL, community reference, likes, comments |
| `Comment` | Post comments linked to users and posts |
| `Community` | Communities with name, description, banner, members, moderators, rules |
| `Rule` | Community-specific content guidelines |
| `Report` | Flagged posts with reporter info and reason |
| `PendingPost` | Posts awaiting moderation review |
| `Token` | JWT access & refresh tokens with expiry |
| `AdminToken` | Separate token collection for admin sessions |
| `Admin` | Admin credentials and access data |
| `Context` | Encrypted login context (IP, device, browser, location) |
| `SuspiciousLogin` | Tracked suspicious login attempts and device info |
| `Email` | Email verification codes and metadata |
| `Log` | System event logs with context and severity |
| `Preference` | User preferences (e.g., context-based auth toggle) |
| `Relationship` | Follower/following relationship mapping |
| `Config` | Application-level configuration (API toggles, timeouts) |

</details>

---

## 🚀 Getting Started

### Prerequisites

| Requirement | Version |
|:---|:---|
| **Node.js** | `v18+` |
| **npm** | `v9+` |
| **MongoDB** | `v6+` (local) or MongoDB Atlas account |
| **Python** | `v3.8+` *(optional, for Flask classifier)* |

### Installation

**1. Clone the repository**

```bash
git clone https://github.com/AKASH-KALSARIYA/social-media-handler.git
cd social-media-handler/SocialEcho-main
```

**2. Install server dependencies**

```bash
cd server
npm install
```

**3. Install client dependencies**

```bash
cd ../client
npm install
```

**4. Configure environment variables**

Create `.env` files in both `server/` and `client/` directories based on the `.env.example` files. See [Environment Variables](#-environment-variables) for details.

**5. Initial Admin Setup**

```bash
cd ../server
chmod +x admin_tool.sh
./admin_tool.sh
```

**6. Start the application**

```bash
# Terminal 1 — Start the backend server
cd server
npm start
# ✅ Server runs on http://localhost:4000

# Terminal 2 — Start the frontend
cd client
npm start
# ✅ Client runs on http://localhost:3000
```

**7. (Optional) Start the ML Classifier Server**

```bash
cd classifier_server
pip install -r requirements.txt
python classifier_api.py
# ✅ Flask classifier runs on http://localhost:5000
```

---

## 🔑 Environment Variables

### Server (`server/.env`)

```env
# ─── Core ──────────────────────────────────────────
CLIENT_URL=http://localhost:3000
MONGODB_URI=mongodb://127.0.0.1:27017/db_socialecho
PORT=4000

# ─── Authentication ───────────────────────────────
SECRET=your_jwt_secret_key
REFRESH_SECRET=your_jwt_refresh_secret_key

# ─── Encryption ───────────────────────────────────
CRYPTO_KEY=your_aes_encryption_key

# ─── Email Service ────────────────────────────────
EMAIL=your_email@example.com
PASSWORD=your_email_password
EMAIL_SERVICE=Gmail                    # Gmail / Zoho / others

# ─── Content Moderation APIs ─────────────────────
PERSPECTIVE_API_KEY=your_key           # Google Perspective API
TEXTRAZOR_API_KEY=your_key             # TextRazor API
INTERFACE_API_KEY=your_key             # Hugging Face Inference API

PERSPECTIVE_API_DISCOVERY_URL=https://commentanalyzer.googleapis.com/$discovery/rest?version=v1alpha1
TEXTRAZOR_API_URL=https://api.textrazor.com/
INTERFACE_API_URL=https://api-inference.huggingface.co/models/facebook/bart-large-mnli

# ─── Self-hosted Classifier (Optional) ───────────
CLASSIFIER_API_URL=http://127.0.0.1:5000/classify
```

### Client (`client/.env`)

```env
REACT_APP_API_URL=http://127.0.0.1:4000
```

<details>
<summary><b>🔗 API Key Resources (Click to expand)</b></summary>

| API | Get Your Key |
|:---|:---|
| **Google Perspective API** | [developers.perspectiveapi.com](https://developers.perspectiveapi.com/s/docs-get-started) |
| **TextRazor API** | [textrazor.com](https://www.textrazor.com/) |
| **Hugging Face Inference API** | [huggingface.co](https://huggingface.co/facebook/bart-large-mnli) |

> **Note:** Content moderation and context-based authentication configurations are **optional**. The platform will function without them, but those features will be disabled.

</details>

---

## 📡 API Endpoints

### Authentication

| Method | Endpoint | Description |
|:---|:---|:---|
| `POST` | `/auth/register` | Register a new user |
| `POST` | `/auth/login` | User login with context capture |
| `POST` | `/auth/refresh` | Refresh access token |
| `POST` | `/auth/logout` | User logout |

### Users

| Method | Endpoint | Description |
|:---|:---|:---|
| `GET` | `/users/profile/:id` | Get user profile |
| `PUT` | `/users/profile` | Update user profile |
| `POST` | `/users/follow/:id` | Follow a user |
| `POST` | `/users/unfollow/:id` | Unfollow a user |

### Posts

| Method | Endpoint | Description |
|:---|:---|:---|
| `GET` | `/posts` | Get all posts |
| `POST` | `/posts` | Create a new post |
| `PUT` | `/posts/:id/like` | Like/unlike a post |
| `POST` | `/posts/:id/comment` | Comment on a post |
| `POST` | `/posts/:id/report` | Report a post |

### Communities

| Method | Endpoint | Description |
|:---|:---|:---|
| `GET` | `/communities` | Get all communities |
| `POST` | `/communities/:id/join` | Join a community |
| `POST` | `/communities/:id/leave` | Leave a community |

### Admin

| Method | Endpoint | Description |
|:---|:---|:---|
| `GET` | `/admin/dashboard` | Admin dashboard data |
| `POST` | `/admin/moderators` | Manage moderators |
| `PUT` | `/admin/config` | Update moderation config |

---

## 👥 User Roles & Permissions

| Role | Capabilities |
|:---|:---|
| 🔴 **Admin** | Full system access — manage moderators, communities, toggle content moderation APIs, monitor user activity, review reports |
| 🟡 **Moderator** | Manage assigned communities, manually review reported/pending posts, moderate community content. *Auto-assigned when registering with `@mod.socialecho.com` email* |
| 🟢 **General User** | Create posts, comment, like, follow/unfollow, join communities, report posts, manage trusted devices |

---

## 🤖 Content Moderation Pipeline

```
              ┌─────────────────────┐
              │  User Submits Post  │
              └──────────┬──────────┘
                         ▼
              ┌─────────────────────┐
              │  Perspective API    │
              │  ┌───────────────┐  │
              │  │ Spam Check    │  │
              │  │ Toxicity      │  │
              │  │ Harassment    │  │
              │  │ Profanity     │  │
              │  └───────────────┘  │
              └──────────┬──────────┘
                         │
                   Pass? │
              ┌────NO────┼────YES────┐
              ▼                      ▼
     ┌────────────────┐    ┌──────────────────┐
     │  Post Rejected │    │   Categorization  │
     └────────────────┘    │  (1 of 3 options) │
                           │                    │
                           │ • TextRazor API    │
                           │ • HuggingFace API  │
                           │ • Flask Classifier │
                           └────────┬───────────┘
                                    │
                              Match? │
                     ┌────NO────────┼──YES──────┐
                     ▼                          ▼
           ┌───────────────────┐     ┌───────────────────┐
           │ Flagged / Pending │     │  Post Published   │
           │   Manual Review   │     │  ✅ Approved      │
           └───────────────────┘     └───────────────────┘
```

The moderation system supports **3 interchangeable categorization providers**, switchable from the admin dashboard without any code changes.

---

## 🔐 Context-Based Authentication

SocialEcho enhances security by analyzing login context:

| Data Captured | Technology Used |
|:---|:---|
| **IP Address** | `request-ip` |
| **Geolocation** (country, city) | `geoip-lite` |
| **Browser & OS** | `express-useragent` |
| **Device Type** | `express-useragent` |

**Security Flow:**
1. On login, the system captures and **encrypts** (AES via `crypto-js`) the user's context
2. Compares with previously stored trusted contexts
3. If a **new/unrecognized context** is detected → sends **email alert** via Nodemailer
4. User must **verify identity** before the new device is trusted
5. Users can **manage trusted devices** from their profile settings

---

## 📂 Project Structure

```
SocialEcho-main/
│
├── 📁 client/                        # ⚛️ React Frontend
│   ├── 📁 src/
│   │   ├── App.jsx                   # Root component
│   │   ├── AppContainer.jsx          # Layout wrapper
│   │   ├── PrivateRoute.jsx          # Auth guard
│   │   ├── routes.js                 # Route definitions
│   │   ├── index.css                 # Global styles
│   │   ├── 📁 components/            # Reusable UI components
│   │   ├── 📁 pages/                 # Page components
│   │   ├── 📁 redux/                 # Store, slices & thunks
│   │   ├── 📁 hooks/                 # Custom hooks
│   │   ├── 📁 middlewares/           # Client middlewares
│   │   ├── 📁 utils/                 # Utility helpers
│   │   └── 📁 assets/               # Static assets
│   ├── .env.example
│   ├── tailwind.config.js
│   └── package.json
│
├── 📁 server/                        # 🟢 Node.js Backend
│   ├── app.js                        # Entry point
│   ├── 📁 config/
│   │   ├── database.js               # MongoDB connection
│   │   └── passport.js               # JWT strategy
│   ├── 📁 controllers/               # Request handlers (7 files)
│   ├── 📁 models/                    # Mongoose schemas (17 models)
│   ├── 📁 routes/                    # API routes (5 files)
│   ├── 📁 services/                  # Business logic (5 files)
│   ├── 📁 middlewares/               # Auth, rate-limit, logging
│   ├── 📁 utils/                     # Helper utilities
│   ├── admin_tool.sh                 # Admin setup CLI
│   ├── .env.example
│   └── package.json
│
├── 📁 classifier_server/             # 🐍 Flask ML Server
│   ├── classifier_api.py             # Flask API + BART model
│   ├── Dockerfile                    # Docker support
│   ├── requirements.txt
│   └── Readme.md
│
├── 📁 resources/                     # 📸 Screenshots & diagrams
│   ├── UI-community.png
│   └── Schema-Diagram.png
│
├── LICENSE                           # MIT License
└── README.md                         # You are here 📍
```

---

## 🤝 Contributing

Contributions make the open-source community an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. **Fork** the repository
2. **Create** your feature branch (`git checkout -b feature/amazing-feature`)
3. **Commit** your changes (`git commit -m 'Add some amazing feature'`)
4. **Push** to the branch (`git push origin feature/amazing-feature`)
5. **Open** a Pull Request

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

<div align="center">

**Built with ❤️ using the MERN Stack**

[![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![Express.js](https://img.shields.io/badge/Express.js-000000?style=flat-square&logo=express&logoColor=white)](https://expressjs.com/)
[![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)](https://reactjs.org/)
[![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=node.js&logoColor=white)](https://nodejs.org/)

⭐ **Star this repo if you find it helpful!** ⭐

</div>
