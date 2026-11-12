# 🎙️ AI-Voice Accessibility Assistant

An AI-powered bilingual voice assistant designed to make public administration communication more accessible and understandable.

The application allows users to communicate with an AI assistant through English voice input and receive responses in both **English and German**, including audio playback for both languages.

The project combines speech recognition, real-time audio processing, large language models, machine learning and speech synthesis to create an accessible conversational experience.

## 🎯 Project Objectives

The main objective is to develop an intelligent voice assistant that helps people understand administrative information without struggling with complicated language or written communication.

The system aims to:

- Enable users to interact with an AI assistant using natural English speech.
- Convert spoken input into text using automatic speech recognition.
- Generate contextually relevant responses using Large Language Models (LLMs).
- Provide responses in both English and German.
- Generate natural-sounding speech in both languages.
- Support real-time voice interaction.
- Improve accessibility through voice-based communication.

## ✨ Key Features

- **Voice Input:** Capture user speech through a microphone.
- **Speech Recognition:** Convert English speech into text using Whisper.
- **Voice Activity Detection:** Detect speech and silence using Silero VAD.
- **Audio Processing:** Process and prepare audio using librosa.
- **AI Response Generation:** Generate contextual responses using an LLM.
- **Bilingual Responses:** Display answers in English and German.
- **Speech Synthesis:** Generate English and German audio using Piper or Coqui TTS.
- **Real-Time Communication:** Support audio streaming through WebRTC.
- **Interactive Interface:** Display conversations and provide audio playback controls.

## 🏗️ System Architecture

The application follows a modular client-server architecture.

### Voice Processing Pipeline

1. **React Frontend:** Captures microphone input.
2. **WebRTC:** Transfers audio between the frontend and backend.
3. **Silero VAD:** Detects speech activity and speech boundaries.
4. **librosa:** Performs audio processing and preparation.
5. **Whisper:** Converts English speech into text.
6. **LLM:** Understands the user's question and generates an English response.
7. **Translation Service:** Translates the English response into German.
8. **Piper / Coqui TTS:** Generates English and German speech.
9. **React Frontend:** Displays both responses and provides audio playback.

### Architecture Overview

```text
                    USER
                      |
                      v
              React Frontend
                      |
                      v
                   WebRTC
                      |
                      v
                FastAPI Backend
                      |
                      v
               Silero VAD
                      |
                      v
                  librosa
                      |
                      v
                   Whisper
                      |
                      v
               English Transcript
                      |
                      v
                  LLM API
                      |
                      v
               English Response
                      |
                      v
             Translation Service
                      |
                +-----+-----+
                |           |
                v           v
           English       German
             Text          Text
                |           |
                v           v
            Piper /      Piper /
            Coqui TTS    Coqui TTS
                |           |
                v           v
          English Audio German Audio
                |           |
                +-----+-----+
                      |
                      v
               React Frontend
                      |
                      v
          Display Both Responses
             + Audio Playback
```

## 🛠️ Technology Stack

| Component | Technology | Purpose |
|---|---|---|
| Programming Language | Python | Backend and AI development |
| Frontend | React, TypeScript | Interactive user interface |
| Backend | FastAPI | REST APIs and backend services |
| Speech Recognition | Whisper | Speech-to-text conversion |
| Speech Synthesis | Piper / Coqui TTS | Text-to-speech generation |
| Voice Activity Detection | Silero VAD | Speech and silence detection |
| Real-Time Communication | WebRTC | Real-time audio streaming |
| Audio Processing | librosa | Audio analysis and processing |
| AI Response Generation | LLM API | Contextual response generation |
| Translation | Translation model / API | English-to-German translation |
| Containerization | Docker | Application deployment |

## 📁 Project Structure

