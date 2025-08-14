# AI Lecture Notes Generator & RAG Study Assistant  

![Python](https://img.shields.io/badge/Python-3.9-blue)  
![License: MIT](https://img.shields.io/badge/License-MIT-green)  

---

## Overview  
This project was developed during my internship at **Intel** under the **Intel Unnathi Program**. It is an **end-to-end AI-powered learning assistant** that:  
- **Generates detailed lecture notes** from YouTube videos or uploaded lecture files.  
- **Identifies topics** and organizes content into structured **exam-ready study guides**.  
- Integrates a **RAG (Retrieval-Augmented Generation) chatbot** to answer questions directly from generated notes.  

---

## Key Features  
- **Lecture Input**: Accepts YouTube links or uploaded `.mp4`, `.wav`, `.webm` files.  
- **Speech-to-Text**: Uses **OpenAI Whisper** for accurate transcription.  
- **Smart Chunking**: Splits transcript into context-preserving chunks.  
- **Topic Identification**: Powered by **Meta LLaMA 4** for semantic topic extraction.  
- **AI-Generated Notes**: Generates:  
  - Comprehensive notes  
  - Condensed study guides  
  - Exam-ready summaries  
- **RAG Chatbot**: Uses **Gemini 1.5** to answer queries from generated notes.  
- **Downloadable Notes** in `.md` format with LaTeX rendering for equations.  

---

## 🛠 Tech Stack  
**Languages:** Python  
**Backend AI Models:** OpenAI Whisper, Meta LLaMA 4, ChatGPT 4.1, Gemini 1.5  
**Libraries:**  
`pandas`, `numpy`, `openai`, `google-generativeai`, `nltk`, `yt-dlp`,`openvino optimum[openvino]`, `transformers`
**Storage & Processing:** Local/Colab file system  
**APIs Used:** OpenAI API, Gemini API  

---

## ⚙️ How It Works  

### 1️⃣ Input Stage  
Upload a lecture file or paste a YouTube link → Provide API keys.  

### 2️⃣ Transcription  
Audio → Text using Whisper AI.  

### 3️⃣ Chunking & Topic Extraction  
Text is split into meaningful chunks and tagged with topics using LLaMA 4.  

### 4️⃣ AI Notes Generation  
ChatGPT 4.1 generates multiple versions of notes for different learning needs.  

### 5️⃣ RAG Chatbot Query  
Gemini 1.5 chatbot answers user questions using only the generated notes.  

**Flow Diagram:**  
![Workflow](<img width="467" height="1149" alt="workflow" src="https://github.com/user-attachments/assets/0380f603-1a7a-4792-b13d-96722db53a32" />)  
*(You can design a flow diagram in draw.io, export as PNG, and save it in `docs/` folder)*  

---

## Example of Generated Notes  

**Exam-Ready Notes**  
![Notes Example](<img width="950" height="954" alt="image" src="https://github.com/user-attachments/assets/0c0f8b12-b459-495f-8611-59ff05253d6d" />)  

**Comprehensive Notes**  
![Study Guide](<img width="936" height="970" alt="image" src="https://github.com/user-attachments/assets/7ff5fca7-8210-4cc9-8e0f-e54b497cfbb2" />)  

**Detailed Prep Notes**
![Induvisual Notes](<img width="1213" height="941" alt="image" src="https://github.com/user-attachments/assets/756833b2-e378-4cdf-96fc-7a2451e8825d" />)


---
