# 👨🏻‍💻 AI Customer Success Agent

A real-time voice and text-powered customer success agent that delivers intelligent, empathetic customer support through seamless conversational AI. Experience natural voice interactions, intelligent response generation, and automatic handoff detection, all powered by OpenAI GPT-4o, Whisper STT, Murf AI TTS, and an elegant React frontend.

Powered by cutting-edge AI, designed for exceptional customer experiences.


## 📄 Features

* **Dual Input Modes:** Interact through both text and voice input with seamless switching.
* **Real-Time Voice Conversations:** Speak naturally with real-time speech-to-text conversion using OpenAI Whisper.
* **Intelligent AI Responses:** Get contextually aware, empathetic responses powered by OpenAI GPT-4o.
* **AI-Generated Voice Narration:** Responses are converted into high-quality, natural-sounding audio using Murf AI.
* **Flexible Response Formats:** Choose between text-only, audio-only, or both formats for agent responses.
* **Interactive React Frontend:** A clean, modern single-page application with:
    * Real-time message display with iMessage-style bubbles.
    * Audio player with playback controls and progress tracking.
    * Voice recording with visual feedback and audio visualization.
    * Processing status indicators for each stage (STT, LLM, TTS).
    * Responsive design for desktop and mobile devices.
* **Human Handoff Detection:** Automatic analysis of customer queries to detect when human assistance is needed.
* **Sentiment Analysis:** Real-time sentiment analysis of customer messages to gauge satisfaction levels.
* **Conversation History:** Maintains full conversation context with intelligent history management.
* **Session Management:** Robust session handling with automatic cleanup and inactivity timeouts.
* **WebSocket Communication:** Real-time bidirectional communication using Flask-SocketIO.
* **Error Handling:** Comprehensive error handling with user-friendly messages and graceful degradation.
* **Rate Limiting:** Built-in rate limiting for text inputs to prevent abuse.
* **Context Window Management:** Intelligent token management to stay within LLM context limits.


## 🧑🏻‍💻 Technologies Used

* **Backend Framework:** Python (Flask) with Flask-SocketIO for WebSocket support
* **Large Language Model (LLM):** OpenAI GPT-4o for intelligent conversation generation
* **Speech-to-Text (STT):** OpenAI Whisper API for accurate voice transcription
* **Text-to-Speech (TTS):** Murf AI for high-quality voice synthesis
* **Frontend Framework:** React 18.2.0 with modern hooks and components
* **Real-Time Communication:** Socket.IO (client) and Flask-SocketIO (server)
* **Dependency Management:** `pip` and `requirements.txt` for Python, `npm` for Node.js
* **Environment Variables:** `python-dotenv` for secure API key management
* **Logging:** `structlog` for structured, production-ready logging
* **Audio Processing:** Browser MediaRecorder API for voice capture, Web Audio API for playback


## 🗂 Project Structure

<pre>
📂 customer-success-agent/

├── backend/
│   ├── requirements.txt           # Python dependencies for the backend
│   ├── services/
│   │   ├── llm.py                # OpenAI GPT-4o integration and conversation management
│   │   ├── murf.py               # Murf AI TTS integration and audio generation
│   │   ├── whisper.py            # OpenAI Whisper STT integration
│   │   └── websocket_handler.py  # WebSocket event handlers and session management
│   └── src/
│       ├── app.py                # Flask application with SocketIO endpoints
│       └── cli.py                # Command-Line Interface for testing and debugging
│
├── frontend/
│   ├── package.json              # Node.js dependencies and scripts
│   ├── package-lock.json         # Locked dependency versions
│   ├── public/
│   │   └── index.html            # HTML template for React app
│   └── src/
│       ├── App.js                # Main React application component
│       ├── index.js              # React application entry point
│       ├── components/
│       │   ├── AudioPlayer.js    # Audio playback component with controls
│       │   ├── AudioPlayer.css   # Audio player styling
│       │   ├── ChatWindow.js     # Chat interface and message display
│       │   ├── ChatWindow.css    # Chat window styling
│       │   ├── MessageInput.js   # Text and voice input components
│       │   ├── MessageInput.css  # Message input styling
│       │   └── ErrorBoundary.js  # React error boundary for error handling
│       ├── hooks/
│       │   └── useMicrophone.js  # Custom React hook for microphone access
│       ├── services/
│       │   └── websocketService.js # WebSocket client service
│       └── styles/
│           └── App.css           # Main application styles
│
├── config.py                     # Centralized configuration management
├── .env                          # Environment variables (API keys)
├── .gitignore                    # Git ignore rules
└── README.md                     

