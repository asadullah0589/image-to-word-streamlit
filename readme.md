# Image to Word Converter

Convert images of documents into **fully editable Microsoft Word (.docx) files** using **Groq Vision models**. The app extracts text, layout, and basic formatting such as headings, lists, tables, and alignment.

---

## 🚀 Features

- 🖼️ Upload one or multiple document images
- 📝 Extract text with formatting (bold, italic, underline)
- 🧱 Detect headings (H1, H2, H3)
- 📋 Recognize bullet and numbered lists
- 📊 Basic table detection
- 📐 Preserve text alignment (left, center, right, justify)
- 📄 Export to editable **.docx** format

---

## 🧠 How It Works

1. You upload document images (PNG / JPG / JPEG)
2. Images are sent to **Groq’s hosted Vision LLM** (remote inference)
3. The model extracts text + structure and returns structured JSON
4. The app converts that JSON into a formatted Word document
5. You download the final `.docx` file

> ⚠️ **Note:** The AI model is **not run locally**. All inference happens on Groq’s servers via API.

---

## 📦 Requirements

- Python **3.8+**
- Internet connection
- A valid **Groq API key**

Python dependencies (already pinned in `requirements.txt`):

```
streamlit==1.31.0
requests==2.31.0
Pillow==10.2.0
python-docx==1.1.0
```

---

## 🔑 Groq API Key Setup (IMPORTANT)

### Recommended (for GitHub & Streamlit Cloud)

Do **NOT** hard-code your API key in `app.py`.

Instead, set it as an environment variable.

#### Local (Windows PowerShell)
```bash
setx GROQ_API_KEY "your_groq_api_key_here"
```

#### Local (macOS / Linux)
```bash
export GROQ_API_KEY="your_groq_api_key_here"
```

Then in `app.py`, the key is read automatically:
```python
GROQ_API_KEY = os.getenv("GROQ_API_KEY")
```

#### Streamlit Community Cloud

1. Go to **App → Settings → Secrets**
2. Add:
```toml
GROQ_API_KEY = "your_groq_api_key_here"
```

---

## ▶️ Running the App Locally

```bash
pip install -r requirements.txt
streamlit run app.py
```

Open the browser link shown in the terminal.

---

## ☁️ Deploying on Streamlit Community Cloud

1. Push this project to a **public GitHub repository**
2. Go to https://share.streamlit.io
3. Click **New App**
4. Select:
   - Repository: your GitHub repo
   - Branch: `main`
   - Main file: `app.py`
5. Add `GROQ_API_KEY` in **Secrets**
6. Deploy 🚀

---

## 🧪 Supported Models

This app uses Groq’s **hosted vision-capable LLM**:

```
meta-llama/llama-4-scout-17b-16e-instruct
```

Model selection happens in the API request. No models are downloaded or loaded locally.

---

## 🛠 Troubleshooting

### ❌ Model Decommissioned Error
- Groq occasionally retires preview models
- Update the `VISION_MODEL` constant to a supported model

### ❌ API Errors (401 / 403)
- Check that your API key is valid
- Ensure the key is set in environment variables or Streamlit Secrets

### ❌ No Text Extracted
- Use clearer, higher-resolution images
- Avoid skewed or blurry scans

---

## 📌 Example Use Cases

- Digitizing scanned documents
- Converting screenshots to editable text
- Processing notes or printed forms
- Creating Word files from multi-page scans

---

## 📄 License

Free to use for learning and experimentation.

---

**Powered by Groq Vision API and python-docx**

