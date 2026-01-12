
# Chat App Backend

A robust Node.js backend API for a real-time chat application built with Express.js, MongoDB, and Socket.IO. Features include user authentication, real-time messaging, image upload with Cloudinary, and WebSocket communication.

## 🚀 Features

- **RESTful API**: Clean and organized API endpoints
- **Real-time Communication**: WebSocket support with Socket.IO
- **User Authentication**: JWT-based authentication system
- **Image Upload**: Cloudinary integration for image storage
- **Database**: MongoDB with Mongoose ODM
- **Security**: Password hashing with bcrypt
- **CORS**: Configured for frontend integration
- **File Upload**: Multer middleware for handling file uploads

## 🛠️ Tech Stack

- **Runtime**: Node.js
- **Framework**: Express.js
- **Database**: MongoDB with Mongoose
- **Authentication**: JSON Web Tokens (JWT)
- **Password Hashing**: bcrypt
- **Real-time**: Socket.IO
- **File Upload**: Multer + Cloudinary
- **Validation**: Validator.js
- **Environment**: dotenv

## 📋 Prerequisites

- Node.js (v16 or higher)
- MongoDB (local or cloud instance)
- Cloudinary account for image storage
- npm or yarn

## 🔧 Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd chat-app-backend-main
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Environment Setup**
   Create a `.env` file in the root directory:
   ```env
   PORT=8000
   MONGODB_URI=mongodb://localhost:27017/chatapp
   JWT_SECRET=your_jwt_secret_key
   CLOUDINARY_CLOUD_NAME=your_cloudinary_cloud_name
   CLOUDINARY_API_KEY=your_cloudinary_api_key
   CLOUDINARY_API_SECRET=your_cloudinary_api_secret
   ```

4. **Start the server**
   ```bash
   # Development mode
   npm run dev
   
   # Production mode
   npm start
   ```

The server will be available at `http://localhost:8000`

## 📁 Project Structure

```
src/
├── config/
│   ├── cloudinary.js    # Cloudinary configuration
│   ├── db.js           # MongoDB connection
│   └── multer.js       # File upload configuration
├── controllers/
│   ├── authController.js    # Authentication logic
│   ├── messageController.js # Message handling
│   └── userController.js    # User management
├── middleware/
│   ├── auth.js         # JWT authentication middleware
│   └── uploadHandler.js # File upload middleware
├── models/
│   ├── message.js      # Message schema
│   └── user.js         # User schema
├── routes/
│   ├── authRoutes.js   # Authentication routes
│   ├── messageRoutes.js # Message routes
│   └── userRoutes.js   # User routes
├── websocket/
│   └── index.js        # Socket.IO configuration
└── app.js              # Express app configuration
```

## 🔌 API Endpoints

### Authentication
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `POST /api/auth/logout` - User logout

### Users
- `GET /api/user/users` - Get all users (authenticated)
- `GET /api/user/profile` - Get user profile (authenticated)

### Messages
- `GET /api/message/:userId` - Get messages with specific user
- `POST /api/message/send/:userId` - Send message to user
- `POST /api/message/upload` - Upload image message

## 🔐 Authentication

The API uses JWT (JSON Web Tokens) for authentication:

1. **Registration/Login**: Returns JWT token
2. **Protected Routes**: Require `Authorization: Bearer <token>` header
3. **Token Validation**: Middleware validates tokens on protected routes

## 🗄️ Database Schema

### User Model
```javascript
{
  username: String (required, unique),
  email: String (required, unique),
  password: String (required, hashed),
  profilePicture: String (optional),
  createdAt: Date,
  updatedAt: Date
}
```

### Message Model
```javascript
{
  sender: ObjectId (ref: User),
  receiver: ObjectId (ref: User),
  message: String,
  messageType: String (text/image),
  imageUrl: String (optional),
  status: String (sent/delivered/read),
  createdAt: Date,
  updatedAt: Date
}
```

## 🌐 WebSocket Events

### Client to Server
- `join` - Join user to their room
- `sendMessage` - Send message to another user
- `messageRead` - Mark message as read

### Server to Client
- `newMessage` - Receive new message
- `messageStatusUpdate` - Message status update
- `userOnline` - User came online
- `userOffline` - User went offline

## ☁️ File Upload

Images are uploaded to Cloudinary with the following features:
- **Automatic optimization**: Images are compressed and optimized
- **Multiple formats**: Supports JPEG, PNG, WebP
- **Size limits**: Configurable file size restrictions
- **Secure URLs**: Generated secure URLs for image access

## 🚀 Available Scripts

- `npm start` - Start production server
- `npm run dev` - Start development server with nodemon
- `npm test` - Run tests (not implemented)

## 🔧 Configuration

### Environment Variables
- `PORT`: Server port (default: 8000)
- `MONGODB_URI`: MongoDB connection string
- `JWT_SECRET`: Secret key for JWT tokens
- `CLOUDINARY_CLOUD_NAME`: Cloudinary cloud name
- `CLOUDINARY_API_KEY`: Cloudinary API key
- `CLOUDINARY_API_SECRET`: Cloudinary API secret

### CORS Configuration
The server is configured to accept requests from:
- `http://localhost:5173` (development)
- `https://chat-app-frontend-one-xi.vercel.app` (production)

## 🚀 Deployment

### Environment Setup
1. Set up MongoDB (MongoDB Atlas recommended)
2. Configure Cloudinary account
3. Set environment variables on hosting platform

### Deployment Platforms
- **Heroku**: Add Procfile with `web: node index.js`
- **Railway**: Automatic deployment from Git
- **DigitalOcean**: Docker or direct deployment

## 🔒 Security Features

- **Password Hashing**: bcrypt with salt rounds
- **JWT Authentication**: Secure token-based auth
- **CORS Protection**: Configured allowed origins
- **Input Validation**: Server-side validation
- **File Upload Security**: Type and size restrictions

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the ISC License.

## 🐛 Troubleshooting

### Common Issues

1. **MongoDB Connection Failed**
   - Check MongoDB URI in environment variables
   - Ensure MongoDB service is running
   - Verify network connectivity

2. **Cloudinary Upload Errors**
   - Verify Cloudinary credentials
   - Check file size and format restrictions
   - Ensure proper API key permissions

3. **JWT Token Issues**
   - Verify JWT_SECRET is set
   - Check token expiration settings
   - Ensure proper token format in requests

4. **Socket.IO Connection Issues**
   - Check CORS configuration
   - Verify client-server URL matching
   - Ensure proper event handling

## 📞 Support

For support and questions, please open an issue in the repository.