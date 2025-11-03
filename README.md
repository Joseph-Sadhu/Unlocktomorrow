# 🎓 Learning Management System (LMS)

## Bronze Level: User Registration & Login with Database Integration

[![Node.js](https://img.shields.io/badge/Node.js-v14+-green.svg)](https://nodejs.org/)
[![Express](https://img.shields.io/badge/Express-v4.18-blue.svg)](https://expressjs.com/)
[![MongoDB](https://img.shields.io/badge/MongoDB-v4.4+-success.svg)](https://www.mongodb.com/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

A complete, production-ready Learning Management System with secure authentication, implementing Bronze Level requirements with full frontend and backend integration.

---

## ✨ Features

### ✅ Implemented (Bronze Level)

- **User Registration**
  - Register with name, email, password, and role (Student/Teacher)
  - Email uniqueness validation
  - Password strength requirements
  - Role-based account creation
  
- **User Authentication**
  - Secure login with email and password
  - JWT token-based authentication
  - Session management
  - Auto-redirect for authenticated users
  
- **Data Security**
  - Password hashing with bcrypt (10 salt rounds)
  - JWT token expiration (7 days)
  - MongoDB database persistence
  - Protected API routes
  - CORS security

- **User Interface**
  - Beautiful animated gradient design
  - Glassmorphism effects
  - Responsive layout
  - Loading states
  - Success/error notifications
  - Form validation feedback

---

## 🚀 Quick Start

### Prerequisites
- Node.js (v14 or higher)
- MongoDB (local or Atlas)
- Modern web browser

### Installation

```bash
# 1. Install backend dependencies
cd backend
npm install

# 2. Start MongoDB (if using local)
mongod

# 3. Start backend server
npm run dev

# 4. Open frontend
# Open frontend/index.html in browser
# Or serve on http://localhost:3000
```

**That's it!** Your LMS is now running! 🎉

---

## 📚 Documentation

| Document | Description |
|----------|-------------|
| **[START_HERE.md](START_HERE.md)** | 🚀 Quick start guide (3 steps) |
| **[INSTALLATION_GUIDE.md](INSTALLATION_GUIDE.md)** | 📖 Complete setup instructions |
| **[README_BACKEND.md](README_BACKEND.md)** | 🔧 Backend API documentation |
| **[ARCHITECTURE.md](ARCHITECTURE.md)** | 🏗️ System architecture & design |
| **[PROJECT_SUMMARY.md](PROJECT_SUMMARY.md)** | 📊 Complete project overview |
| **[PROJECT_STRUCTURE.md](PROJECT_STRUCTURE.md)** | 📂 File structure guide |

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────┐
│                     Frontend (Client)                   │
│  - HTML/CSS/JavaScript                                  │
│  - Form validation                                      │
│  - API communication                                    │
│  - LocalStorage management                             │
└────────────────────┬────────────────────────────────────┘
                     │ HTTPS/JSON
                     ↓
┌─────────────────────────────────────────────────────────┐
│                   Backend (Server)                      │
│  - Express.js REST API                                  │
│  - JWT authentication                                   │
│  - Input validation                                     │
│  - Password hashing                                     │
└────────────────────┬────────────────────────────────────┘
                     │ Mongoose ODM
                     ↓
┌─────────────────────────────────────────────────────────┐
│                  Database (MongoDB)                     │
│  - User collection                                      │
│  - Persistent storage                                   │
│  - Data validation                                      │
└─────────────────────────────────────────────────────────┘
```

---

## 📡 API Endpoints

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| `POST` | `/api/auth/register` | Register new user | No |
| `POST` | `/api/auth/login` | Login user | No |
| `GET` | `/api/auth/me` | Get current user | Yes |

### Example Request

```bash
# Register User
curl -X POST http://localhost:5000/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{
    "name": "John Doe",
    "email": "john@example.com",
    "password": "password123",
    "role": "Student"
  }'
```

### Example Response

```json
{
  "success": true,
  "message": "User registered successfully",
  "data": {
    "user": {
      "id": "64f5a3b2c1234567890abcde",
      "name": "John Doe",
      "email": "john@example.com",
      "role": "Student",
      "createdAt": "2025-10-18T10:30:00.000Z"
    },
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
  }
}
```

---

## 🗂️ Project Structure

```
.
├── backend/                    # Backend API Server
│   ├── models/
│   │   └── User.js            # User schema with bcrypt
│   ├── routes/
│   │   └── auth.js            # Authentication endpoints
│   ├── middleware/
│   │   └── auth.js            # JWT verification
│   ├── server.js              # Express server
│   ├── package.json           # Dependencies
│   └── .env                   # Configuration
│
├── frontend/                   # Frontend Application
│   ├── index.html             # Login/Register page
│   ├── dashboard.html         # User dashboard
│   ├── style.css              # Enhanced styles
│   ├── config.js              # API configuration
│   ├── app.js                 # Auth logic
│   └── dashboard.js           # Dashboard logic
│
└── docs/                       # Documentation
    ├── README_BACKEND.md
    ├── INSTALLATION_GUIDE.md
    ├── ARCHITECTURE.md
    ├── PROJECT_SUMMARY.md
    └── PROJECT_STRUCTURE.md
```

---

## 🔧 Tech Stack

### Backend
- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **MongoDB** - Database
- **Mongoose** - ODM
- **bcryptjs** - Password hashing
- **jsonwebtoken** - JWT authentication
- **express-validator** - Input validation
- **cors** - CORS middleware

### Frontend
- **HTML5** - Structure
- **CSS3** - Styling & animations
- **JavaScript (ES6+)** - Logic
- **Fetch API** - HTTP requests
- **LocalStorage** - Client storage

---

## 🔒 Security Features

✅ **Password Security**
- Bcrypt hashing with 10 salt rounds
- Never stored in plain text
- Timing attack resistant

✅ **Authentication**
- JWT token-based
- 7-day expiration
- Secure token verification

✅ **Input Validation**
- Client-side validation
- Server-side validation
- Database schema validation

✅ **API Security**
- CORS configuration
- Protected routes
- Error handling
- Environment variables

---

## 🧪 Testing

### Manual Testing

1. **Register a Student**
   - Go to http://localhost:3000
   - Fill registration form with Student role
   - Verify success message and redirect

2. **Register a Teacher**
   - Register with Teacher role
   - Verify account creation

3. **Login**
   - Logout and login with created account
   - Verify authentication works

4. **Database Verification**
   ```bash
   mongo
   use lms_database
   db.users.find().pretty()
   ```

### API Testing with Postman

Import the collection: `backend/LMS_API.postman_collection.json`

---

## 📊 Database Schema

### User Collection

```javascript
{
  _id: ObjectId,              // Auto-generated
  name: String,               // 2-50 characters
  email: String,              // Unique, valid email
  password: String,           // Hashed with bcrypt
  role: "Student"|"Teacher",  // Enum
  createdAt: Date,            // Auto-generated
  updatedAt: Date             // Auto-updated
}
```

---

## ⚙️ Configuration

### Environment Variables (.env)

```env
PORT=5000
NODE_ENV=development
MONGODB_URI=mongodb://localhost:27017/lms_database
JWT_SECRET=your_secret_key_here
JWT_EXPIRE=7d
CLIENT_URL=http://localhost:3000
```

**⚠️ Important**: Change `JWT_SECRET` in production!

---

## 🎨 Screenshots

### Login Page
![Beautiful gradient design with glassmorphism effects]

### Registration
![Role-based registration with validation]

### Dashboard
![User information and account details]

---

## 🐛 Troubleshooting

### MongoDB Connection Error
```bash
# Ensure MongoDB is running
mongod
```

### Port Already in Use
```bash
# Change PORT in .env or kill process
lsof -ti:5000 | xargs kill -9
```

### CORS Error
```bash
# Verify CLIENT_URL in .env matches frontend URL
CLIENT_URL=http://localhost:3000
```

See [INSTALLATION_GUIDE.md](INSTALLATION_GUIDE.md) for more troubleshooting.

---

## 🚀 Deployment

### Backend (Heroku/Railway/Render)

```bash
# Set environment variables
PORT=5000
NODE_ENV=production
MONGODB_URI=<your_mongodb_atlas_uri>
JWT_SECRET=<strong_random_string>
CLIENT_URL=<your_frontend_url>
```

### Frontend (Netlify/Vercel)

Update `config.js`:
```javascript
const API_CONFIG = {
  BASE_URL: 'https://your-backend-api.com'
};
```

---

## 📈 Next Steps

### Silver Level Features
- [ ] Course management (Teacher)
- [ ] Course enrollment (Student)
- [ ] View enrolled students (Teacher)

### Gold Level Features
- [ ] Assignment creation (Teacher)
- [ ] Assignment submission (Student)
- [ ] View submissions (Teacher)

### Platinum Level Features
- [ ] Grading system
- [ ] Performance analytics
- [ ] Discussion forums
- [ ] Course materials upload
- [ ] Notification system

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

---

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

## 👥 Support

For questions or issues:
1. Check [INSTALLATION_GUIDE.md](INSTALLATION_GUIDE.md)
2. Review [README_BACKEND.md](README_BACKEND.md)
3. Read [ARCHITECTURE.md](ARCHITECTURE.md)

---

## 🎓 Learning Resources

- **Node.js**: https://nodejs.org/docs
- **Express.js**: https://expressjs.com/guide
- **MongoDB**: https://docs.mongodb.com/
- **JWT**: https://jwt.io/introduction
- **bcrypt**: https://github.com/kelektiv/node.bcrypt.js

---

## ✅ Success Checklist

- [x] User registration with validation
- [x] Secure password hashing
- [x] User login with authentication
- [x] JWT token generation
- [x] MongoDB database integration
- [x] Protected API routes
- [x] Role-based access (Student/Teacher)
- [x] Beautiful, responsive UI
- [x] Comprehensive documentation
- [x] API testing collection

---

## 📊 Project Stats

- **Total Files**: 21
- **Lines of Code**: ~2,900
- **Documentation**: ~2,000 lines
- **API Endpoints**: 3
- **Database Models**: 1
- **Frontend Pages**: 2
- **Security Features**: 6+

---

## 🏆 Achievements

✨ **100% Bronze Level Requirements Met**

- ✅ User registration working perfectly
- ✅ User login functioning correctly
- ✅ Secure database integration complete
- ✅ Production-quality code
- ✅ Comprehensive documentation
- ✅ Enhanced user experience

---

## 🔮 Vision

This Bronze Level implementation provides a solid foundation for building a complete Learning Management System with:

- **Scalable Architecture** - Ready for feature additions
- **Security First** - Industry-standard practices
- **Great UX** - Modern, intuitive interface
- **Well Documented** - Easy to understand and extend

---

## 📞 Quick Links

- [Quick Start Guide](START_HERE.md)
- [Installation Guide](INSTALLATION_GUIDE.md)
- [API Documentation](README_BACKEND.md)
- [Architecture Overview](ARCHITECTURE.md)
- [Project Summary](PROJECT_SUMMARY.md)
- [File Structure](PROJECT_STRUCTURE.md)

---

<div align="center">

**Built with ❤️ for modern education**

**Version 1.0.0 - Bronze Level**

[Get Started](START_HERE.md) • [Documentation](INSTALLATION_GUIDE.md) • [API Docs](README_BACKEND.md)

</div>

---

**Made with Node.js, Express, MongoDB, and a passion for education! 🚀**
