### Name : Kevin Yoga Pratama

### Tech Stack : Python, Gradio, LangChain, HuggingFace Embedding, FAISS vector store

---

### 1. Analysis about how the project works

The project is a simple application that allows users to upload a PDF file and ask questions about it using the Retrieval-Augmented Generation (RAG) technique. The application uses the Groq API Key to access powerful LLMs allowing for contextual question answering based on the uploaded document.
In this project, I uploaded a file titled "KEVIN YOGA PRATAMA_CV & LinkedIn Review Booklet", which contains detailed feedback and recommendations to improve a CV and LinkedIn profile. 

---

### 2. Analysis about how different every model works on Retrieval-Augmented Generation

```python
def get_llm():
    return ChatGroq(
        groq_api_key=GROQ_API_KEY,
        model_name="llama-3.3-70b-versatile",
        temperature=0.2
    )
```

- Model used : `[llama-3.3-70b-versatile, deepseek-r1-distill-llama-70b, gemma2-9b-it]`

2.1 Analysis on `llama-3.3-70b-versatile` :

- Question: apa saja hal penting yang harus diperbaiki dari CV dan LinkedIn saya?
- Answer: Berdasarkan dokumen yang tersedia, beberapa hal penting yang perlu diperbaiki antara lain penambahan nomor WhatsApp terintegrasi, penguatan bagian summary dengan menyebutkan minat karier, serta penambahan data terukur pada pengalaman kerja. Model ini merespons dengan akurat dan menjelaskan poin utama tanpa tambahan informasi di luar konteks dokumen.
- Analysis: The model acted conservatively and correctly declined to answer without context, highlighting its suitability for accurate RAG-based systems.

2.2 Analysis on `deepseek-r1-distill-llama-70b` :

- Question: apa saja hal penting yang harus diperbaiki dari CV dan LinkedIn saya?
- Answer: Beberapa perbaikan penting meliputi meningkatkan deskripsi pengalaman kerja dengan menambahkan angka, menyusun ulang bagian skill menjadi lebih terstruktur, serta memperbaiki desain CV agar lebih bersih dan sesuai standar ATS. Model ini memberikan jawaban yang lebih luas dan kreatif, meskipun beberapa poin merupakan generalisasi berdasarkan pemahaman umum terhadap topik CV dan LinkedIn.
- Analysis: The model provided a well-written, plausible general answer but ignored context limitations. It's helpful for generalization, but not strictly faithful to the source.

2.3 Analysis on `gemma2-9b-it` :

- Question: apa saja hal penting yang harus diperbaiki dari CV dan LinkedIn saya?
- Answer: Model ini menyoroti pentingnya menambahkan bagian featured di LinkedIn untuk menampilkan karya, serta mengingatkan perlunya memperbarui bagian aktivitas dengan konten profesional. Jawabannya padat, langsung ke inti, dan berdasarkan potongan teks yang ditemukan tanpa terlalu banyak tambahan.
- Analysis: The model correctly identified context limitations and responded accurately. Its behavior shows it's efficient and appropriate for context-dependent use even with smaller size.

---

### 3. Analysis about how temperature works

```python
def get_llm():
    return ChatGroq(
        groq_api_key=GROQ_API_KEY,
        model_name="llama-3.3-70b-versatile",
        temperature=0.9
    )
```

3.1 Analysis on higher temperature (0.9)

- High temperature allows for more creative and varied answers. It may include guesses and self-reflections, but risks being less consistent and factual.

3.2 Analysis on lower temperature (0.1)

- Low temperature results in concise, fact-based responses. The model avoids speculation and prioritizes context-faithful answers. This is ideal for RAG scenarios.

---

### 4. How to run the project

- Clone this repository:

```bash
git clone https://github.com/arifian853/RAG_with_GroqAPI.git
```

- Rename `.env.example` to `.env` and insert your Groq API Key:

```env
GROQ_API_KEY=your-groq-api-key
```

- Create virtual environment:

```bash
python -m venv venv
```

- Activate virtual environment:

```bash
venv\Scripts\activate        # Windows
source venv/bin/activate      # macOS/Linux
```

- Install dependencies:

```bash
pip install -r requirements.txt
```

- Run the app:

```bash
python app.py
```

- Open browser at: [http://127.0.0.1:7860](http://127.0.0.1:7860)

---


