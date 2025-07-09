# AI Code Assistant

A full-stack AI-powered code assistant application with a modern React frontend and FastAPI backend. Features real-time streaming responses, syntax highlighting, session management, and model selection.

## Features

### 🚀 Core Features
- **ChatGPT-like Interface**: Modern chat interface with real-time streaming responses
- **Multiple AI Models**: Support for Ollama (local), OpenAI GPT-4, Claude, and Gemini
- **Session Management**: Create, save, and switch between multiple conversation sessions
- **Code Highlighting**: Automatic syntax highlighting for 20+ programming languages
- **Auto-resizing Input**: Dynamic textarea that adjusts to content length
- **Responsive Design**: Works seamlessly on desktop and mobile devices

### 🛠️ Technical Features
- **Real-time Streaming**: Server-Sent Events for live response streaming
- **Persistent Sessions**: Local storage with automatic session saving
- **Copy Code Blocks**: One-click copying of code snippets
- **Error Handling**: Graceful error handling and user feedback
- **Extensible Architecture**: Easy to add new models and features

## Quick Start

### Prerequisites
- Node.js (v16 or higher)
- Python 3.8+
- npm or yarn

### 1. Clone the Repository
```bash
git clone <repository-url>
cd code-assistant
```

### 2. Start the Backend
```bash
cd backend
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
uvicorn main:app --reload --port 8000
```

### 3. Start the Frontend
```bash
cd frontend
npm install
npm run dev
```

### 4. Access the Application
Open your browser and navigate to `http://localhost:5173`

## Project Structure

```
code-assistant/
├── backend/                 # FastAPI backend
│   ├── main.py             # Main application file
│   ├── requirements.txt    # Python dependencies
│   └── README.md          # Backend documentation
└── frontend/               # React frontend
    ├── src/
    │   ├── components/     # React components
    │   │   ├── ChatArea.jsx
    │   │   ├── Message.jsx
    │   │   └── SessionsSidebar.jsx
    │   ├── hooks/          # Custom React hooks
    │   │   ├── useChatStream.js
    │   │   └── useLocalStorage.js
    │   ├── App.jsx         # Main app component
    │   ├── App.css         # Styles
    │   └── main.jsx        # React entry point
    ├── package.json        # Node.js dependencies
    ├── vite.config.js      # Vite configuration
    └── index.html          # HTML template
```

## API Endpoints

### Chat API
- `POST /api/chat/stream` - Stream chat responses
- `GET /api/models` - Get available AI models
- `GET /api/sessions/{session_id}` - Get session history
- `GET /api/health` - Health check

### Request Example
```json
{
  "session_id": "uuid-string",
  "model": "ollama-llama2",
  "message": "Write a Python function to sort a list"
}
```

## Local AI Model Integration

### Ollama Setup
1. Install Ollama from https://ollama.ai
2. Download a model: `ollama pull llama2`
3. Start Ollama server: `ollama serve`
4. The application will automatically detect local models

### Custom Model Integration
Modify the `simulate_ai_response` function in `backend/main.py` to integrate with your preferred AI model API.

## Environment Variables

### Backend
- `HOST`: Server host (default: 0.0.0.0)
- `PORT`: Server port (default: 8000)
- `CORS_ORIGINS`: Allowed CORS origins

### Frontend
- `VITE_API_URL`: Backend API URL (default: http://localhost:8000)

## Production Deployment

### Backend
```bash
pip install gunicorn
gunicorn main:app -w 4 -k uvicorn.workers.UvicornWorker
```

### Frontend
```bash
npm run build
# Serve the dist/ folder with your preferred web server
```

## Features in Detail

### Streaming Responses
The application uses Server-Sent Events (SSE) for real-time streaming, providing a ChatGPT-like experience where responses appear word by word.

### Code Highlighting
Powered by Prism.js, the application automatically detects and highlights code blocks in over 20 programming languages including:
- JavaScript/TypeScript
- Python
- Java
- C/C++
- CSS/SCSS
- SQL
- Bash
- And many more...

### Session Management
- Sessions are automatically saved to browser localStorage
- Each session has a unique ID and title
- Easy switching between multiple conversations
- Session history persists between browser sessions

### Model Selection
- Dropdown interface for selecting AI models
- Support for both local and cloud-based models
- Easy to extend with new model providers

## Troubleshooting

### Common Issues

**CORS Error**
- Ensure the backend is running on the correct port
- Check CORS settings in `main.py`

**Streaming Not Working**
- Verify the backend is returning `text/event-stream` content type
- Check browser developer tools for SSE connection status

**Sessions Not Saving**
- Ensure localStorage is enabled in your browser
- Check browser developer tools → Application → Local Storage

### Development Tips

**Hot Reload**
Both frontend and backend support hot reload for development:
- Backend: `uvicorn main:app --reload`
- Frontend: `npm run dev`

**API Documentation**
Access interactive API docs at `http://localhost:8000/docs`

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## License

This project is open source and available under the MIT License.

## Support

For support, please open an issue in the repository or contact the development team.