</pre>


## 📁 Project Resources

Additional project resources, including demo materials and project documentation, are available in our Google Drive folder:

🔗 **[Project Drive Folder](https://drive.google.com/drive/folders/1iDxA5OhKZMQP_iUIfjDEyjpVLaYUknqf)**

The Drive folder contains:
* **AI Customer Success Agent.docx:** Comprehensive project documentation and design specifications.
* **Demo-Video.mp4:** Demo video showcasing the AI Customer Success Agent in action.

Feel free to explore these resources to see the application in action and access detailed project information.


## ⚙️ Setup Instructions

Follow these steps to get the AI Customer Success Agent running on your local machine.

### Prerequisites

* Python 3.8 or higher
* Node.js 14 or higher and npm
* API keys for:
    * OpenAI (for GPT-4o and Whisper)
    * Murf AI (for TTS)

### Backend Setup

1. **Clone the Repository:**
    Navigate to your desired directory in the terminal and clone the project:
    ```bash
    git clone <repository-url>
    cd customer-success-agent
    ```

2. **Create a Virtual Environment:**
    It's highly recommended to use a virtual environment to manage project dependencies.
    ```bash
    python3 -m venv venv
    ```

3. **Activate the Virtual Environment:**
    * **On macOS/Linux:**
        ```bash
        source venv/bin/activate
        ```
    * **On Windows (Command Prompt):**
        ```cmd
        .\venv\Scripts\activate
        ```
    * **On Windows (PowerShell):**
        ```powershell
        .\venv\Scripts\Activate.ps1
        ```

4. **Install Python Dependencies:**
    With your virtual environment activated, install all necessary Python packages:
    ```bash
    cd backend
    pip install -r requirements.txt
    ```

5. **Set Up Environment Variables:**
    Create a file named `.env` in the **root directory** of your project (the `customer-success-agent/` folder). Add your API keys to this file:

    ```ini
    OPENAI_API_KEY=your_openai_api_key_here
    MURF_API_KEY=your_murf_ai_api_key_here
    ```

    * **`OPENAI_API_KEY`**: Obtain this from your OpenAI account. This key is used for both GPT-4o (LLM) and Whisper (STT) APIs.
    * **`MURF_API_KEY`**: Obtain this from your Murf AI account for text-to-speech functionality.

6. **Run the Flask Backend Server:**
    Open your terminal, navigate to the `backend/src/` directory, and run the Flask server:
    ```bash
    cd backend/src/
    python app.py
    ```
    This will start the Flask server with SocketIO support, usually on `http://localhost:5000`. Keep this terminal window open.

    **Alternative:** You can also run it using Flask's development server:
    ```bash
    export FLASK_APP=app.py  # On macOS/Linux
    # or
    set FLASK_APP=app.py     # On Windows (Command Prompt)
    # or
    $env:FLASK_APP="app.py"  # On Windows (PowerShell)
    flask run
    ```

### Frontend Setup

1. **Install Node.js Dependencies:**
    Open a **new terminal window** (keep the backend server running in the first one). Navigate to the `frontend/` directory and install dependencies:
    ```bash
    cd frontend
    npm install
    ```

2. **Start the React Development Server:**
    With dependencies installed, start the React development server:
    ```bash
    npm start
    ```
    This will start the React development server, usually on `http://localhost:3000`. The browser should open automatically.

3. **Access the Application:**
    The application should now be accessible at `http://localhost:3000`. The frontend will automatically connect to the backend WebSocket server at `http://localhost:5000`.

### Configuration

The application uses a centralized configuration file (`config.py`) that can be customized. Key configuration options include:

* **LLM Settings:** Model selection, temperature, max tokens, context window management
* **TTS Settings:** Voice ID, speed, pitch, volume, audio format
* **STT Settings:** Language, response format, temperature
* **Flask Settings:** Host, port, CORS origins, debug mode
* **SocketIO Settings:** Async mode, ping timeout, ping interval
* **Session Management:** Inactivity timeout, cleanup interval
* **Rate Limiting:** Text input rate limits and maximum lengths

You can override any configuration value using environment variables. See `config.py` for details.


## 🧑🏻‍🔧 Local Testing with CLI

If you wish to test the backend logic (LLM responses, TTS generation, STT transcription, session management) directly from your terminal, you can use the `cli.py` script.

1. **Ensure your virtual environment is activated.**
2. **Navigate to the `backend/src/` directory:**
    ```bash
    cd backend/src/
    ```
3. **Run the CLI script:**
    ```bash
    python cli.py
    ```
    This provides a comprehensive menu-driven interface for:
    * **Service Testing:** Test LLM, Murf TTS, Whisper STT, and Session Manager
    * **Network Testing:** Test HTTP endpoints and WebSocket connections
    * **Configuration Testing:** Validate configuration and environment setup
    * **Performance Testing:** Load testing and benchmarking
    * **Handoff Analysis Testing:** Test human handoff detection logic
    * **Complete Test Suite:** Run all tests with detailed reporting

The CLI provides beautiful, color-coded output and detailed test results to help you debug and verify your setup.


## 🚀 Usage

### Starting a Conversation

1. **Choose Input Method:** When you first open the application, you'll see a welcome screen with options to choose between Text Chat and Voice Chat.

2. **Text Input:**
    * Select "Text" mode from the input controls.
    * Type your message in the text area.
    * Choose your preferred response format (Text, Audio, or Both).
    * Press Enter or click Send.

3. **Voice Input:**
    * Select "Voice" mode from the input controls.
    * Click the Record button and speak your message.
    * Click Stop when finished recording.
    * The audio will be automatically transcribed and sent to the agent.

### Response Formats

* **Text Only:** Receive responses as text messages only.
* **Audio Only:** Receive responses as audio playback only (useful for hands-free interactions).
* **Both:** Receive both text and audio responses (default for voice input).

### Human Handoff

The system automatically analyzes customer queries to determine if human assistance is needed. When a handoff is suggested:
* You'll see a handoff suggestion message with category and urgency.
* You can choose to "Connect to Human Agent" or "Continue with AI".
* If you accept, a handoff ticket will be created and you'll be connected to a human agent.

### Conversation Features

* **Conversation History:** All messages are maintained in the conversation context.
* **Sentiment Analysis:** The system analyzes customer sentiment in real-time.
* **Session Management:** Sessions are automatically managed with cleanup for inactive sessions.
* **Error Handling:** User-friendly error messages are displayed for any issues.


## 📊 API Endpoints

### HTTP Endpoints

* **`GET /`** - Root endpoint with application information
* **`GET /health`** - Health check endpoint for monitoring
* **`GET /status`** - Detailed status endpoint with metrics
* **`GET /sessions`** - Get information about active sessions
* **`DELETE /sessions/<session_id>`** - Terminate a specific session

### WebSocket Events

#### Client to Server:
* **`connect`** - Establish WebSocket connection
* **`text_input`** - Send text input to the agent
* **`audio_stream`** - Send audio stream chunks
* **`get_conversation_history`** - Request conversation history
* **`analyze_sentiment`** - Request sentiment analysis
* **`generate_summary`** - Request conversation summary
* **`request_human_assistance`** - Request human handoff
* **`ping`** - Connection health check

#### Server to Client:
* **`connection_established`** - Connection confirmation
* **`conversation_completed`** - Conversation response with text and/or audio
* **`processing_status`** - Processing stage updates (STT, LLM, TTS)
* **`handoff_suggestion`** - Human handoff suggestion
* **`human_handoff_initiated`** - Handoff confirmation
* **`error`** - Error messages
* **`pong`** - Ping response


## 🧑🏻‍🔬 Future Enhancements

* **Multi-Language Support:** Extend support for multiple languages in both STT and TTS.
* **Voice Cloning:** Allow customization of agent voice using voice cloning technology.
* **Advanced Analytics:** Dashboard for conversation analytics, sentiment trends, and performance metrics.
* **Integration with CRM:** Integrate with popular CRM systems for seamless customer data management.
* **Multi-Channel Support:** Extend support for email, SMS, and social media channels.
* **Advanced Handoff Logic:** More sophisticated handoff detection with machine learning models.
* **Conversation Summarization:** Automatic summarization of long conversations for agents.
* **Knowledge Base Integration:** Integrate with knowledge bases for more accurate responses.
* **Deployment:** Instructions for deploying to cloud platforms (AWS, Azure, GCP, Heroku).
* **Docker Support:** Containerization for easier deployment and scaling.
* **CI/CD Pipeline:** Automated testing and deployment pipelines.
* **Monitoring and Alerting:** Advanced monitoring and alerting for production environments.


## 🔒 Security Considerations

* **API Keys:** Never commit API keys to version control. Always use `.env` files and ensure they are in `.gitignore`.
* **Environment Variables:** Use environment variables for all sensitive configuration.
* **CORS:** Configure CORS origins appropriately for production environments.
* **Rate Limiting:** Implement additional rate limiting for production to prevent abuse.
* **Authentication:** Consider adding authentication for production deployments.
* **HTTPS:** Always use HTTPS in production for secure WebSocket connections.
* **Input Validation:** All user inputs are validated on both client and server sides.
* **Session Security:** Sessions are automatically cleaned up to prevent resource exhaustion.


## 🐛 Troubleshooting

### Backend Issues

* **API Key Errors:** Ensure your `.env` file is in the root directory and contains valid API keys.
* **Port Already in Use:** If port 5000 is already in use, change `FLASK_PORT` in `config.py` or set it as an environment variable.
* **Import Errors:** Ensure all dependencies are installed: `pip install -r backend/requirements.txt`
* **WebSocket Connection Failed:** Check that the Flask server is running and CORS is configured correctly.

### Frontend Issues

* **Connection Errors:** Ensure the backend server is running on `http://localhost:5000`.
* **Microphone Access:** Grant microphone permissions in your browser settings.
* **Audio Playback Issues:** Check browser compatibility and ensure audio codecs are supported.
* **Build Errors:** Clear `node_modules` and reinstall: `rm -rf node_modules && npm install`

### Common Solutions

* **Clear Browser Cache:** Clear your browser cache and reload the application.
* **Check Console Logs:** Check browser console and server logs for detailed error messages.
* **Verify API Keys:** Use the CLI tool to test API connectivity: `python backend/src/cli.py`
* **Restart Servers:** Restart both backend and frontend servers if issues persist.


## ✒️ Acknowledgments

* [OpenAI](https://openai.com/) for GPT-4o and Whisper APIs.
* [Murf AI](https://murf.ai/) for the powerful text-to-speech API.
* [Flask](https://flask.palletsprojects.com/en/latest/) for the robust web framework.
* [Flask-SocketIO](https://flask-socketio.readthedocs.io/) for WebSocket support.
* [React](https://react.dev/) for the modern frontend framework.
* [Socket.IO](https://socket.io/) for real-time communication.
* [Python](https://www.python.org/) for the programming language.
* [Structlog](https://www.structlog.org/) for structured logging.


## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.


## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.


## 📧 Contact

For questions, issues, or suggestions, please open an issue on the GitHub repository or contact the project maintainers.


---

**Built with ❤️ for exceptional customer experiences.**
