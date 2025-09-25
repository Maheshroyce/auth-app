# Full-Stack Authentication Module

A complete authentication system built with React (frontend) and Node.js + Express + MongoDB (backend), featuring JWT authentication, password hashing, and input validation.

## 🚀 Features

### Backend Features
- **User Registration & Login** with email/password
- **JWT Authentication** with secure token management
- **Password Hashing** using bcrypt with salt rounds
- **Input Validation** using Joi schemas
- **Protected Routes** with authentication middleware
- **MongoDB Integration** with Mongoose ODM
- **Error Handling** with proper HTTP status codes
- **CORS Configuration** for cross-origin requests

### Frontend Features
- **React Router** for navigation and protected routes
- **Context API** for state management
- **Responsive Design** with Tailwind CSS
- **Form Validation** with real-time feedback
- **Loading States** and error handling
- **Token Management** with automatic header injection
- **Auto-redirect** on authentication state changes

## 🛠️ Tech Stack

### Backend
- Node.js
- Express.js
- MongoDB with Mongoose
- JWT (jsonwebtoken)
- bcrypt for password hashing
- Joi for validation
- CORS for cross-origin requests

### Frontend
- React.js (JavaScript)
- React Router DOM
- Context API
- Tailwind CSS
- Axios for HTTP requests

## 📦 Installation & Setup

### Prerequisites
- Node.js (v14 or higher)
- MongoDB Atlas account (or local MongoDB instance)
- Python (for JWT secret generation)

### 1. Clone and Setup

```bash
# Install backend dependencies
cd backend
npm install

# Install frontend dependencies
cd ../frontend
npm install
```

### 2. Environment Variables

#### Backend (.env)
```env
PORT=5000
MONGODB_URI=mongodb+srv://korivimaheswarreddy063_db_user:FQdzWEvbKERLM3JL@cluster0.chtsuum.mongodb.net/authapp
JWT_SECRET=your_jwt_secret_key_here_make_it_long_and_secure_2024
```

#### Frontend (.env)
```env
REACT_APP_API_URL=http://localhost:5000/api
PORT=3000
```

### 3. Generate JWT Secret (Python)

You can generate a secure JWT secret using Python:

```python
import secrets
import string

def generate_jwt_secret(length=64):
    characters = string.ascii_letters + string.digits + "!@#$%^&*"
    secret = ''.join(secrets.choice(characters) for _ in range(length))
    return secret

# Generate a secure JWT secret
jwt_secret = generate_jwt_secret()
print(f"JWT_SECRET={jwt_secret}")
```

Run this Python script and copy the generated secret to your backend `.env` file.

### 4. Run the Application

#### Terminal 1 - Backend Server
```bash
cd backend
npm start
```
The backend will run on `http://localhost:5000`

#### Terminal 2 - Frontend Server
```bash
cd frontend
npm start
```
The frontend will run on `http://localhost:3000`

## 🗂️ Project Structure

```
project-root/
├── backend/
│   ├── controllers/
│   │   └── authController.js
│   ├── middleware/
│   │   └── authMiddleware.js
│   ├── models/
│   │   └── User.js
│   ├── routes/
│   │   └── authRoutes.js
│   ├── validation/
│   │   └── authValidation.js
│   ├── server.js
│   ├── package.json
│   └── .env
├── frontend/
│   ├── public/
│   │   └── index.html
│   ├── src/
│   │   ├── components/
│   │   │   ├── Login.js
│   │   │   ├── Register.js
│   │   │   ├── Profile.js
│   │   │   ├── ProtectedRoute.js
│   │   │   └── Navbar.js
│   │   ├── context/
│   │   │   └── AuthContext.js
│   │   ├── services/
│   │   │   └── authService.js
│   │   ├── App.js
│   │   ├── index.js
│   │   └── index.css
│   ├── package.json
│   └── .env
└── README.md
```

## 🔐 API Endpoints

### Public Routes
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login

### Protected Routes
- `GET /api/auth/profile` - Get user profile (requires JWT token)

### Health Check
- `GET /api/health` - Server health check

## 🎨 UI Features

- **Clean, modern design** with Tailwind CSS
- **Responsive layout** that works on all devices
- **Form validation** with real-time error feedback
- **Loading states** with spinners and disabled buttons
- **Success/error messages** with color-coded alerts
- **Navigation bar** with authentication state awareness
- **Protected routing** with automatic redirects

## 🔒 Security Features

1. **Password Security**
   - Minimum 6 characters
   - Must contain uppercase, lowercase, and numbers
   - Hashed with bcrypt (12 salt rounds)

2. **JWT Security**
   - 7-day expiration
   - Secure secret key
   - Automatic token validation

3. **Input Validation**
   - Server-side validation with Joi
   - Client-side form validation
   - SQL injection prevention

4. **CORS Protection**
   - Configured for frontend origin only
   - Credential support enabled

## 🚦 Usage

1. **Register**: Create a new account with name, email, and password
2. **Login**: Sign in with your email and password
3. **Profile**: View your account information and statistics
4. **Logout**: Sign out and clear authentication tokens

## 🐛 Error Handling

The application includes comprehensive error handling for:
- Network errors
- Validation errors
- Authentication errors
- Server errors
- Token expiration

## 📱 Responsive Design

The frontend is fully responsive with breakpoints for:
- Mobile devices (< 768px)
- Tablet devices (768px - 1024px)
- Desktop devices (> 1024px)

## 🔧 Development

### Backend Development
```bash
cd backend
npm run dev  # Uses nodemon for auto-restart
```

### Frontend Development
```bash
cd frontend
npm start  # Hot reload enabled
```

## 🧪 Testing

Test the API endpoints using tools like Postman or curl:

```bash
# Health check
curl http://localhost:5000/api/health

# Register user
curl -X POST http://localhost:5000/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{"name":"John Doe","email":"john@example.com","password":"Password123"}'

# Login user
curl -X POST http://localhost:5000/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"john@example.com","password":"Password123"}'

# Get profile (replace TOKEN with actual JWT)
curl -X GET http://localhost:5000/api/auth/profile \
  -H "Authorization: Bearer TOKEN"
```

## 📄 License

This project is open source and available under the MIT License.

## 🤝 Contributing

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📞 Support

If you have any questions or need help, please open an issue in the GitHub repository.

---

**Note**: Make sure to replace the JWT_SECRET in your production environment with a secure, randomly generated secret key.