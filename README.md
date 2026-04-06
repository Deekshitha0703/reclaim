# Reclaim

Reclaim is a Flutter recovery-support app with an AI microservice for relapse-risk estimation and personalized recovery-plan guidance.

## What This Repository Contains

- Flutter client app for Android, iOS, web, desktop, and Windows
- FastAPI-based AI microservice for recovery plan inference
- ML training scripts and model conversion utilities
- Firebase integration (Auth, Firestore, Storage, Messaging)

## High-Level Architecture

1. Flutter app collects user progress, habits, and recovery signals.
2. App can call the local AI service over HTTP.
3. AI service predicts risk level and returns recovery goals/tips.
4. If model inference is unavailable, fallback logic can still produce guidance.

## Tech Stack

- Flutter (Dart)
- FastAPI + Uvicorn (Python)
- TensorFlow / scikit-learn model tooling
- Firebase (Core/Auth/Firestore/Storage/Messaging)

## Prerequisites

- Flutter SDK (compatible with this project)
- Dart SDK (via Flutter)
- Python 3.x for the AI service environment
- Firebase project configuration files already placed in platform folders

## Quick Start

### 1) Install Flutter dependencies

```powershell
flutter pub get
```

### 2) Set up and run AI service

From the repository root:

```powershell
python -m venv .venv
.venv\Scripts\activate
pip install -r ai_service/requirements.txt
uvicorn ai_service.app:app --reload --host 127.0.0.1 --port 8000
```

Health check:

```powershell
curl http://127.0.0.1:8000/health
```

### 3) Run Flutter app

In another terminal:

```powershell
flutter run
```

## VS Code Tasks (Already Included)

- Start AI Service (Uvicorn)
- Flutter Run
- Start API + Flutter (runs both in parallel)

Use Terminal -> Run Task in VS Code and pick the task label above.

## Testing

Flutter tests:

```powershell
flutter test
```

Python AI service tests (from repository root or ai_service folder):

```powershell
python -m pytest ai_service
```

## Important Folders

- `lib/` - Flutter app source (screens, providers, services, widgets)
- `test/` - Flutter tests
- `ai_service/` - FastAPI service and model inference logic
- `ml_training/` - model training pipelines and utilities
- `assets/models/` - bundled model assets for client inference

## Key Documentation

- `GETTING_STARTED_AI.md`
- `QUICK_START_AI.md`
- `FLUTTER_PYTHON_INTEGRATION.md`
- `FIRESTORE_SETUP.md`
- `ai_service/DEPLOYMENT.md`
- `ml_training/README.md`

## Notes

- The project includes multiple AI/ML paths (service inference, local model assets, and fallback logic), so review the docs above before production deployment.
- Firebase and platform configuration must match your own project setup before release builds.
