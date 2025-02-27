# 🧠 Kortana - Privacy-First Ambient Intelligence
**Your always-available guardian for devices, time, and space**  
*"Zero phoning home - 100% local-first where possible"*

[![AGPL-3.0](https://img.shields.io/badge/License-AGPL_v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![Flutter](https://img.shields.io/badge/Flutter-3.19%2B-02569B?logo=flutter)](https://flutter.dev)

![Kortana Demo](https://via.placeholder.com/800x400.png?text=Mobile+UI+with+Alarms%2C+IoT+Controls%2C+Voice+Auth)

## 🌟 Core Features

### 🕰️ Advanced Alarm System

- **Screen Saver Mode**: Dims/Blacks out screen when idle (OLED-safe)
- **Motion Wake**: Front camera detects movement to wake device
- **Alarm Types**:
  | Type          | Description                          |
  |---------------|--------------------------------------|
  | Locked        | Cannot dismiss without auth          |
  | Geo-Fenced    | Triggers when entering locations     |
  | Recurring     | Custom schedules (cron-like rules)   |
  | Voiceprint    | Requires "Stop" in enrolled voice    |
- **Customization**:
```yaml
  alarms:
    - title: "Morning Run"
      sound: nature_stream.mp3
      vibration: morse
      pre_wake: 
        lights: 10% over 30m
        thermostat: 22°C
```

### 🎤 Voice & Presence
- **Voice Imprint Auth**:
```bash
  # Enroll via 3 phrase repetition
  kortana-cli voice-enroll --user alice --phrases "stop alarm" "lights on" "emergency mute"
```
- **Find My Device**:
```
  Shout "Kortana, ping!" within earshot → Device responds with unique LED pattern/sound
``` 
- **Conversational Memory**:
```
  "Remind me to water plants when kitchen lights turn on"
  → Creates IoT-triggered reminder
```

### 🏠 IoT Orchestration
- **Google Home Integration**:
```dart
  final googleHome = GoogleHomeAPI(
    clientId: 'YOUR_CLIENT_ID',
    scopes: [GoogleHomeScopes.controlDevices],
  );
  await googleHome.setThermostat(deviceId: 'nest-123', temp: 21.5);
```
- **Local Device Control**:
```bash
  # MQTT-based control for local devices
  kortana-cli iot --protocol mqtt --topic home/living-room/light --command dim=50%
```

## 🛠️ Tech Stack

```text
Frontend:
  Flutter 3.19+ · Dart 3.3 · Riverpod · Hive

Local AI:
  MediaPipe Tasks · TensorFlow Lite · ONNX Runtime

Cloud Sync (Optional):
  Firebase Auth · Firestore · self-hosted Supabase

IoT Protocols:
  MQTT · Matter · Google Home Local SDK
```

## 🚀 Installation

### Mobile (Android/iOS)
```bash
flutter pub get
flutter build apk --release --target-platform android-arm64

# Enable camera wake:
adb shell settings put system screen_off_timeout 86400000  # 24h timeout
```

### Google Home Setup
1. Create OAuth client: [Google Cloud Console](https://console.cloud.google.com)
2. Add credentials:
```yaml
# config/google_home.yaml
client_id: "your-client-id.apps.googleusercontent.com"
client_secret: "GOCSPX-your-secret"
redirect_uri: "com.kortana.app:/oauth2redirect"
```

## 🔧 Configuration

```yaml
# config/device_policies.yaml
screen:
  dim_after: 5m
  wake_on:
    motion: true
    decibel_threshold: 65dB

alarms:
  default_sound: waves.mp3
  escalation:
    - after: 1m → volume +20%
    - after: 3m → lights strobe

privacy:
  voice_data: local_only
  camera_frames: never_stored
```

## 🤝 Contributing

By contributing, you agree to:
1. **Irrevocably license** all code to Kortana Project
2. **Never redistribute** modified versions commercially
3. **Maintain compatibility** with core privacy principles

```bash
# Submit features:
git checkout -b feat/voice-imprint
flutter analyze --fatal-infos
dart format . && dart test
```

---

**Why AGPL-3.0?** Ensures all derivatives must:  
- Disclose source code  
- Preserve privacy features  
- Not commercialize without our consent  

*Third-party service data (Google, Spotify) governed by their respective policies*