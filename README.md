# BioM-NER: Biomedical NER & Drug Recommender 🧬💊

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://biomner.streamlit.app/)

An advanced web application designed to bridge the gap between biomedical literature and actionable insights. It leverages a powerful deep learning model (**BioBERT**) to perform Named Entity Recognition (NER) on clinical texts, identifying key entities like diseases and chemicals. For each detected disease, it intelligently queries **Google's Gemini API** to provide relevant drug recommendations.

### ➡️ **[View the Live Demo](https://biomner.streamlit.app/)**

---

## ✨ Key Features

* 🧠 **Advanced Biomedical NER**: Utilizes a fine-tuned BioBERT model to accurately identify diseases, disorders, chemicals, and other biomedical entities from unstructured text.
* 📄 **Multi-Format File Support**: Seamlessly upload and process text from `.txt`, `.pdf`, and `.docx` files, making it easy to analyze research papers, patient notes, or articles.
* 🤖 **AI-Powered Drug Recommendations**: Integrates with the Google Gemini API to provide concise, relevant drug suggestions for any diseases identified in the text.
* 📊 **Clear & Interactive UI**: A clean and user-friendly interface built with Streamlit that presents the detected entities in a structured table and the drug recommendations in a clear list.

---

## 🔧 How It Works

The application follows a simple yet powerful workflow to deliver insights:

1.  **Text Input**: The user provides text either by direct input or by uploading a document.
2.  **Text Extraction**: The system extracts raw text from the uploaded file, regardless of its format (`pdf`, `docx`, `txt`).
3.  **NER with BioBERT**: The text is processed by a **BioBERT model** (fine-tuned on the BC5CDR and JNLPBA datasets) to extract and classify biomedical entities.
4.  **Disease Filtering**: The app specifically identifies and collects all unique "disease" and "disorder" entities from the NER results.
5.  **Gemini API Query**: For each unique disease, a targeted prompt is sent to the **Gemini 2.0 Flash model** to request a list of 1-3 relevant drugs.
6.  **Display Results**: The app neatly presents a table of all recognized entities and a list of drug recommendations for each detected disease.

---

## 🛠️ Tech Stack

* **Backend & Frontend**: [Streamlit](https://streamlit.io/)
* **NLP / NER**: [Hugging Face Transformers](https://huggingface.co/transformers) with a fine-tuned [BioBERT](https://github.com/dmis-lab/biobert) model.
* **Generative AI**: [Google Gemini API](https://ai.google.dev/)
* **File Processing**: `PyPDF2`, `python-docx`
* **Environment Management**: `python-dotenv`

---

## ⚙️ Setup and Local Installation

To run this project on your local machine, follow these steps.

### Prerequisites

* Python 3.8+
* `pip` package manager

### Installation

1.  **Clone the Repository**
    ```bash
    git clone [https://github.com/YOUR_USERNAME/YOUR_REPOSITORY_NAME.git](https://github.com/YOUR_USERNAME/YOUR_REPOSITORY_NAME.git)
    cd YOUR_REPOSITORY_NAME
    ```

2.  **Create and Activate a Virtual Environment**
    ```bash
    # Create the environment
    python -m venv venv

    # Activate it (macOS/Linux)
    source venv/bin/activate

    # Activate it (Windows)
    .\venv\Scripts\activate
    ```

3.  **Install Dependencies**
    Create a `requirements.txt` file with the necessary packages and install them.
    ```bash
    pip install -r requirements.txt
    ```

4.  **Download the NER Model**
    This project uses a local BioBERT model. You need to download the `biobert_ner_bc5cdr_jnlpba` model files and place them in your project directory. Update the model path in `app.py` if you place them in a sub-folder.
    *(You should add a note here on where other users can download this model from, e.g., a link to a Hugging Face model page or a Google Drive link.)*

5.  **Set Up Environment Variables**
    Create a file named `.env` in the root of your project directory and add your Google API key:
    ```
    GOOGLE_API_KEY="your_actual_google_api_key_here"
    ```

6.  **Run the Streamlit App**
    ```bash
    streamlit run app.py
    ```

---

## 📝 Usage

1.  Launch the application.
2.  Either paste text directly into the text area or use the file uploader to select a `.txt`, `.pdf`, or `.docx` document.
3.  Click the "Analyze" button.
4.  View the results in the "Named Entities Detected" table and the "Recommended Drugs" list.

