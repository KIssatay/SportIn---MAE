# SportIn - Sports-Focused Social Networking Application

SportIn is a mobile social networking platform designed specifically for athletes, fans, and coaches. Built with Flutter and Firebase, it provides a dedicated space for sports enthusiasts to connect, share achievements, discover content, and communicate within their sports communities.

## 🎯 Project Overview

SportIn addresses the gaps in current general-purpose social networks by offering:
- **For Athletes**: Professional sports profiles, achievement showcasing, career visibility
- **For Fans**: Personalized sports feeds, community discovery, focused content consumption
- **For Coaches**: Talent discovery, athlete evaluation, progress tracking, centralized communication

## 👥 Team

- **Issatay** (Group Leader) - Profile Module, Onboarding, Project Architecture, CI/CD
- **Rafi** - Feed Module, Search, Post Creation
- **Bektay** - Authentication, Messages, User Profile View

## 🏗️ Tech Stack

- **Framework**: Flutter 3.19.0+
- **Language**: Dart
- **Backend**: Firebase
  - Authentication
  - Cloud Firestore
  - Cloud Storage
  - Cloud Messaging (notifications)
- **State Management**: Provider
- **Architecture**: MVVM (Model-View-ViewModel)

## 📁 Project Structure

```
lib/
├── core/
│   ├── constants/          # App-wide constants (colors, strings, routes)
│   ├── theme/              # Theme configuration
│   ├── utils/              # Helper functions, validators
│   └── widgets/            # Reusable widgets
├── data/
│   ├── models/             # Data models (User, Post, Message, etc.)
│   ├── repositories/       # Repository pattern implementations
│   └── services/           # Firebase services, API calls
├── presentation/
│   ├── auth/               # Login, Signup screens
│   ├── onboarding/         # Sport selection onboarding
│   ├── profile/            # Profile view/edit
│   ├── feed/               # Post feed
│   ├── messages/           # Chat functionality
│   ├── search/             # Search screens
│   └── shared/             # Shared presentation components
└── main.dart
```

## 🚀 Getting Started

### Prerequisites

- Flutter SDK 3.19.0 or higher
- Dart SDK 3.3.0 or higher
- Android Studio / VS Code with Flutter extensions
- Firebase account
- Git

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/KIssatay/SportIn---MAE.git
   cd SportIn---MAE
   ```

2. **Install dependencies**
   ```bash
   flutter pub get
   ```

3. **Firebase Setup**
   - Create a Firebase project at [Firebase Console](https://console.firebase.google.com/)
   - Enable Authentication (Email/Password)
   - Create Cloud Firestore database
   - Enable Cloud Storage
   - Download `google-services.json` (Android) and `GoogleService-Info.plist` (iOS)
   - Place them in respective directories:
     - Android: `android/app/google-services.json`
     - iOS: `ios/Runner/GoogleService-Info.plist`
   - Run Firebase configuration:
     ```bash
     flutterfire configure
     ```

4. **Run the app**
   ```bash
   flutter run
   ```

## 🔄 Development Workflow

### Branching Strategy

- `main` — production-ready code (protected, requires PR review)
- `dev` — integration branch (default branch for development)
- `feature/*` — feature branches (e.g., `feature/profile-edit`, `feature/feed-filtering`)

### Development Process

1. Create feature branch from `dev`:
   ```bash
   git checkout dev
   git pull origin dev
   git checkout -b feature/your-feature-name
   ```

2. Make changes and commit:
   ```bash
   git add .
   git commit -m "feat: add profile edit functionality"
   ```

3. Push to remote:
   ```bash
   git push origin feature/your-feature-name
   ```

4. Create Pull Request to `dev` on GitHub

5. Request code review from a teammate

6. After approval, merge to `dev`

### Commit Message Convention

Follow conventional commits format:

- `feat:` — new feature
- `fix:` — bug fix
- `docs:` — documentation changes
- `refactor:` — code refactoring
- `test:` — adding or updating tests
- `chore:` — maintenance tasks

Examples:
```
feat: add sport selection onboarding screen
fix: resolve feed infinite scroll bug
docs: update README with Firebase setup
refactor: extract profile form into separate widget
```

## 📋 Module Responsibilities

### Issatay (Group Leader)
- **Onboarding & Sport Selection**
  - Sport selection screen (UFC, Football, F1, Tennis)
  - Save user preferences to Firestore
  - Navigate to main app after completion

- **Profile Module**
  - View profile screen
  - Edit profile functionality
  - Upload media (PDF/PNG/MP4) to Firebase Storage
  - CRUD operations for achievements, activities, skills

- **Project Setup & Architecture**
  - Initialize Flutter project
  - Set up folder structure
  - Configure Firebase
  - Set up Provider for state management
  - Create MVVM base classes

- **CI/CD & Deployment**
  - GitHub Actions workflows
  - Automated builds
  - Firebase App Distribution
  - Release management

### Rafi
- **Feed Module**
  - Personalized post feed based on selected sports
  - Sport filtering functionality
  - Infinite scroll implementation
  - Pull-to-refresh

- **Search Module**
  - Search by keywords, sport type, location, users
  - Search results display
  - Filter and sort options

- **Post Creation**
  - Create posts with text and images
  - Link posts to specific sports
  - Upload media to Firebase Storage

### Bektay
- **Authentication Module**
  - Firebase Auth integration (email/password)
  - Login screen
  - Signup screen
  - Session management
  - Password reset

- **Messages Module**
  - Chat list screen
  - Individual chat screen
  - Real-time messaging via Firestore
  - Message notifications

- **User Profile View**
  - View other user's profiles
  - "Message" button integration
  - Navigate to Messages module

## 🧪 Testing

Run tests:
```bash
flutter test
```

Run tests with coverage:
```bash
flutter test --coverage
```

## 🔧 Common Issues & Solutions

### Firebase Configuration Issues
- Ensure `google-services.json` and `GoogleService-Info.plist` are properly placed
- Run `flutterfire configure` after adding Firebase files
- Check that Firebase project has correct package name

### Build Errors
- Clean build folder: `flutter clean`
- Get dependencies: `flutter pub get`
- Rebuild: `flutter run`

### Hot Reload Not Working
- Stop and restart the app
- Check for syntax errors in recent changes

## 📚 Resources

- [Flutter Documentation](https://docs.flutter.dev/)
- [Firebase for Flutter](https://firebase.flutter.dev/)
- [Provider State Management](https://pub.dev/packages/provider)
- [MVVM Architecture Guide](https://docs.flutter.dev/development/data-and-backend/state-mgmt/options)

## 📝 License

This project is part of the MAE (Mobile Application Engineering) course at Asia Pacific University.

## 🤝 Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our development process and how to submit pull requests.

## 📧 Contact

For questions or issues, please contact the team through GitHub Issues or reach out to the group leader.

---

**Course**: Mobile Application Engineering (MAE)  
**Institution**: Asia Pacific University of Technology and Innovation (APU)  
