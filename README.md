# Real-Time Chat Application 📱💬
## Overview
This real-time chat application provides a seamless and responsive messaging experience. Designed with modern aesthetics and functionality, the app features multiple themes, robust authentication, and real-time communication.

## Features
### 1. Real-Time Messaging
Utilizes Socket.IO to ensure seamless real-time message delivery between users.
```
io.on("connection", (socket) => {
  console.log("A user connected", socket.id);

  io.emit("getOnlineUsers", Object.keys(userSocketMap));

  socket.on("disconnect", () => {
    console.log("A user disconnected", socket.id);
    delete userSocketMap[userId];
    io.emit("getOnlineUsers", Object.keys(userSocketMap));
  });
```
### 2. Secure User Authentication
User accounts are secured with bcrypt for password hashing and JWT for authentication.


### 3. Dynamic Themes
Supports 26 themes with Tailwind CSS and DaisyUI for complete customization.
Typing Indicators: Real-time feedback when other users are typing.
### 4. Responsive Design
Built with Tailwind CSS and DaisyUI, the application is fully responsive, providing a smooth experience across all devices, from desktops to mobile phones.
Dark Mode: Optional dark theme for comfortable viewing at night.
### 5. Media Sharing
Users can upload and share images or files securely through Cloudinary.
Read Receipts: Notifications when a message has been read.
Group Chats: Create and manage group conversations with multiple participants.
Media Sharing: Supports image, video, and document uploads.
### 4. Responsive Design
Built with Tailwind CSS and DaisyUI, the application is fully responsive, providing a smooth experience across all devices, from desktops to mobile phones.
Dark Mode: Optional dark theme for comfortable viewing at night.
## Tech Stack
## Front-End:
React with JSX for UI development.<br>
Tailwind CSS and DaisyUI for styling and themes
## Back-End:
Node.js with Express for the server.<br>
MongoDB for database management.<br>
Socket.IO for real-time messaging
## Additional Tools:
bcrypt for password hashing<br>
JWT for authentication<br>
Cloudinary for media storage<br>
dotenv for environment configuration<br>
cookie-parser for handling cookies<br>
CORS for managing cross-origin requests
## How It Works
### 1. User Authentication: 
Users register or log in securely using hashed passwords and JWT.
### 2. Real-Time Communication: 
Messages are exchanged instantly using Socket.IO.
### 3. Database Storage: 
MongoDB stores user data, messages, and media links.
### 4. Dynamic Themes:
Users can switch between 26 available themes.
### 5.Responsive UI: 
Tailored for desktops and mobile devices with responsive design.
### Future Plans
Implement AI-based message filtering for spam detection.
Integrate end-to-end encryption for enhanced security.
Introduce voice and video calling features.

