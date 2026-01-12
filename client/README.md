# Chat App Frontend

A modern real-time chat application built with React, Redux Toolkit, and Socket.IO. Features include user authentication, real-time messaging, image sharing, and message status indicators.

## 🚀 Features

- **Real-time Messaging**: Instant message delivery using Socket.IO
- **User Authentication**: Secure login and registration system
- **Image Sharing**: Upload and share images with automatic compression
- **Message Status**: Read receipts with single/double tick indicators
- **Responsive Design**: Mobile-friendly interface built with Tailwind CSS
- **User Management**: View online users and chat history
- **Modern UI**: Clean and intuitive user interface

## 🛠️ Tech Stack

- **Frontend Framework**: React 19
- **State Management**: Redux Toolkit
- **Styling**: Tailwind CSS 4
- **Build Tool**: Vite
- **Real-time Communication**: Socket.IO Client
- **HTTP Client**: Axios
- **Routing**: React Router DOM
- **Image Compression**: CompressorJS
- **Notifications**: React Toastify
- **Loading States**: React Loading Skeleton

## 📋 Prerequisites

- Node.js (v16 or higher)
- npm or yarn
- Backend server running (see backend README)

## 🔧 Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd chat-app-frontend-main
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Environment Setup**
   Create a `.env` file in the root directory:
   ```env
   VITE_API_URL=http://localhost:8000
   VITE_SOCKET_URL=http://localhost:8000
   ```

4. **Start the development server**
   ```bash
   npm run dev
   ```

The application will be available at `http://localhost:5173`

## 📁 Project Structure

```
src/
├── api/                 # API service functions
│   ├── auth.js         # Authentication API calls
│   ├── axios.js        # Axios configuration
│   ├── messages.js     # Message API calls
│   └── user.js         # User API calls
├── assets/             # Static assets (images, icons)
├── components/         # Reusable UI components
│   ├── ChatContainer.jsx
│   ├── ChatInput.jsx
│   ├── UsersList.jsx
│   └── ...
├── context/            # React context providers
│   └── SocketContext.jsx
├── feature/            # Redux slices
│   ├── messageSlice.js
│   └── userSlice.js
├── pages/              # Page components
│   ├── ChatWindow.jsx
│   ├── Home.jsx
│   ├── Login.jsx
│   └── Signup.jsx
├── routes/             # Route configuration
├── services/           # Utility services
└── store/              # Redux store configuration
```

## 🔑 Key Components

### Authentication
- **Login/Signup**: User registration and authentication
- **Protected Routes**: Route guards for authenticated users
- **JWT Token Management**: Automatic token handling

### Chat Features
- **Real-time Messaging**: Instant message delivery
- **Image Upload**: Drag & drop image sharing with compression
- **Message Status**: Delivery and read status indicators
- **User List**: Online users and chat history

### State Management
- **Redux Toolkit**: Centralized state management
- **Message Slice**: Chat messages and conversation state
- **User Slice**: User authentication and profile data

## 🚀 Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build
- `npm run lint` - Run ESLint

## 🌐 Deployment

The app is configured for deployment on Vercel:

1. **Build the project**
   ```bash
   npm run build
   ```

2. **Deploy to Vercel**
   - Connect your repository to Vercel
   - Set environment variables in Vercel dashboard
   - Deploy automatically on push to main branch

## 🔧 Configuration

### Environment Variables
- `VITE_API_URL`: Backend API URL
- `VITE_SOCKET_URL`: Socket.IO server URL

### CORS Configuration
Ensure your backend allows the frontend domain in CORS settings.

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

1. **Connection Issues**
   - Verify backend server is running
   - Check API and Socket URLs in environment variables

2. **Build Errors**
   - Clear node_modules and reinstall dependencies
   - Check Node.js version compatibility

3. **Socket Connection Failed**
   - Ensure Socket.IO server is running on backend
   - Verify CORS configuration allows frontend domain

## 📞 Support

For support and questions, please open an issue in the repository.