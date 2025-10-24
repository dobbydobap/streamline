<h1 align="center">🎥 Streamify - Real-Time Video Calls & Chat Application</h1>

<p align="center">
  <strong>A full-stack video calling and messaging platform built with the MERN stack</strong>
</p>

<p align="center">
  <a href="#-features">Features</a> •
  <a href="#-tech-stack">Tech Stack</a> •
  <a href="#-getting-started">Getting Started</a> •
  <a href="#-deployment">Deployment</a> •
  <a href="#-api-documentation">API Documentation</a>
</p>

---

## ✨ Features

### 🎯 Core Functionality
- **Real-Time Messaging**: Instant chat with live typing indicators, emoji reactions to messages, threaded replies, and read receipts
- **Video & Audio Calls**: High-quality 1-on-1 and group video calls powered by Stream
- **Screen Sharing**: Share your screen during video calls
- **Call Recording**: Record and save important video conversations
- **Friend System**: Send, accept, and manage friend requests
- **User Profiles**: Customizable user profiles with avatars
- **Notifications**: Real-time notifications for messages, calls, and friend requests

### 🎨 User Experience
- **32 Unique Themes**: Customize your interface with a variety of beautiful themes
- **Responsive Design**: Seamless experience across desktop, tablet, and mobile devices
- **Dark/Light Mode**: Toggle between dark and light themes
- **Loading States**: Smooth loading animations and skeleton screens
- **Error Handling**: User-friendly error messages and fallbacks

### 🔐 Security & Authentication
- **JWT Authentication**: Secure token-based authentication
- **Protected Routes**: Client and server-side route protection
- **HTTP-Only Cookies**: Secure session management
- **Password Hashing**: bcrypt encryption for user passwords
- **CORS Configuration**: Proper cross-origin resource sharing setup

### 🚀 Performance & Scalability
- **TanStack Query**: Efficient data fetching, caching, and synchronization
- **Zustand State Management**: Lightweight and performant global state
- **Stream SDK**: Enterprise-grade real-time infrastructure
- **MongoDB Atlas**: Cloud database with automatic scaling
- **Optimized Builds**: Code splitting and lazy loading

---

## 🛠️ Tech Stack

### Frontend
- **React 18** - UI library with hooks and modern features
- **Vite** - Lightning-fast build tool and dev server
- **TailwindCSS** - Utility-first CSS framework
- **Stream Chat React** - Real-time chat SDK
- **Stream Video React** - Real-time video SDK
- **TanStack Query (React Query)** - Server state management
- **Zustand** - Lightweight state management
- **React Router** - Client-side routing
- **React Hot Toast** - Beautiful notifications
- **Axios** - HTTP client

### Backend
- **Node.js** - JavaScript runtime
- **Express.js** - Web application framework
- **MongoDB** - NoSQL database
- **Mongoose** - MongoDB object modeling
- **Stream Chat & Video** - Real-time communication APIs
- **JWT** - JSON Web Tokens for authentication
- **bcryptjs** - Password hashing
- **cookie-parser** - Cookie parsing middleware
- **CORS** - Cross-origin resource sharing

### DevOps & Deployment
- **Vercel** - Frontend hosting
- **Render** - Backend hosting
- **MongoDB Atlas** - Database hosting
- **Git & GitHub** - Version control

---

## 🚀 Getting Started

### Prerequisites

