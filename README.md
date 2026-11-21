# Coders pro

Coders pro is a collaborative coding platform where multiple users can join a shared room, edit code together in real time, chat, and use AI assistance. The project combines a React + Vite frontend with a Node.js + Express + Socket.IO backend and MongoDB persistence.

## Overview

This app includes:
- Real-time collaborative code editing
- Shared room-based sessions with room codes
- Live chat inside the editor room
- AI code assistant integration
- Video call support using PeerJS
- Phone-based authentication support via Twilio Verify
- MongoDB-backed room data storage

## Tech Stack

### Frontend
- React 18
- Vite
- Tailwind CSS
- Monaco Editor via @monaco-editor/react
- Socket.IO client
- PeerJS
- Lucide React icons

### Backend
- Node.js
- Express.js
- Socket.IO
- MongoDB with Mongoose
- JWT-based phone auth
- Twilio Verify
- Groq AI SDK

## Project Structure

```text
coders-hub/
├── backend/
│   ├── src/
│   │   ├── auth/
│   │   │   ├── phoneJwt.js
│   │   │   ├── phoneNormalize.js
│   │   │   └── twilioVerify.js
│   │   └── models/
│   │       └── Room.js
│   ├── .env
│   ├── package.json
│   └── server.js
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   │   ├── ai/
│   │   │   │   └── AIAssistant.jsx
│   │   │   ├── chat/
│   │   │   │   └── Chatbox.jsx
│   │   │   ├── editor/
│   │   │   │   ├── CodeEditor.jsx
│   │   │   │   ├── CodeOutput.jsx
│   │   │   │   ├── FileTabs.jsx
│   │   │   │   └── LanguageSelector.jsx
│   │   │   ├── room/
│   │   │   │   └── RoomJoin.jsx
│   │   │   └── video/
│   │   │       └── VideoCall.jsx
│   │   ├── pages/
│   │   │   └── EditorRoom.jsx
│   │   ├── styles/
│   │   │   └── index.css
│   │   ├── utils/
│   │   │   ├── phoneAuth.js
│   │   │   ├── projectFiles.js
│   │   │   └── roomAdminToken.js
│   │   ├── App.jsx
│   │   └── main.jsx
│   ├── .env.production
│   ├── index.html
│   ├── package.json
│   ├── postcss.config.js
│   ├── tailwind.config.js
│   ├── vite.config.js
│   └── .vite-cache/
├── .gitignore
├── README.md
└── package-lock.json (if present in workspace root)
```

## Prerequisites

Before running the project, make sure you have:
- Node.js 18 or newer
- npm or pnpm
- MongoDB instance running locally or a MongoDB Atlas connection string
- Optional: Twilio account for phone verification
- Optional: Groq API key for AI assistance

## Environment Variables

Create a `.env` file inside the `backend` folder with the following values:

```env
PORT=3001
MONGODB_URI=mongodb://localhost:27017/codershub
JWT_SECRET=your_super_secret_key_here
SKIP_PHONE_AUTH=false
GROQ_API_KEY=your_groq_api_key
TWILIO_ACCOUNT_SID=your_twilio_account_sid
TWILIO_AUTH_TOKEN=your_twilio_auth_token
TWILIO_VERIFY_SERVICE_SID=your_twilio_verify_service_sid
```

### Frontend environment

Create a `.env` file in the `frontend` folder, or configure the production environment as needed:

```env
VITE_API_URL=http://localhost:3001
```

## Installation

### 1. Install backend dependencies

```bash
cd backend
npm install
```

### 2. Install frontend dependencies

```bash
cd ../frontend
npm install
```

## Running the Project

### Start the backend

```bash
cd backend
npm run dev
```

The backend runs on port 3001 by default.

### Start the frontend

```bash
cd frontend
npm run dev
```

The frontend will typically run on Vite’s default port 5173.

## Production Build

```bash
cd frontend
npm run build
```

## Features in Detail

### Collaborative Editor
- Multiple users can edit code in the same room
- Project files are managed per room
- Language can be selected for file type support

### Room System
- Users create or join room codes
- Room state is persisted in MongoDB
- Admin tokens are generated for room management

### AI Assistant
- AI integration is built in for code assistance and generation
- This is connected through Groq API support in the backend

### Communication Features
- Socket-based live updates
- Chat panel for room communication
- Video calling support through PeerJS

### Authentication
- Phone number verification can be enabled with Twilio
- JWT tokens are used for secure phone-auth flows
- The app supports skipping phone auth locally via `SKIP_PHONE_AUTH=true`

## Notes

- The backend is configured to accept CORS requests from local Vite development and deployed frontend URLs.
- The app uses MongoDB as the database for room data.
- Production deployment may require different values for `VITE_API_URL`, `MONGODB_URI`, and API keys.

## License

This project is currently provided as a codebase for local development and collaboration. If a formal license is added later, update this section accordingly.

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Open a pull request

## Support

For local development issues:
- verify your `.env` values
- ensure MongoDB is running
- confirm both frontend and backend services are started
- check the browser console and backend logs for connection errors
