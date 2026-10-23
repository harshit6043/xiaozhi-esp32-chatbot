# 🤖 XiaoChi Chatbot — ESP32 AI Voice Assistant

A low-latency, cloud-connected AI voice assistant built using an **ESP32 microcontroller**, **INMP441 I2S microphone**, **MAX98357A I2S audio amplifier**, and an **I2C OLED display**.

XiaoChi is designed to capture voice input, communicate with a cloud-based AI service, and deliver spoken responses while displaying useful information on a compact screen.

## ✨ Features

- 🎙️ **Voice Input:** Captures audio through the INMP441 digital I2S microphone.
- 🧠 **Cloud AI Integration:** Connects to a compatible AI service for intelligent responses.
- 🔊 **Voice Output:** Plays audio through the MAX98357A amplifier and a compatible speaker.
- 🖥️ **OLED Interface:** Displays status, listening indicators, and response text.
- 📶 **Wi-Fi Connectivity:** Enables communication with cloud services.
- ⚡ **Low-Latency Design:** Optimizes the audio and network workflow for responsive conversations.
- 🔧 **Embedded Design:** Integrates audio input, output, networking, and display functions on an ESP32.

*Actual performance and features depend on the firmware, AI provider, network conditions, and ESP32 variant.*

## 🧰 Hardware Requirements

| Component | Purpose |
|---|---|
| ESP32 development board | Main controller and Wi-Fi connectivity |
| INMP441 I2S microphone | Digital audio input |
| MAX98357A I2S amplifier | Audio output amplification |
| Compatible speaker | Plays assistant responses |
| I2C OLED display | Shows status and text |
| USB cable and suitable power supply | Programming and power |
| Jumper wires and breadboard | Prototyping and connections |

## 🏗️ System Architecture

```text
        User Voice
            │
            ▼
     INMP441 Microphone
            │ I2S
            ▼
        ESP32 Board
        ├── I2C OLED
        │     └── Status / Text
        │
        ├── Wi-Fi Connection
        │     └── Cloud AI Service
        │             └── AI Response
        │
        └── I2S Audio Output
                  │
                  ▼
           MAX98357A Amplifier
                  │
                  ▼
                Speaker
```

## 🔌 Hardware Connections

**Important:** GPIO assignments depend on your ESP32 board and existing wiring. The table below intentionally leaves pin numbers unspecified.

| Module | Signal | ESP32 Connection |
|---|---|---|
| INMP441 | SCK / BCLK | Configure GPIO |
| INMP441 | WS / LRCL | Configure GPIO |
| INMP441 | SD | Configure GPIO |
| INMP441 | VDD, GND | Compatible power and ground |
| MAX98357A | BCLK | Configure GPIO |
| MAX98357A | LRC / WS | Configure GPIO |
| MAX98357A | DIN | Configure GPIO |
| MAX98357A | VIN, GND | Compatible power and ground |
| OLED | SDA, SCL | Configure I2C pins |
| OLED | VCC, GND | Compatible power and ground |

Check your specific module documentation for voltage requirements and wiring. Do not connect the speaker directly to ESP32 GPIO pins.

## 💻 Software and Libraries

The software stack may include:

- **Arduino IDE** or PlatformIO
- ESP32 board support package
- `WiFi.h` for network connectivity
- `driver/i2s_std.h` or a compatible I2S audio library
- `Wire.h` for I2C communication
- `Adafruit_GFX` and `Adafruit_SSD1306` for compatible OLED displays
- An HTTP, WebSocket, or other supported client for cloud communication
- A compatible AI API or voice-processing service

Install only the libraries required by your actual firmware.

## ⚙️ Setup Instructions

### 1. Clone the repository

```bash
git clone https://github.com/harshit6043
cd XiaoChi-Chatbot
```

### 2. Configure the ESP32 environment

1. Install the Arduino IDE or PlatformIO.
2. Install ESP32 board support.
3. Select the correct ESP32 board and serial port.
4. Install the libraries used by your firmware.

### 3. Configure credentials

Provide your Wi-Fi credentials and cloud service credentials through a private configuration file or a secure secrets mechanism.

### 4. Configure the hardware

Set the I2S microphone pins, I2S amplifier pins, OLED I2C address, and display settings to match your physical connections.

### 5. Upload and test

Upload the firmware and test each subsystem individually:

1. ESP32 boots successfully.
2. OLED initializes and displays status.
3. Wi-Fi connects.
4. Microphone captures audio.
5. Cloud service returns a response.
6. Amplifier plays the response through the speaker.

## 🔄 Expected Workflow

1. The ESP32 initializes its peripherals.
2. The OLED displays the assistant's current state.
3. The microphone captures the user's voice.
4. The firmware sends audio or processed speech to the configured service.
5. The AI or voice-processing service generates a response.
6. The assistant displays the response and plays audio when supported by the implementation.

Speech recognition, AI inference, and text-to-speech may be separate cloud services depending on your architecture.

## 🔒 Security and Privacy

- Keep credentials out of source control.
- Use HTTPS or secure WebSocket connections where supported.
- Validate server responses and handle network timeouts.
- Explain to users when voice data is transmitted to external services.
- Avoid storing voice recordings unless necessary and appropriately protected.

## 🛠️ Troubleshooting

| Problem | Things to check |
|---|---|
| OLED remains blank | I2C address, SDA/SCL wiring, display driver, and power |
| Microphone captures silence | I2S pin configuration, clock settings, and microphone wiring |
| No speaker output | Amplifier power, I2S format, BCLK/WS/DIN pins, and speaker wiring |
| Wi-Fi fails | SSID, password, signal strength, and router compatibility |
| AI response fails | API credentials, endpoint, request format, and service availability |
| Slow response | Network latency, audio buffering, and cloud processing time |

## 🚀 Future Improvements

- Wake-word detection
- Streaming speech recognition
- Streaming text-to-speech
- Conversation history
- Multilingual voice interaction
- Improved audio buffering and noise reduction
- Battery-powered portable operation
- Animated OLED status interface
- Interruptible speech playback


## 👨‍💻 Project

**Name:** XiaoChi Chatbot  
**Platform:** ESP32  
**Category:** AI, IoT, Embedded Systems, Voice Interfaces