Before you begin, ensure you have the following installed:
- **Node.js** (v16 or higher) - [Download](https://nodejs.org/)
- **npm** or **yarn** - Package manager
- **MongoDB Atlas Account** - [Sign up](https://www.mongodb.com/cloud/atlas)
- **Stream Account** - [Sign up](https://getstream.io/)

### Installation

#### 1. Clone the Repository

```bash
git clone https://github.com/Astro-Dude/Streamify.git
cd Streamify
```

#### 2. Install Dependencies

**Backend:**
```bash
cd backend
npm install
```

**Frontend:**
```bash
cd frontend
npm install
```

#### 3. Environment Variables Setup

Create `.env` files in both backend and frontend directories:

**Backend `.env` (`/backend/.env`):**
```env
# Server Configuration
PORT=5001
NODE_ENV=development

# MongoDB Database
MONGO_URI=mongodb+srv://your_username:your_password@cluster.mongodb.net/?retryWrites=true&w=majority

# Stream Chat & Video API (Get from https://getstream.io/)
STREAM_API_KEY=your_stream_api_key
STREAM_API_SECRET=your_stream_api_secret

# JWT Authentication (Generate with: node -e "console.log(require('crypto').randomBytes(48).toString('hex'))")
JWT_SECRET_KEY=your_generated_jwt_secret_key_here
```

**Frontend `.env` (`/frontend/.env`):**
```env
# Stream Chat & Video API Key
VITE_STREAM_API_KEY=your_stream_api_key

# Backend API URL
VITE_API_URL=http://localhost:5001
```

#### 4. Get Your API Keys

**MongoDB Atlas:**
1. Go to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Create a cluster (free tier available)
3. Go to Database Access → Add Database User
4. Go to Network Access → Add IP Address (add `0.0.0.0/0` for development)
5. Go to Clusters → Connect → Connect your application
6. Copy the connection string and replace `<password>` with your database user password

**Stream:**
1. Go to [GetStream.io](https://getstream.io/)
2. Sign up for a free account
3. Create a new app
4. Copy the API Key and API Secret from your dashboard

**JWT Secret:**
Generate a secure random string:
```bash
node -e "console.log(require('crypto').randomBytes(48).toString('hex'))"
```

#### 5. Run the Application

**Start Backend Server:**
```bash
cd backend
npm run dev
```
Backend will run on `http://localhost:5001`

**Start Frontend Development Server:**
```bash
cd frontend
npm run dev
```
Frontend will run on `http://localhost:5173`

#### 6. Open in Browser

Navigate to `http://localhost:5173` to see the application in action!

---

## 🌐 Deployment

### Backend Deployment (Render)

1. **Create a Render Account**: [Sign up at Render](https://render.com/)

2. **Create a New Web Service**:
   - Connect your GitHub repository
   - Select the repository: `Streamify`
   - Root Directory: `backend`
   - Build Command: `npm install`
   - Start Command: `node src/server.js`

3. **Environment Variables**:
   Add these in Render's Environment Variables section:
   ```
   NODE_ENV=production
   PORT=10000
   JWT_SECRET_KEY=your_jwt_secret_key
   STREAM_API_KEY=your_stream_api_key
   STREAM_API_SECRET=your_stream_api_secret
   MONGO_URI=your_mongodb_connection_string
   ```

4. **Deploy**: Click "Create Web Service"

5. **Get Your Backend URL**: Copy the URL (e.g., `https://streamify-xxx.onrender.com`)

### Frontend Deployment (Vercel)

1. **Create a Vercel Account**: [Sign up at Vercel](https://vercel.com/)

2. **Import Project**:
   - Click "Add New" → "Project"
   - Import your GitHub repository
   - Root Directory: `frontend`
   - Framework Preset: `Vite`
   - Build Command: `npm run build`
   - Output Directory: `dist`

3. **Environment Variables**:
   Add these in Vercel's Environment Variables section:
   ```
   VITE_STREAM_API_KEY=your_stream_api_key
   VITE_API_URL=https://your-render-backend-url.onrender.com
   ```

4. **Deploy**: Click "Deploy"

5. **Update Backend CORS**:
   After deployment, update your backend `server.js` CORS origin to your Vercel URL

### MongoDB Atlas Setup for Production

1. **Network Access**:
   - Go to Network Access in MongoDB Atlas
   - Add IP Address: `0.0.0.0/0` (allows all IPs)
   - Or add specific Render IP addresses

2. **Database User**:
   - Ensure your database user has proper read/write permissions

---

## � API Documentation

### Authentication Endpoints

#### Sign Up
```http
POST /api/auth/signup
Content-Type: application/json

{
  "email": "user@example.com",
  "password": "password123",
  "fullName": "John Doe"
}
```

#### Login
```http
POST /api/auth/login
Content-Type: application/json

{
  "email": "user@example.com",
  "password": "password123"
}
```

#### Logout
```http
POST /api/auth/logout
```

#### Get Authenticated User
```http
GET /api/auth/me
```

### User Endpoints

#### Get All Users
```http
GET /api/users
```

#### Get Friend Requests
```http
GET /api/users/friend-requests
```

#### Send Friend Request
```http
POST /api/users/friend-request/:userId
```

#### Accept Friend Request
```http
POST /api/users/accept-request/:requestId
```

#### Reject Friend Request
```http
POST /api/users/reject-request/:requestId
```

### Chat Endpoints

#### Get Stream Token
```http
GET /api/chat/token
```

---

## 📁 Project Structure

```
streamify-video-calls-master/
├── backend/
│   ├── src/
│   │   ├── controllers/
│   │   │   ├── auth.controller.js
│   │   │   ├── chat.controller.js
│   │   │   └── user.controller.js
│   │   ├── lib/
│   │   │   ├── db.js
│   │   │   └── stream.js
│   │   ├── middleware/
│   │   │   └── auth.middleware.js
│   │   ├── models/
│   │   │   ├── FriendRequest.js
│   │   │   └── User.js
│   │   ├── routes/
│   │   │   ├── auth.route.js
│   │   │   ├── chat.route.js
│   │   │   └── user.route.js
│   │   └── server.js
│   ├── .env
│   └── package.json
│
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── CallButton.jsx
│   │   │   ├── ChatLoader.jsx
│   │   │   ├── FriendCard.jsx
│   │   │   ├── Layout.jsx
│   │   │   ├── Navbar.jsx
│   │   │   ├── NoFriendsFound.jsx
│   │   │   ├── NoNotificationsFound.jsx
│   │   │   ├── PageLoader.jsx
│   │   │   ├── Sidebar.jsx
│   │   │   └── ThemeSelector.jsx
│   │   ├── constants/
│   │   │   └── index.js
│   │   ├── hooks/
│   │   │   ├── useAuthUser.js
│   │   │   ├── useLogin.js
│   │   │   ├── useLogout.js
│   │   │   └── useSignUp.js
│   │   ├── lib/
│   │   │   ├── api.js
│   │   │   ├── axios.js
│   │   │   └── utils.js
│   │   ├── pages/
│   │   │   ├── CallPage.jsx
│   │   │   ├── ChatPage.jsx
│   │   │   ├── HomePage.jsx
│   │   │   ├── LoginPage.jsx
│   │   │   ├── NotificationsPage.jsx
│   │   │   ├── OnboardingPage.jsx
│   │   │   └── SignUpPage.jsx
│   │   ├── store/
│   │   │   └── useThemeStore.js
│   │   ├── App.jsx
│   │   ├── index.css
│   │   └── main.jsx
│   ├── .env
│   ├── vercel.json
│   ├── vite.config.js
│   └── package.json
│
└── README.md
```

---

## 🔧 Development

### Available Scripts

**Backend:**
- `npm run dev` - Start development server with nodemon
- `npm start` - Start production server

**Frontend:**
- `npm run dev` - Start Vite development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build locally

### Code Style

This project uses:
- **ESLint** for JavaScript linting
- **Prettier** for code formatting (optional)

---

## � Troubleshooting

### Common Issues

**1. MongoDB Connection Error:**
```
Error: MongooseServerSelectionError: Could not connect to any servers
```
**Solution**: Add `0.0.0.0/0` to MongoDB Atlas Network Access whitelist

**2. CORS Error:**
```
Access to XMLHttpRequest blocked by CORS policy
```
**Solution**: Update backend CORS origin to match your frontend URL

**3. Stream API Error:**
```
Error: api_key not valid
```
**Solution**: Verify `STREAM_API_KEY` matches between backend and frontend `.env` files

**4. JWT Authentication Error:**
```
Error: jwt malformed
```
**Solution**: Ensure `JWT_SECRET_KEY` is set and is a strong random string

**5. 404 on Page Refresh (Vercel):**
**Solution**: Ensure `vercel.json` is present in the frontend directory with proper rewrites

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📝 License

This project is open source and available under the [MIT License](LICENSE).

---

## 👨‍💻 Author

**Astro-Dude**
- GitHub: [@Astro-Dude](https://github.com/Astro-Dude)

---

## 🙏 Acknowledgments

- [Stream](https://getstream.io/) - For providing the real-time chat and video infrastructure
- [MongoDB](https://www.mongodb.com/) - For the database solution
- [Vercel](https://vercel.com/) - For frontend hosting
- [Render](https://render.com/) - For backend hosting
- [TailwindCSS](https://tailwindcss.com/) - For the styling framework

---

## 📸 Screenshots

### Home Page
![Home Page](https://via.placeholder.com/800x400?text=Add+Your+Screenshot)

### Chat Interface
![Chat Interface](https://via.placeholder.com/800x400?text=Add+Your+Screenshot)

### Video Call
![Video Call](https://via.placeholder.com/800x400?text=Add+Your+Screenshot)

### Theme Selector
![Theme Selector](https://via.placeholder.com/800x400?text=Add+Your+Screenshot)

---

<p align="center">
  Made with ❤️ by <a href="https://github.com/Astro-Dude">Astro-Dude</a>
</p>

<p align="center">
  <strong>⭐ Star this repository if you find it helpful!</strong>
</p>
