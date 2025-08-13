# 📚 AI Lecture Notes Generator & RAG Study Assistant

## 📌 Overview  
This project was developed during my internship at **Intel** under the **Intel Unnathi Program**. It is an **end-to-end AI-powered learning assistant** that:  
- **Generates detailed lecture notes** from YouTube videos or uploaded lecture files.  
- **Identifies topics** and organizes content into structured **exam-ready study guides**.  
- Integrates a **RAG (Retrieval-Augmented Generation) chatbot** to answer questions directly from generated notes.  

---

## ✨ Key Features  
- 🎥 **Lecture Input**: Accepts YouTube links or uploaded `.mp4`, `.wav`, `.webm` files.  
- 🎙️ **Speech-to-Text**: Uses **OpenAI Whisper** for accurate transcription.  
- 📝 **Smart Chunking**: Splits transcript into context-preserving chunks.  
- 📚 **Topic Identification**: Powered by **Meta LLaMA 4** for semantic topic extraction.  
- 🧠 **AI-Generated Notes**: Generates:  
  - Comprehensive notes  
  - Condensed study guides  
  - Exam-ready summaries  
- 🤖 **RAG Chatbot**: Uses **Gemini 1.5** to answer queries from generated notes.  
- 📥 **Downloadable Notes** in `.md` format with LaTeX rendering for equations.  

---

## 🛠 Tech Stack  
- **Languages**: Python  
- **Backend AI Models**: OpenAI Whisper, Meta LLaMA 4, ChatGPT 4.1, Gemini 1.5  
- **Libraries**:  
  - `pandas`, `numpy`, `openai`, `google-generativeai`  
  - `streamlit` (UI), `pyngrok` (tunneling)  
- **Storage & Processing**: Local/Colab file system  
- **APIs Used**: OpenAI API, Gemini API  

---

## 🚀 How It Works  
1. **Input Stage**  
   - Enter a YouTube video link or upload a lecture file.  
   - Provide your **OpenAI API key**.  

2. **Transcription**  
   - Audio extracted from the video is transcribed using **Whisper**.  

3. **Chunking & Topic Extraction**  
   - Transcript is divided into context-aware chunks.  
   - Topics are identified using **LLaMA 4**.  

4. **Notes Generation**  
   - ChatGPT 4.1 generates multiple note formats.  

5. **Interactive Study Assistant**  
   - Gemini 1.5 chatbot answers questions based on your notes.  

---

