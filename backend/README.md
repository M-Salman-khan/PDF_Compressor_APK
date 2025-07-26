# PDF Compressor - Flask API Backend

<p align="center">
  <img src="https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white" alt="Flask Badge"/>
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python Badge"/>
  <img src="https://img.shields.io/badge/Ghostscript-v10.x-red.svg?style=for-the-badge" alt="Ghostscript Badge"/>
</p>

This directory contains the Flask backend server for the PDF Compressor project. It's a lightweight, pure API server designed to receive a PDF file from the Flutter frontend, compress it using Ghostscript, and return the optimized file.

## ✨ Core Functionality

-   **Single API Endpoint:** Exposes a `/compress` endpoint to handle all compression logic.
-   **Ghostscript Engine:** Leverages the powerful Ghostscript command-line tool for efficient PDF compression.
-   **Stateless Design:** The server processes requests on the fly and does not store user data long-term (uploaded files are temporary).

---

## ⚙️ API Documentation

### Compress PDF

-   **Endpoint:** `POST /compress`
-   **Description:** Uploads a PDF file, compresses it to the specified quality, and returns the result.
-   **Request Type:** `multipart/form-data`

#### Form Data Parameters

| Key       | Type   | Description                                                                                             |
| :-------- | :----- | :------------------------------------------------------------------------------------------------------ |
| `pdf`     | File   | **Required.** The PDF file to be compressed.                                                            |
| `quality` | String | *Optional.* The compression level. Defaults to `ebook`.<br>Options: `screen`, `ebook`, `printer`, `prepress`. |

#### Responses

-   **`200 OK`**:
    -   **Content:** The compressed PDF file as a binary stream.
    -   **Headers:**
        -   `Content-Type: application/pdf`
        -   `Content-Disposition: attachment; filename="compressed_{quality}_{original_filename}"`

-   **`400 Bad Request`**:
    -   **Content:** `{"error": "No file part"}` or `{"error": "No selected file"}`
    -   **Reason:** The `pdf` file part is missing from the request.

-   **`500 Internal Server Error`**:
    -   **Content:** `{"error": "<error_message>"}`
    -   **Reason:** An error occurred during the Ghostscript compression process.

---

## 🚀 Getting Started

### Prerequisites

1.  **Python 3.7+**
2.  **Pip** (Python package installer)
3.  **Ghostscript:** Must be installed on the server's operating system.
    -   Download Ghostscript

### Installation & Setup

1.  **Navigate to the backend directory:**
    ```bash
    cd backend
    ```

2.  **Install Python dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Configure Ghostscript Path:**
    This is a critical step. Open `main.py` and find the `get_ghostscript_cmd()` function. Update the path to match your Ghostscript installation, especially for Windows.

    ```python
    # d:\Downloads\Desktop\New folder\Flutter\backend\main.py

    def get_ghostscript_cmd():
        if platform.system() == "Windows":
            # ‼️ UPDATE THIS PATH if your installation is different
            return "C:\\Program Files\\gs\\gs10.05.1\\bin\\gswin64c.exe"
        else:
            # On Linux/macOS, 'gs' should be in the system PATH
            return "gs"
    ```

4.  **Run the Server:**
    ```bash
    python main.py
    ```
    The API server will start on `http://0.0.0.0:10000`.

---

## 🧪 Testing the API

You can test the endpoint using a tool like `curl` without needing the Flutter app.

```bash
# Replace 'path/to/your/file.pdf' with an actual file path
curl -X POST \
  -F "pdf=@path/to/your/file.pdf" \
  -F "quality=screen" \
  http://127.0.0.1:10000/compress \
  -o compressed_output.pdf
```

----
This command will send `file.pdf`, compress it with `screen` quality, and save the result as `compressed_output.pdf`.

