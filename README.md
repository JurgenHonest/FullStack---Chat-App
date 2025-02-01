# Real-Time Chat Application 📱💬
![image (2)](https://github.com/user-attachments/assets/4839e318-13f0-4377-bffc-5e70ec286003)


## Overview
This real-time chat application delivers a modern, seamless messaging experience. Packed with features like real-time communication, secure authentication, media sharing, and dynamic themes, it’s designed to provide both functionality and aesthetics.

🌟 Live Demo: Check it out [here](https://fullstack-chat-app-ydz9.onrender.com/)

## 🚀 Features
🔴 Real-Time Messaging
- Powered by Socket.IO, ensuring instant message delivery between users.
- Efficient handling of user connections and disconnections.
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
### 🔒 Secure User Authentication
- Password hashing with bcrypt ensures data safety.
- JWT (JSON Web Tokens) for secure session management.
```
import jwt from "jsonwebtoken";

export const generateToken = (userId, res) => {
  const token = jwt.sign({ userId }, process.env.JWT_SECRET, {
    expiresIn: "7d",
  });

  res.cookie("jwt", token, {
    maxAge: 7 * 24 * 60 * 60 * 1000, //Millisecond
    httpOnly: true, //prevent XSS attacks croos-site scripting attacks
    sameSite: "strict", // CSRF attacks cross-site request forgery attacks
    secure: process.env.NODE_ENV !== "development",
  });

  return token;
};
```

### 🎨 Dynamic Themes
- Supports 26 customizable themes using Tailwind CSS and DaisyUI.

### 📱 Responsive Design
- Fully responsive UI for desktops, tablets, and mobile devices.
- Built with Tailwind CSS and DaisyUI, the application is fully responsive, providing a smooth experience across all devices, from desktops to mobile phones.
```
<div
      data-theme={theme}
      className="h-screen container mx-auto px-4 pt-20 max-w-5xl"
    >
      <div className="space-y-6">
        <div className="flex flex-col gap-1">
          <h2 className="text-lg font-semibold">Theme</h2>
          <p className="text-sm text-base-content/70">
            Choose a theme for your chat interface
          </p>
        </div>
    </div>
```

### 🖼️ Media Sharing
- Upload and share images/files seamlessly through Cloudinary integration.

```
cloudinary.config({
  cloud_name: process.env.CLOUDINARY_CLOUD_NAME,
  api_key: process.env.CLOUDINARY_API_KEY,
  api_secret: process.env.CLOUDINARY_API_SECRET,
});
```

## 🛠️ Tech Stack

## Front-End:
- React with JSX for UI development.<br>
- Tailwind CSS and DaisyUI for styling and themes

## Back-End:
- Node.js with Express for the server.<br>
- MongoDB for database management.<br>
- Socket.IO for real-time messaging

## Additional Tools:
1. bcrypt for password hashing<br>
2. JWT for authentication<br>
3. Cloudinary for media storage<br>
4. dotenv for environment configuration<br>
5. cookie-parser for handling cookies<br>
6. CORS for managing cross-origin requests

###   To install: 
Must have node installed from browsers
```
//create package.json
npm init -y
npm install express socket.io mongoose bcrypt jsonwebtoken cors cookie-parser dotenv multer cloudinary multer-storage-cloudinary
```

## How It Works
#### 1. User Authentication: 
Users register or log in securely using hashed passwords and JWT.
#### 2. Real-Time Communication: 
Messages are exchanged instantly using Socket.IO.
#### 3. Database Storage: 
MongoDB stores user data, messages, and media links.
#### 4. Dynamic Themes:
Users can switch between 26 available themes.
#### 5.Responsive UI: 
Tailored for desktops and mobile devices with responsive design.

## Future Plans
1. Implement AI-based message filtering for spam detection.
2. Integrate end-to-end encryption for enhanced security.
3. Introduce voice and video calling features.

