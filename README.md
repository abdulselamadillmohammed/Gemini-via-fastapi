### **Step-by-Step Setup Instructions**

#### **1. Clone or Download the Code**
- clone repo
---

#### **2. Install Python**
Ensure Python 3.7 or higher is installed on your friend’s machine. They can check their Python version by running:
```bash
python --version
```
If Python is not installed, download and install it from [python.org](https://www.python.org/downloads/).

---

#### **3. Create a Virtual Environment**
A virtual environment isolates the project dependencies from the global Python installation.

1. Open a terminal (Command Prompt, PowerShell, or Terminal).
2. Navigate to the directory where the `main.py` file is located:
   ```bash
   cd path/to/your/project
   ```
3. Create a virtual environment:
   ```bash
   python -m venv venv
   ```
   This will create a folder named `venv` in your project directory.

4. Activate the virtual environment:
   - **On Windows**:
     ```bash
     venv\Scripts\activate
     ```
   - **On macOS/Linux**:
     ```bash
     source venv/bin/activate
     ```
   Once activated, you’ll see `(venv)` in the terminal prompt.

---

#### **4. Install Dependencies**
Install the required Python packages using `pip`.

1. Create a `requirements.txt` file in the same directory as `main.py` with the following content:
   ```
   fastapi
   uvicorn
   google-generativeai
   pillow
   python-multipart
   ```
   This file lists all the dependencies needed for the project.

2. Install the dependencies:
   ```bash
   pip install -r requirements.txt
   ```

---

#### **5. Set Up the Gemini API Key**
Your friend will need a Gemini API key to use the backend.

1. Ask them to sign up for a Gemini API key from [Google AI Studio](https://makersuite.google.com/).
2. Once they have the API key, they should replace `YOUR_API_KEY` in the `main.py` file with their actual key:
   ```python
   genai.configure(api_key="YOUR_API_KEY")  # Replace with your actual API key
   ```

---

#### **6. Run the Backend**
Start the FastAPI server using `uvicorn`.

1. Ensure the virtual environment is activated (you should see `(venv)` in the terminal prompt).
2. Run the following command:
   ```bash
   uvicorn main:app --reload
   ```
   - `main` refers to the `main.py` file.
   - `app` refers to the FastAPI instance in the code.
   - The `--reload` flag enables auto-reloading when code changes are made (useful during development).

3. The server will start, and you’ll see output like this:
   ```
   INFO:     Uvicorn running on http://127.0.0.1:8000 (Press CTRL+C to quit)
   ```

---

#### **7. Test the Backend**
Your friend can test the backend using Postman or any other API testing tool.

1. Open Postman.
2. Create a new `POST` request to `http://127.0.0.1:8000/analyze-image/`.
3. In the `Body` tab, select `form-data`, add a key named `file`, and upload an image.
4. Send the request and check the response.

---

#### **8. (Optional) Deploy for Frontend Access**
If your friend needs to access the backend from a frontend application, they can:
1. Run the server on a specific host and port:
   ```bash
   uvicorn main:app --host 0.0.0.0 --port 8000
   ```
   This makes the backend accessible on the local network.

2. Update the frontend code to point to the backend URL (e.g., `http://<your-ip>:8000/analyze-image/`).

---

### **Summary of Commands**
Here’s a quick summary of the commands your friend will need to run:

```bash
# Navigate to the project directory
cd path/to/your/project

# Create a virtual environment
python -m venv venv

# Activate the virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Run the backend
uvicorn main:app --reload
```

---

### **Folder Structure**
After setting up, the project folder should look like this:
```
project/
├── main.py
├── requirements.txt
└── venv/
```

---

### **Troubleshooting**
- **Port Already in Use**: If port `8000` is already in use, specify a different port:
  ```bash
  uvicorn main:app --reload --port 8001
  ```
- **Missing Dependencies**: If any dependencies are missing, reinstall them using:
  ```bash
  pip install -r requirements.txt
  ```
- **CORS Issues**: If the frontend cannot access the backend, ensure CORS is properly configured in the backend code.
