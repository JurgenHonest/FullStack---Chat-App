# Real-Time Chat Application 📱💬
![Uploading image (2).png…]()



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

### 3. Dynamic Themes
Supports 26 themes with Tailwind CSS and DaisyUI for complete customization.

### 4. Responsive Design
Built with Tailwind CSS and DaisyUI, the application is fully responsive, providing a smooth experience across all devices, from desktops to mobile phones.
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

### 5. Media Sharing
Users can upload and share images or files securely through Cloudinary.
```
cloudinary.config({
  cloud_name: process.env.CLOUDINARY_CLOUD_NAME,
  api_key: process.env.CLOUDINARY_API_KEY,
  api_secret: process.env.CLOUDINARY_API_SECRET,
});
```

## Tech Stack

## Front-End:
React with JSX for UI development.<br>
Tailwind CSS and DaisyUI for styling and themes

## Back-End:
Node.js with Express for the server.<br>
MongoDB for database management.<br>
Socket.IO for real-time messaging

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

## Deployment
The application is live and deployed on Render.com. Check it out here: Your App URL.

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

