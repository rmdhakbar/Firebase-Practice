# Firebase Task Manager 📝

A Flutter task management application that demonstrates Firebase integration including Authentication, Firestore Database, and Storage functionality.

## 🚀 Features

- **User Authentication**: Sign up and login with Firebase Auth
- **Task Management**: Create, view, and manage tasks
- **Date Selection**: Schedule tasks with date picker
- **Color Customization**: Choose colors for your tasks
- **Image Upload**: Attach images to tasks using Firebase Storage
- **Real-time Updates**: Tasks update in real-time using Firestore streams
- **Responsive UI**: Clean and intuitive user interface

## 📱 Screenshots

<!-- Add your app screenshots here -->

## 🛠️ Technologies Used

- **Flutter**: Cross-platform mobile app development
- **Firebase Core**: Firebase SDK for Flutter
- **Firebase Auth**: User authentication
- **Cloud Firestore**: NoSQL database for storing tasks
- **Firebase Storage**: File storage for task images
- **Additional Packages**:
  - `cupertino_icons`: iOS-style icons
  - `dotted_border`: Dotted border widgets
  - `intl`: Internationalization and date formatting
  - `flex_color_picker`: Color picker widget
  - `image_picker`: Image selection from gallery/camera
  - `uuid`: Generate unique identifiers

## 📋 Prerequisites

Before running this app, make sure you have:

- [Flutter SDK](https://flutter.dev/docs/get-started/install) installed
- [Android Studio](https://developer.android.com/studio) or [VS Code](https://code.visualstudio.com/) with Flutter extension
- A Firebase project set up ([Firebase Console](https://console.firebase.google.com/))

## 🔧 Installation & Setup

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/firebase-task-manager.git
cd firebase-task-manager
```

### 2. Install dependencies

```bash
flutter pub get
```

### 3. Firebase Setup

#### Android Setup:

1. Create a new Firebase project in [Firebase Console](https://console.firebase.google.com/)
2. Add an Android app to your Firebase project
3. Download `google-services.json` file
4. Place it in `android/app/` directory

#### iOS Setup:

1. Add an iOS app to your Firebase project
2. Download `GoogleService-Info.plist` file
3. Add it to `ios/Runner/` directory

### 4. Enable Firebase Services

In your Firebase Console, enable:

- **Authentication** (Email/Password provider)
- **Cloud Firestore** (in test mode initially)
- **Storage** (in test mode initially)

### 5. Update Firestore Security Rules

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /tasks/{taskId} {
      allow read, write: if request.auth != null && request.auth.uid == resource.data.postedBy;
      allow create: if request.auth != null && request.auth.uid == request.resource.data.postedBy;
    }
  }
}
```

### 6. Update Storage Security Rules

```javascript
rules_version = '2';
service firebase.storage {
  match /b/{bucket}/o {
    match /tasks/{allPaths=**} {
      allow read, write: if request.auth != null;
    }
  }
}
```

## 🚀 Running the App

```bash
flutter run
```

## 📁 Project Structure

```
lib/
├── main.dart                 # App entry point
├── home_page.dart           # Main task list screen
├── login_page.dart          # User login screen
├── signup_page.dart         # User registration screen
├── add_new_task.dart        # Create new task screen
├── utils.dart               # Utility functions
├── firebase_options.dart    # Firebase configuration
└── widgets/
    ├── date_selector.dart   # Date selection widget
    └── task_card.dart       # Task display widget
```

## 📚 Key Components

### Authentication Flow

- Users can sign up with email and password
- Login screen with form validation
- Automatic redirect based on authentication state

### Task Management

- Create tasks with title, description, date, and color
- Optional image attachment
- Real-time task display
- User-specific task filtering

### Firebase Integration

- **Auth**: User management and session handling
- **Firestore**: Task data storage with real-time listeners
- **Storage**: Image upload and retrieval

## 🔐 Security Considerations

⚠️ **Important**: Never commit your Firebase configuration files to public repositories:

Add to `.gitignore`:

```
android/app/google-services.json
ios/Runner/GoogleService-Info.plist
```

## 🎨 Customization

You can customize the app by:

- Modifying the color scheme in `main.dart`
- Adding new task fields in `add_new_task.dart`
- Updating the UI components in the `widgets/` folder
- Changing the app theme and fonts

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-feature`)
3. Commit your changes (`git commit -am 'Add new feature'`)
4. Push to the branch (`git push origin feature/new-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Flutter team for the amazing framework
- Firebase team for the backend services
- Rivaan Ranawat for the tutorial inspiration

## 📞 Support

If you have any questions or run into issues, please:

1. Check the [Flutter documentation](https://flutter.dev/docs)
2. Review [Firebase documentation](https://firebase.google.com/docs)
3. Open an issue in this repository

---

**Happy Coding!** 🎉
