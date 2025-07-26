# PDF_Compressor Flutter & Flask Project

This repository contains both the **Flutter frontend** (mobile/desktop app) and the **Flask backend** (PDF compression server) for a student-friendly PDF compression tool.

## 📁 Folder Structure

```
PDF_Compressor/
├── frontend/   # Flutter app (Android, iOS, Web, Windows, macOS, Linux)
│   ├── lib/
│   ├── pubspec.yaml
│   ├── README.md
│   └── ... (other Flutter files)
├── backend/    # Flask server (PDF compression logic)
│   ├── app.py
│   ├── requirements.txt
│   ├── README.md
│   └── ... (static, templates, uploads)
└── README.md   # Project overview (this file)
```

## 🚀 Features

- **File Selection:** Pick PDF files from your device.
- **Quality Control:** Choose compression level (`screen`, `ebook`, `printer`, `prepress`).
- **Compress & Download:** Uploads to backend, downloads optimized PDF.
- **Cross-Platform:** Flutter app runs on Android, iOS, Web, Windows, macOS, Linux.

## 🛠️ Tech Stack

- **Frontend:** Flutter (Dart)
- **Backend:** Flask (Python) + Ghostscript

## 📦 Quick Start

### 1. Backend Setup

See [`backend/README.md`](backend/README.md) for full instructions.

- Install Python, Flask, and Ghostscript.
- Run the Flask server (`python app.py`).

### 2. Frontend Setup

```bash
cd frontend
flutter pub get
flutter run
```
- Update the backend URL in [`lib/main.dart`](frontend/lib/main.dart) if needed.

## 📖 How to Use

1. Launch the Flutter app.
2. Select a PDF file.
3. Choose compression quality.
4. Tap "Compress & Download".
5. Save the compressed PDF.

## 📚 More Info

- For backend details, see [`backend/README.md`](backend/README.md).
- For frontend details, see [`frontend/README.md`](frontend/README.md).

## 👨‍💻 Author

Made by 💙