# Accesso

Accesso is a voice-operated Android application that assists visually impaired individuals and tourists by providing real-time scene recognition, navigation assistance, multilingual translation, and itinerary suggestions. Built during the TDSC Datathon - Spring 2025.

## Features

### Dual-Mode System

**Tourist Mode**
- Capture scenes and get AI-generated image descriptions with contextual understanding
- Translate foreign text (e.g., Japanese billboards) into the user's preferred language
- Ask follow-up questions about the image (e.g., "What's the name of this place?", "Is this a restaurant?")
- Discover and store favorite spots using MongoDB Atlas Vector Search for recommendations

**Visually Impaired Mode**
- One-tap capture for real-time scene description via speech
- Voice command-based interactions for hands-free operation
- Immediate audio feedback for seamless navigation and understanding
- All interactions powered by image recognition + conversational Q&A

### Core Capabilities
- **Scene Recognition**: AI-powered image analysis using Qwen models via Nebius API
- **Multilingual Support**: Real-time translation to 9 languages (Hindi, Tamil, Bengali, Telugu, Marathi, Gujarati, Kannada, Urdu, English)
- **Text-to-Speech**: Android TTS engine with offline/low-latency audio feedback
- **Camera Integration**: CameraX for image capture with compression and Firebase Storage upload
- **Interactive Chat**: Follow-up questions about captured scenes

## Tech Stack

- **Frontend**: Kotlin, Android SDK
- **AI/ML**: Qwen2-VL-72B-Instruct via Nebius API for image understanding and Q&A
- **Translation**: Google ML Kit Translation
- **Text-to-Speech**: Android TextToSpeech engine
- **Storage**: Firebase Storage for image hosting
- **Database**: MongoDB Atlas with Vector Search (for scene embeddings and recommendations)
- **UI**: Material Design, Lottie animations, View Binding
- **Camera**: CameraX (camera2, lifecycle, view)

## Architecture

```
SplashActivity -> PermissionCheckerActivity -> TransitionActivity -> touristHomeActivity
                                                                    |
                                                                    v
                                              MainActivity (Camera + AI Chat)
                                                                    |
                                                                    v
                                              discoverActivity (Translation)
```

## Setup

### Prerequisites
- Android Studio
- JDK 17
- Android SDK 24+ (minSdk), 35 (targetSdk)

### Installation

1. Clone the repository:
```bash
git clone https://github.com/codeEnthusiast21/buhackaccino.git
cd buhackaccino
```

2. Open in Android Studio and sync Gradle.

3. Add your `google-services.json` to the `app/` directory for Firebase integration.

4. Update the Nebius API key in `MainActivity.kt` (line 67) with your own key.

5. Build and run on an Android device or emulator.

### Required Permissions
- `CAMERA` - For scene capture
- `INTERNET` - For API calls and Firebase
- `RECORD_AUDIO` - For voice commands
- `POST_NOTIFICATIONS` - For system notifications

## Usage

1. Launch the app and wait for the splash animation.
2. Select your preferred language from the spinner.
3. Grant camera and accessibility permissions.
4. In Tourist Mode, tap the camera to capture a scene and ask questions.
5. In Visually Impaired Mode, use voice commands to interact with the app.
6. Swipe left in the camera view to access the Navigation screen.

## Screenshots

- Tourist home screen with place listings
- AI scene recognition with chat interface
- Transition animations
- Multilingual translation interface

## Built With

- Android Studio
- Kotlin
- Firebase (Storage, Analytics)
- Google ML Kit (Translation)
- CameraX
- Lottie
- Volley (HTTP client)
- Glide (Image loading)
- Material Design Components