```text
voice-accessibility-assistant/
│
├── backend/
│   ├── app/
│   │   ├── main.py
│   │   │
│   │   ├── api/
│   │   │   ├── voice.py
│   │   │   ├── conversation.py
│   │   │   └── audio.py
│   │   │
│   │   ├── services/
│   │   │   ├── whisper_service.py
│   │   │   ├── vad_service.py
│   │   │   ├── audio_processing.py
│   │   │   ├── llm_service.py
│   │   │   ├── translation_service.py
│   │   │   └── tts_service.py
│   │   │
│   │   ├── realtime/
│   │   │   └── webrtc_service.py
│   │   │
│   │   └── config/
│   │
│   └── requirements.txt
│
├── frontend/
│   └── src/
│       ├── components/
│       │   ├── MicrophoneButton.tsx
│       │   ├── Conversation.tsx
│       │   ├── LanguageResponse.tsx
│       │   └── AudioPlayer.tsx
│       │
│       ├── services/
│       │   └── voiceService.ts
│       │
│       └── App.tsx
│
├── evaluation/
│   ├── whisper_evaluation.py
│   ├── vad_evaluation.py
│   ├── tts_evaluation.py
│   └── latency_evaluation.py
│
├── docker-compose.yml
└── README.md
```

## ⚙️ Installation and Setup

### Prerequisites

Make sure the following tools are installed:

- Python 3.11+
- Node.js 22+
- npm
- Git
- Docker (optional, for containerized deployment)

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/voice-accessibility-assistant.git

cd voice-accessibility-assistant
```

### 2. Backend Setup

Navigate to the backend directory:

```bash
cd backend
```

Create a virtual environment:

```bash
python -m venv venv
```

Activate the environment:

**macOS / Linux:**

```bash
source venv/bin/activate
```

**Windows:**

```bash
venv\Scripts\activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Start the backend server:

```bash
uvicorn app.main:app --reload
```

Backend API:

```text
http://localhost:8000
```

API documentation:

```text
http://localhost:8000/docs
```

### 3. Frontend Setup

Open another terminal:

```bash
cd frontend
```

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

Open the application in your browser using the local URL displayed by Vite or Next.js, depending on the frontend setup.

## 📊 AI Model Evaluation

A dedicated evaluation module is included to measure the performance and reliability of the voice assistant.

| Evaluation Module | Evaluation Metrics |
|---|---|
| Whisper Evaluation | Word Error Rate (WER) |
| VAD Evaluation | Precision, Recall, F1-score |
| TTS Evaluation | Speech intelligibility and naturalness |
| Latency Evaluation | End-to-end response time |

The evaluation framework will help identify performance bottlenecks and improve the quality of speech processing.

## 🔐 Privacy and Security

The application is designed with privacy and responsible AI development in mind.

Planned considerations include:

- Secure handling of microphone input.
- Avoiding unnecessary audio retention.
- Secure API key management through environment variables.
- HTTPS for production communication.
- Explicit microphone permissions.
- Transparent AI-generated responses.

## 🚀 Development Roadmap

- [ ] Set up the FastAPI backend.
- [ ] Develop the React frontend.
- [ ] Implement microphone recording.
- [ ] Integrate Whisper for speech recognition.
- [ ] Implement Silero VAD.
- [ ] Integrate librosa for audio processing.
- [ ] Implement LLM-based response generation.
- [ ] Integrate English-to-German translation.
- [ ] Implement Piper / Coqui TTS.
- [ ] Integrate WebRTC for real-time communication.
- [ ] Build bilingual response and audio playback interfaces.
- [ ] Implement model evaluation and latency benchmarking.
- [ ] Dockerize the application.
- [ ] Deploy the application to the cloud.

## 🎯 Expected Outcome

The final application will allow users to ask questions through English voice input and receive understandable responses in both English and German, with independent audio playback for each language.

The project demonstrates practical applications of speech AI, real-time communication, audio engineering, LLM integration and accessible conversational technology.

## 📌 Project Status

**Currently in development.**

More features, implementation details and evaluation results will be added as development progresses.
