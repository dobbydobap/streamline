# Streamify

<p align="center">
  <strong>Enterprise-grade real-time video conferencing and messaging platform</strong>
</p>

<p align="center">
  A full-stack communication solution built with the MERN stack, featuring real-time video calls, instant messaging, and collaborative tools for seamless remote communication.
</p>

---

## Overview

Streamify is a production-ready platform enabling teams to connect through high-quality video calls and real-time messaging. Built with modern web technologies and powered by Stream's infrastructure, it delivers enterprise-level performance with an intuitive user experience.

## Key Features

### Communication
- **Real-Time Messaging** - Instant chat with typing indicators, emoji reactions, threaded replies, and read receipts
- **HD Video Conferencing** - 1-on-1 and group calls with adaptive bitrate and noise suppression
- **Screen Sharing & Recording** - Share screens and record important conversations
- **Friend System** - Send, accept, and manage friend requests with real-time notifications

### User Experience
- **32 Premium Themes** - Extensive customization options with dark/light mode support
- **Responsive Design** - Optimized for desktop, tablet, and mobile devices
- **Progressive UI** - Skeleton screens, optimistic updates, and smooth loading states
- **Accessibility** - WCAG 2.1 compliant with keyboard navigation

### Security
- JWT-based authentication with HTTP-only cookies
- bcrypt password encryption and input sanitization
- Protected routes with server-side authorization
- Configurable CORS policies

---

## Technology Stack

**Frontend:** React 18, Vite, TailwindCSS, Stream SDKs, TanStack Query, Zustand, React Router

**Backend:** Node.js, Express, MongoDB, Mongoose, Stream APIs, JWT, bcryptjs

**Infrastructure:** Vercel (Frontend), Render (Backend), MongoDB Atlas (Database)

---

## Installation

### Prerequisites
- Node.js v16+ and npm v8+
- MongoDB Atlas account
- Stream account ([Sign up](https://getstream.io/))

### Setup

1. **Clone Repository**
```bash
git clone <your-repository-url>
cd Streamify
```

2. **Install Dependencies**
```bash
# Backend
cd backend && npm install

# Frontend
cd ../frontend && npm install
```

3. **Configure Environment Variables**

**Backend** (`backend/.env`):
```env
PORT=5001
NODE_ENV=development
MONGO_URI=mongodb+srv://<user>:<pass>@cluster.mongodb.net/streamify
STREAM_API_KEY=your_stream_api_key
STREAM_API_SECRET=your_stream_api_secret
JWT_SECRET_KEY=your_generated_secret
```

**Frontend** (`frontend/.env`):
```env
VITE_STREAM_API_KEY=your_stream_api_key
VITE_API_URL=http://localhost:5001
```

4. **Generate JWT Secret**
```bash
node -e "console.log(require('crypto').randomBytes(48).toString('hex'))"
```

5. **Run Application**
```bash
# Backend (runs on :5001)
cd backend && npm run dev

# Frontend (runs on :5173)
cd frontend && npm run dev
```

---

## Deployment

### Backend (Render)

1. Create new Web Service at [Render](https://render.com/)
2. Connect GitHub repository
3. Configure:
   - Root Directory: `backend`
   - Build Command: `npm install`
   - Start Command: `node src/server.js`
4. Add environment variables (same as local `.env`)
5. Deploy and copy the service URL

### Frontend (Vercel)

1. Import project at [Vercel](https://vercel.com/)
2. Configure:
   - Root Directory: `frontend`
   - Framework: `Vite`
   - Build Command: `npm run build`
   - Output Directory: `dist`
3. Add environment variables:
   ```
   VITE_STREAM_API_KEY=your_key
   VITE_API_URL=https://your-backend.onrender.com
   ```
4. Deploy

**Important:** Update backend CORS origin with your Vercel URL after deployment.

---

## API Reference

### Authentication

```http
POST   /api/auth/signup      # Register new user
POST   /api/auth/login       # User login
POST   /api/auth/logout      # User logout
GET    /api/auth/me          # Get current user
```

### Users

```http
GET    /api/users                        # Get all users
GET    /api/users/friend-requests        # Get friend requests
POST   /api/users/friend-request/:id     # Send friend request
POST   /api/users/accept-request/:id     # Accept friend request
POST   /api/users/reject-request/:id     # Reject friend request
```

### Chat

```http
GET    /api/chat/token       # Get Stream authentication token
```

---

## Project Structure

```
streamify/
├── backend/
│   ├── src/
│   │   ├── controllers/       # Request handlers
│   │   ├── middleware/        # Auth & validation
│   │   ├── models/            # Database schemas
│   │   ├── routes/            # API endpoints
│   │   ├── lib/               # Database & Stream config
│   │   └── server.js          # App entry point
│   └── package.json
│
├── frontend/
│   ├── src/
│   │   ├── components/        # Reusable UI components
│   │   ├── pages/             # Route pages
│   │   ├── hooks/             # Custom React hooks
│   │   ├── store/             # Global state management
│   │   ├── lib/               # API & utilities
│   │   └── App.jsx            # Main app component
│   └── package.json
│
└── README.md
```

---

## Troubleshooting

**MongoDB Connection Error**
- Add `0.0.0.0/0` to MongoDB Atlas Network Access whitelist

**CORS Error**
- Ensure backend CORS origin matches frontend URL exactly

**Stream API Error**
- Verify API keys match in both backend and frontend `.env` files

**JWT Authentication Error**
- Confirm JWT_SECRET_KEY is properly set in backend `.env`

**404 on Page Refresh (Vercel)**
- Ensure `vercel.json` with proper rewrites exists in frontend directory

---

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## Acknowledgments

- [Stream](https://getstream.io/) - Real-time communication infrastructure
- [MongoDB](https://www.mongodb.com/) - Database solution
- [Vercel](https://vercel.com/) & [Render](https://render.com/) - Hosting platforms
- [TailwindCSS](https://tailwindcss.com/) - Styling framework

---

<p align="center">
  <strong>Built with ❤️ for seamless communication</strong>
</p>

<p align="center">
  If you find this project helpful, please consider giving it a ⭐
</p>