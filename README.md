
# **Node.js Real-Time Chat Application 💬**

[![Node.js Version](https://img.shields.io/badge/node-%3E%3D12.0.0-green.svg)](https://nodejs.org/)
[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![GitHub Stars](https://img.shields.io/github/stars/aadhar-gaur/nodejs-chat-app.svg)](https://github.com/aadhar-gaur/nodejs-chat-app/stargazers)
[![GitHub Issues](https://img.shields.io/github/issues/aadhar-gaur/nodejs-chat-app.svg)](https://github.com/aadhar-gaur/nodejs-chat-app/issues)

## **🚀 Overview**

**Node.js Real-Time Chat Application** is a simple yet powerful real-time chat application built using Node.js, Express, and Socket.io. This project demonstrates real-time communication between clients and server using WebSockets, allowing users to chat instantly without page refreshes.

Perfect for developers looking to understand:
- Real-time web applications
- Socket.io for WebSocket communication
- Basic Node.js server architecture
- Frontend-backend integration

## **✨ Features**

* **Real-time messaging** - Instant message delivery to all connected users
* **User management** - Unique usernames for each participant
* **Simple UI** - Clean, responsive interface using Bootstrap 5
* **Cross-browser compatibility** - Works on all modern browsers
* **Easy deployment** - Simple setup with Node.js
* **Scalable architecture** - Ready for expansion with additional features

## **🛠️ Tech Stack**

- **Backend**: Node.js, Express, Socket.io
- **Frontend**: HTML5, CSS3, Bootstrap 5
- **Real-time Communication**: WebSockets via Socket.io
- **Development Environment**: Node.js 12+
- **Package Manager**: npm

## **📦 Installation**

### **Prerequisites**

Ensure you have the following installed:
- [Node.js](https://nodejs.org/) (v12 or higher)
- [npm](https://www.npmjs.com/) (comes with Node.js)
- A modern web browser

### **Quick Start**

1. **Clone the repository**:
   ```bash
   git clone https://github.com/aadhar-gaur/nodejs-chat-app.git
   cd nodejs-chat-app
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Start the server**:
   ```bash
   node server.js
   ```

4. **Open the application**:
   - Open your browser and navigate to `http://localhost:3000`

### **Development Setup**

For development, you can use:
```bash
npm run dev
```
This will start the server with nodemon for automatic restarting during development.

## **🎯 Usage**

### **Basic Usage**

1. **Access the application** in your browser at `http://localhost:3000`
2. **Create a username** by entering a unique name and clicking "Submit"
3. **Start chatting** by typing messages in the input field and pressing Enter
4. **See all messages** in real-time as they are sent by other users

### **Example Code Snippets**

#### **Server-side Socket.io Events**
```javascript
// server.js
io.sockets.on("connection", function(socket) {
    // Handle new user connection
    socket.on("new user", function(data, callback) {
        if (usernames.indexOf(data) != -1) {
            callback(false); // Username taken
        } else {
            callback(true);
            socket.username = data;
            usernames.push(socket.username);
            updateUsernames();
        }
    });

    // Handle message sending
    socket.on("send message", function(data) {
        io.sockets.emit("new message", {msg: data, user: socket.username});
    });

    // Handle user disconnection
    socket.on("disconnect", function() {
        if (!socket.username) return;
        usernames.splice(usernames.indexOf(socket.username), 1);
        updateUsernames();
    });
});
```

#### **Client-side Socket.io Connection**
```javascript
// Inside your client-side JavaScript
const socket = io();
socket.on('connect', () => {
    console.log('Connected to server');
});

socket.on('new message', (data) => {
    // Display received message
    const messageElement = document.createElement('div');
    messageElement.textContent = `${data.user}: ${data.msg}`;
    document.getElementById('chatWindow').appendChild(messageElement);
});
```

## **📁 Project Structure**

```
nodejs-chat-app/
├── node_modules/          # Dependencies
├── public/                # Static files
│   ├── css/               # CSS files
│   ├── js/                # JavaScript files
│   └── index.html         # Main HTML file
├── views/                 # View templates (if any)
├── .gitignore             # Git ignore file
├── package.json           # Project dependencies and scripts
├── package-lock.json      # Lock file for dependency versions
├── README.md              # This file
└── server.js              # Main server file
```

## **🔧 Configuration**

### **Environment Variables**

You can configure the application using environment variables:

```bash
# Set the port
PORT=8080 node server.js
```

### **Customization Options**

1. **Change the port**:
   Modify the `PORT` variable in `server.js` or set it via environment variables.

2. **Customize the UI**:
   Edit the CSS in `public/css/chat.css` or modify the Bootstrap components in `index.html`.

3. **Add new features**:
   Extend the Socket.io event handlers in `server.js` to add new functionality.

## **🤝 Contributing**

We welcome contributions from the community! Here's how you can contribute:

1. **Fork the repository** and create your branch from `main`.
2. **Write tests** for your new features.
3. **Commit your changes** with descriptive messages.
4. **Open a pull request** explaining your changes.

### **Development Setup**

To set up the development environment:

1. Clone the repository
2. Install dependencies:
   ```bash
   npm install
   ```
3. Start the development server:
   ```bash
   npm run dev
   ```

### **Code Style Guidelines**

- Follow the existing code style
- Use consistent indentation (2 spaces)
- Write clear, concise comments
- Ensure all new code is tested

## **📝 License**

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

## **👥 Authors & Contributors**

**Maintainer**: [Aadhar Gaur](https://github.com/aadhar-gaur)

**Contributors**:
- [Your Name](https://github.com/yourusername) - Your Contribution
- [Another Contributor](https://github.com/anotheruser) - Another Contribution

## **🐛 Issues & Support**

### **Reporting Issues**

If you encounter any problems or have feature requests, please open an issue on GitHub. Include:

- Detailed description of the issue
- Steps to reproduce
- Expected behavior
- Screenshots or code snippets if applicable

### **Getting Support**

For questions or support, you can:

- Open an issue on GitHub
- Join our community discussion (link to be added)
- Contact the maintainer directly

## **🗺️ Roadmap**

Here's what we have planned for future updates:

- **Feature 1**: Add user authentication
- **Feature 2**: Implement private messaging
- **Feature 3**: Add message persistence
- **Feature 4**: Implement user presence indicators
- **Feature 5**: Add support for file sharing

## **🎉 Star and Share!**

If you found this project helpful, please consider giving it a star ⭐ on GitHub. Sharing is caring!

[![GitHub Stars](https://img.shields.io/github/stars/aadhar-gaur/nodejs-chat-app.svg?style=social)](https://github.com/aadhar-gaur/nodejs-chat-app/stargazers)
```

This README.md provides a comprehensive guide for developers, making it easy to understand, install, and contribute to the project. It follows modern GitHub README best practices with clear sections, engaging content, and practical examples. The emojis and visual elements make it more appealing, while the detailed structure ensures all necessary information is easily accessible.
