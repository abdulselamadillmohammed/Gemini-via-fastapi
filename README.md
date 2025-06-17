# 📚 Project Setup Guide

![Python](https://img.shields.io/badge/Python-3.7%2B-blue?logo=python)
![FastAPI](https://img.shields.io/badge/FastAPI-0.95%2B-green?logo=fastapi)
![License](https://img.shields.io/badge/license-MIT-lightgrey)

This README provides clear step-by-step instructions for setting up and running the backend service.

---

## **Step 1: Clone or Download the Repository**

Clone the repository or download the code as a ZIP file.

```bash
# Example
git clone https://github.com/your-username/your-repository.git
```

---

## **Step 2: Install Python**

Ensure Python 3.7 or higher is installed on your system.

Check your Python version:
```bash
python --version
```
If Python is not installed, download it from [python.org](https://www.python.org/downloads/).

---

## **Step 3: Create a Virtual Environment**

It’s recommended to create a virtual environment to isolate the project's dependencies.

```bash
# Navigate to the project directory
cd path/to/your/project

# Create a virtual environment
python -m venv venv

# Activate the virtual environment
# On Windows
venv\Scripts\activate
# On macOS/Linux
source venv/bin/activate
```

---

## **Step 4: Install Project Dependencies**

Ensure there is a `requirements.txt` file with the following content:

```
fastapi
uvicorn
google-generativeai
pillow
python-multipart
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## **Step 5: Set Up Gemini API Key**

Obtain a Gemini API key from [Google AI Studio](https://makersuite.google.com/).

Update your `main.py` file:

```python
genai.configure(api_key="YOUR_API_KEY")  # Replace YOUR_API_KEY with your real key
```

---

## **Step 6: Run the Backend Server**

Start the FastAPI server:

```bash
uvicorn main:app --reload
```

If successful, you will see:
```
INFO:     Uvicorn running on http://127.0.0.1:8000 (Press CTRL+C to quit)
```

---

## **Step 7: Test the Backend**

Using Postman or any API client:

1. Create a new `POST` request to:
   ```
http://127.0.0.1:8000/analyze-image/
```
2. Under `Body`, select `form-data` and upload a file with the key name `file`.
3. Send the request and review the response.

---

## **Step 8: (Optional) Make Backend Accessible to Other Devices**

Run the server on a public host:

```bash
uvicorn main:app --host 0.0.0.0 --port 8000
```

Access from another device via:
```
http://<your-ip-address>:8000/analyze-image/
```

---

# 🛠️ Quick Summary of Commands

```bash
# Navigate to project
cd path/to/your/project

# Create virtual environment
python -m venv venv

# Activate virtual environment
# Windows:
venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Run server
uvicorn main:app --reload
```

---

# 📂 Folder Structure

```
project/
├── main.py
├── requirements.txt
└── venv/
```

---

# 🚑 Troubleshooting

- **Port Already in Use**
  ```bash
  uvicorn main:app --reload --port 8001
  ```

- **Missing Dependencies**
  ```bash
  pip install -r requirements.txt
  ```

- **CORS Issues**
  Make sure CORS middleware is properly set up in FastAPI if accessing from a frontend.
---

# 📄 License

This project is licensed under the MIT License.
