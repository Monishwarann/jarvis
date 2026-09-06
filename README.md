# 🤖 JARVIS (MARK LI) — Advanced Multimodal AI Assistant & Autonomous Voice Agent

[![Python 3.11](https://img.shields.io/badge/python-3.11-blue.svg)](https://www.python.org/downloads/release/python-3110/)
[![Tests](https://img.shields.io/badge/unit%20tests-50%20passed-brightgreen.svg)]()
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Platform: Windows 10/11](https://img.shields.io/badge/platform-Windows%2010%2F11-0078D6.svg)]()
[![FastAPI Web Dashboard](https://img.shields.io/badge/Web%20Dashboard-FastAPI%20%7C%20WebSocket-009688.svg)]()
[![GitHub Repo](https://img.shields.io/badge/GitHub-Monishwarann%2Fjarvis-black?logo=github)](https://github.com/Monishwarann/jarvis)

**JARVIS (MARK LI)** is an autonomous, multimodal personal AI assistant designed for Windows 10/11. It combines real-time 2-way voice calls over WhatsApp Desktop, computer vision, Windows OS automation, physical/simulated drone flight control, local offline LLM reasoning (Ollama), real-time cloud multimodal streaming (Gemini Live API), an encrypted FastAPI Web Dashboard, and an extensible zero-code plugin engine.

---

## 📸 Overview & Key Modules

```
 ┌─────────────────────────────────────────────────────────────────────────────────┐
 │                                   JARVIS HUD                                    │
 │    ┌─────────────────────────┐  ┌─────────────────────────┐  ┌────────────────┐ │
 │    │ Visual Waveform & Audio │  │ Camera & Vision Engine  │  │ GPU/CPU Telem  │ │
 │    └─────────────────────────┘  └─────────────────────────┘  └────────────────┘ │
 └────────────────────────────────────────┬────────────────────────────────────────┘
                                          │
    ┌─────────────────────────────────────┼─────────────────────────────────────┐
    │                                     │                                     │
    ▼                                     ▼                                     ▼
┌───────────────────────┐     ┌───────────────────────┐     ┌───────────────────────┐
│ 📞 WhatsApp Voice     │     │ 🌐 Encrypted FastAPI  │     │ 🚁 Drone & Hardware   │
│   Bridge (WASAPI+STT) │     │   Web Dashboard :8000 │     │   Flight Controller   │
└───────────────────────┘     └───────────────────────┘     └───────────────────────┘
    │                                     │                                     │
    ▼                                     ▼                                     ▼
┌───────────────────────┐     ┌───────────────────────┐     ┌───────────────────────┐
│ 🧠 Hybrid Reasoning   │     │ ⚡ CUDA Speech Engine │     │ ⚙️ 20+ OS & Computer  │
│   (Ollama / Gemini)   │     │   (Faster-Whisper)    │     │   Action Modules      │
└───────────────────────┘     └───────────────────────┘     └───────────────────────┘
```

---

## 🌟 Key Highlights & Feature Matrix

### 🎙️ Autonomous 2-Way WhatsApp Voice Bridge
- **Automated Calling**: Uses Windows Accessibility (UI Automation / PyAutoGUI) to locate contacts and initiate phone/video calls automatically.
- **Direct WASAPI Capture**: Hooks directly into Windows Audio Session API (WASAPI) loopback devices to record incoming caller audio with zero acoustic degradation.
- **CUDA Speech-to-Text**: Processes recorded audio chunks through NVIDIA CUDA-accelerated `faster-whisper` for ultra-fast, accurate transcription (with automatic INT8 CPU fallback).
- **Adaptive VAD**: Silero-powered Voice Activity Detection filters background noise, detecting exact speech start/end boundaries.
- **Echo Cancellation & Cooldown**: Intelligent audio gating discards self-heard TTS output and enforces acoustic cooldown intervals to prevent audio feedback loops.
- **Synthesized Voice Feedback**: Streams responses back into WhatsApp via `EdgeTTS` routed through **VB-Audio Virtual Cable**.

### 🧠 Dual Multimodal Engine (Cloud + Offline)
- **Google Gemini Live API**: WebSocket-based real-time multimodal streaming with video, screen frames, and high-fidelity audio responses.
- **Local Intelligence (Ollama)**: Full offline operation using models like `llama3.2`, `llama3.1`, `qwen`, or `gemma` with 0ms cloud latency and complete data privacy.

### 🌐 Encrypted FastAPI Web Dashboard (`:8000`)
- **Real-Time Web Panel**: Built-in HTTP server providing system management, live streaming assistant logs, and telemetry charts.
- **AES-256-CBC Security**: Application-layer encrypted WebSocket and REST communications derived from session handshake keys.
- **Remote File Hub**: Supports chunked file uploading and downloading up to 500MB directly to dedicated user upload folders.

### 🚁 KY-UFO Drone Flight Controller
- **UDP Socket Communication**: Direct telemetry parsing and command transmission for physical and simulated KY-UFO drones.
- **Safety Protocol**: Automatic sensor calibration, altitude hold, flight trajectory commands, and emergency kill-switch functionality.

### 🏋️ Computer Vision & Pose Tracking
- **Push-up & Exercise Counter**: Real-time pose landmark estimation using OpenCV & MediaPipe to count reps and evaluate posture accuracy via camera feed.
- **Screen & OCR Processor**: Captures active displays, extracts text via OCR, locates UI buttons, and enables visual desktop automation.

### 💻 20+ OS & Computer Action Modules
- **Dev Agent**: Autonomous coding assistant capable of writing, debugging, testing, and running terminal commands.
- **System Automation**: Volume adjustment, display brightness control, Wi-Fi/Bluetooth toggles, mouse/keyboard macro execution.
- **Document & File Processor**: PDF, DOCX, CSV parsing, smart file search, organization, and metadata indexer.
- **Browser & Media Manager**: Chrome/Edge navigation, YouTube search, background video playback, and video uploader automation.
- **Travel & Utilities**: Real-time weather reporting, flight finder, game library update checker, and proactive background reminders.

---

## 📋 System Prerequisites

| Component | Minimum Requirement | Recommended |
|---|---|---|
| **Operating System** | Windows 10/11 (64-bit) | Windows 11 (64-bit) |
| **Python** | Python 3.11 | Python 3.11 |
| **Processor** | Intel Core i5 / AMD Ryzen 5 | Intel Core i7/i9 or AMD Ryzen 7/9 |
| **GPU** | CPU supported | NVIDIA GPU (4GB+ VRAM, CUDA 11.8 / 12.x) |
| **Virtual Audio** | Required for WhatsApp Voice Calls | [VB-Audio Virtual Cable](https://vb-audio.com/Cable/) |
| **Local LLM** | Ollama | [Ollama](https://ollama.com/) with `llama3.2` |

---

## 🛠️ Step-by-Step Installation Guide

### 1. Clone the Repository

```powershell
git clone https://github.com/Monishwarann/jarvis.git
cd jarvis
```

### 2. Set Up Python Environment

```powershell
python -m venv .venv
.\.venv\Scripts\activate
```

### 3. Install Dependencies

```powershell
pip install -r requirements.txt
```

> **For PyTorch with NVIDIA CUDA Support**:
> To enable hardware-accelerated speech recognition on NVIDIA graphics cards:
> ```powershell
> pip install torch torchaudio --index-url https://download.pytorch.org/whl/cu118
> ```

### 4. Application Configuration

Copy the example configuration template:

```powershell
Copy-Item config\api_keys.json.example config\api_keys.json
```

Edit `config/api_keys.json`:
```json
{
    "gemini_api_key": "YOUR_GEMINI_API_KEY",
    "os_system": "windows",
    "camera_index": 0,
    "llm_provider": "ollama",
    "llm_model": "llama3.2",
    "llm_url": "http://localhost:11434",
    "plugins_enabled": {
        "whatsapp_monitor": true,
        "whatsapp_voice_bridge": true,
        "ky_ufo_drone": true
    },
    "assistant_name": "JARVIS",
    "user_name": "Sir",
    "ui_color": "#00d4ff"
}
```

### 5. Setup Local LLM (Ollama)

1. Download and install **Ollama** from [https://ollama.com](https://ollama.com).
2. Pull the recommended model:
   ```powershell
   ollama pull llama3.2
   ```
3. Start the server:
   ```powershell
   ollama serve
   ```

### 6. Setup VB-Audio Virtual Cable (for WhatsApp Calls)

1. Download and install **VB-Audio Virtual Cable** from [https://vb-audio.com/Cable/](https://vb-audio.com/Cable/).
2. Open **WhatsApp Desktop** -> **Settings** -> **Audio & Video**:
   - Set **Microphone** to: `CABLE Output (VB-Audio Virtual Cable)`
   - Set **Speakers** to: `Default System Speaker`

---

## 🚀 Running JARVIS

### Launching the Full HUD Interface
Starts the futuristic PyQt6 dashboard with interactive waveforms, telemetry graphs, camera feed, and voice control:

```powershell
python main.py
```

### Launching the Web Dashboard Server
Starts the AES-256 encrypted FastAPI HTTP & WebSocket web dashboard on port 8000:

```powershell
python dashboard/server.py
```

Access via browser at: `http://localhost:8000`

### Launching Autonomous WhatsApp Voice Bridge
Initiates an autonomous 2-way AI phone conversation with a specific contact:

```powershell
python live_test_bridge.py "<contact_name>" --debug-audio
```

*Example:*
```powershell
python live_test_bridge.py "John Doe" --debug-audio
```

---

## 📂 Project Architecture & Directory Structure

```
jarvis/
├── main.py                          # Main PyQt6 HUD entrypoint & Gemini Live event loop
├── ui.py                            # Futuristic HUD interface, canvas, and widgets
├── setup.py                         # Interactive first-time setup wizard
├── live_test_bridge.py              # Autonomous 2-way WhatsApp call runner
├── check_uia.py                     # Windows UI Automation inspector tool
├── list_windows.py                  # Active Windows handles inspector
├── dump_devices.py                  # WASAPI audio input/output enumeration utility
├── inspect_whatsapp.py              # WhatsApp UIA hierarchy analyzer
├── inspect_whatsapp_ui.py           # Deep WhatsApp window automation debugger
├── requirements.txt                 # Manifest of required Python packages
├── LICENSE                          # MIT License file
├── README.md                        # Project documentation
│
├── core/                            # Core System Engines
│   ├── llm_client.py                # Multi-provider LLM router (Ollama, Gemini, OpenAI)
│   ├── stt.py                       # CUDA Faster-Whisper & Vosk speech-to-text
│   ├── tts.py                       # EdgeTTS streaming synthesis & audio output routing
│   ├── plugin_loader.py             # Isolated dynamic plugin manager
│   └── installer.py                 # Automated dependency installer helper
│
├── actions/                         # 20+ Specialized OS & Computer Automation Modules
│   ├── dev_agent.py                 # Autonomous code writer, terminal exec, & debugger
│   ├── browser_control.py           # Chrome/Edge tab, search, & navigation manager
│   ├── computer_control.py          # Mouse, keyboard shortcut, & macro controller
│   ├── computer_settings.py         # Volume, brightness, Wi-Fi, & Bluetooth toggles
│   ├── screen_processor.py          # Real-time screen capture & OCR targeting
│   ├── pushup_counter.py            # MediaPipe vision exercise rep counter
│   ├── file_controller.py           # Smart file search, batch rename, & folder operations
│   ├── file_processor.py            # PDF, DOCX, CSV parsing & document text extractor
│   ├── youtube_video.py             # YouTube search, playback, & downloader
│   ├── upload_video.py              # Social video uploader automation
│   ├── game_updater.py              # Game library patch checker & launcher
│   ├── flight_finder.py             # Flight tracker & travel price locator
│   ├── background_monitor.py        # System background activity watcher
│   ├── system_monitor.py            # Hardware stats (CPU/GPU/RAM/Network telemetry)
│   ├── proactive.py                 # Proactive suggestions & alert engine
│   ├── reminder.py                  # Alarm & notification scheduler
│   ├── code_helper.py               # AI programming syntax & refactoring helper
│   ├── desktop.py                   # Desktop icon & window snap controller
│   ├── open_app.py                  # Application launcher & process monitor
│   ├── send_message.py              # Multi-channel messaging automation
│   ├── weather_report.py            # Live weather forecast provider
│   └── web_search.py                # Web search & scraper agent
│
├── plugins/                         # Dynamic Plug-and-Play Modules
│   ├── whatsapp_voice_bridge.py     # 2-way call state machine & WASAPI VAD loopback
│   ├── whatsapp_desktop_call.py     # WhatsApp UIA contact search & caller driver
│   ├── whatsapp_monitor.py          # WhatsApp incoming message watcher
│   └── ky_ufo_drone.py              # Drone UDP socket telemetry & flight control
│
├── dashboard/                       # FastAPI Web Control Panel
│   ├── server.py                    # FastAPI server with AES-256 WebSocket security
│   └── static/                      # HTML, JS, CSS dashboard assets
│
├── memory/                          # Context & Memory Management
│   ├── memory_manager.py            # Persistent dialogue & context vector store
│   └── config_manager.py            # JSON configuration reader/writer
│
├── tests/                           # Unit Test Suite (50+ Tests)
│   ├── test_whatsapp_voice_bridge.py# Tests for call states & audio safety loops
│   ├── test_whatsapp_desktop_call.py# Tests for Windows UI automation drivers
│   ├── test_whatsapp_desktop_logic.py# Tests for caller state machine logic
│   └── test_ky_ufo_drone.py         # Tests for drone telemetry & flight safety
│
└── config/
    └── api_keys.json.example        # Configuration blueprint template
```

---

## 🧪 Testing & Verification

Run the full automated unit test suite:

```powershell
python -m unittest discover tests
```

### Individual Diagnostic Tools

- **WASAPI Audio Device Enumeration**:
  ```powershell
  python dump_devices.py
  ```
- **Audio Loopback & VAD Diagnostic**:
  ```powershell
  python -c "from live_test_bridge import diagnostic_audio_test; diagnostic_audio_test()"
  ```
- **Ollama Connection & LLM Readiness**:
  ```powershell
  python -c "from core.llm_client import check_llm_readiness; check_llm_readiness()"
  ```

---

## 🧩 Creating Custom Plugins

Creating a plugin for JARVIS is simple. Just drop a Python file into `plugins/`:

```python
# plugins/my_custom_plugin.py

class Plugin:
    def __init__(self, jarvis_core):
        self.jarvis = jarvis_core
        self.name = "My Custom Plugin"

    def register(self):
        print(f"[{self.name}] Registered successfully!")

    def execute(self, command: str) -> str:
        if "hello" in command.lower():
            return "Greetings! How can I assist you today?"
        return ""
```

On next startup, JARVIS automatically loads `my_custom_plugin.py` with full error isolation.

---

## 📜 License

This project is released under the **[MIT License](LICENSE)**.

Copyright (c) 2026 **[Monishwarann](https://github.com/Monishwarann)**.
