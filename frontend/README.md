# PDF Compressor - Flutter Frontend

<p align="center">
  <img src="https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white" alt="Flutter Badge"/>
  <img src="https://img.shields.io/badge/Dart-0175C2?style=for-the-badge&logo=dart&logoColor=white" alt="Dart Badge"/>
</p>

This directory contains the Flutter frontend for the PDF Compressor project. It is a cross-platform application designed to provide a simple and intuitive user interface for interacting with the Flask compression backend.

The app allows users to select a PDF, choose a compression quality, and save the optimized file back to their device.

![App Demo](../.github/assets/Output.png)

---

## ✨ Features

-   **Native File Picker:** Uses the device's native file explorer to select PDF files.
-   **Quality Selection:** A clean dropdown menu to choose the desired compression level.
-   **API Integration:** Communicates with the backend via HTTP requests to upload and download files.
-   **Progress Indication:** Provides status updates to the user during the upload and compression process.
-   **Save File Dialog:** Leverages `file_saver` to let the user choose the save location and filename for the compressed PDF.
-   **Cross-Platform:** Built with Flutter to run on Android, iOS, Windows, macOS, and Linux from a single codebase.

---

## 🛠️ Built With

This app is built using the following key packages:

-   **Flutter**: The UI toolkit for building the application.
-   **http**: For making HTTP requests to the Flask backend.
-   **file_picker**: For selecting files from the device storage.
-   **file_saver**: For saving the compressed file back to the device.

---

## 🚀 Getting Started

Follow these instructions to get the Flutter app up and running on your local machine.

### Prerequisites

-   **Flutter SDK:** Ensure you have Flutter installed. You can follow the official guide.
-   **A Code Editor:** VS Code with the Flutter extension or Android Studio.
-   **Running Backend:** The Flask backend server must be running and accessible from the device/emulator where you run the app.

### Installation & Setup

1.  **Navigate to the frontend directory:**
    ```bash
    # If you are at the root of the project
    cd frontend
    ```

2.  **Install dependencies:**
    This command fetches all the required packages listed in `pubspec.yaml`.
    ```bash
    flutter pub get
    ```

### Configuration

The most important step is to configure the app to communicate with your backend server.

1.  **Open the main file:**
    `frontend/lib/main.dart`

2.  **Update the API URL:**
    Find the `Uri.parse(...)` line inside the `compressAndDownload` function and replace the URL with the IP address and port of your running Flask server.

    ```dart
    // lib/main.dart

    // ... inside compressAndDownload()
    var request = http.MultipartRequest(
      'POST',
      // ‼️ UPDATE THIS URL ‼️
      Uri.parse("http://<YOUR_BACKEND_IP_ADDRESS>:<PORT>/compress"),
    );
    // ...
    ```

    -   If running the backend on the same machine as an Android emulator, use `10.0.2.2` for the IP address (e.g., `http://10.0.2.2:10000/compress`).
    -   If running on a physical device, use your computer's local network IP address (e.g., `http://192.168.1.10:10000/compress`).

### Running the App

1.  Ensure your Flask backend server is running.
2.  Connect a device or start an emulator.
3.  Run the app from your terminal:
    ```bash
    flutter run
    ```

---

## 🤝 Contributing

Contributions to the frontend are welcome! Please refer to the main `README.md` at the root of the project for general contribution guidelines.

## 📜 License

This project is licensed under the MIT License. See the `LICENSE` file in the root directory for more details.
