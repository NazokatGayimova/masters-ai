
Hugging Face deployment link: https://huggingface.co/spaces/Nazokatgmva/AI_Support_Volkswagen

---
title: "Volkswagen AI Support Chat"
emoji: "🚗"
colorFrom: "blue"
colorTo: "green"
sdk: "streamlit"
app_file: "app.py"
pinned: false
---

# 🚗 Volkswagen AI Support Chat

An AI-powered customer support chat for Volkswagen documents, built with **Streamlit**. This application extracts and searches PDF files to answer customer questions, raise support tickets, and provide accurate document citations.

---

## 🎯 **Project Objective**

To build a customer support solution that can:

1. **Answer Questions from Documents**  
   - Uses Volkswagen documents as data sources to provide accurate answers.  
   - Cites the correct file name and page number for each response.  
   - Supports at least 3 documents (2 PDFs and 1 file with 400+ pages).  

2. **Create Support Tickets**  
   - If no relevant answer is found, the agent suggests creating a support ticket.  
   - Collects user name, email, title, and description for the ticket.  
   - Creates a GitHub issue to track the ticket.  

3. **Keep Conversation History**  
   - Stores the entire conversation context for a more human-like chat experience.  

4. **Provide Company Information**  
   - Always displays the company's name, email, and phone number in the chat.  

---

## 💻 **Technical Requirements**

- **Language:** Python  
- **Dependencies:** See `requirements.txt`  
- **Vector Storage:** Sentence Transformers with FAISS-like retrieval  
- **Web Interface:** Streamlit  
- **Deployment:** Hosted on Hugging Face Spaces  

---

## 📁 **Project Structure**
📁 Volkswagen_AI_Support_Chat/
├── Y_2024_e.pdf
├── 2023_Volkswagen_Group_Sustainability_Report.pdf
├── 20240930_Group_CoC_Brochure_EN_RGB_V3_1.pdf
├── app.py                   # Main Streamlit application
├── document_retrieval.py    # Document processing and search
├── github_integration.py    # GitHub issue creation
├── context.py               # Company info and conversation history
├── requirements.txt         # Python dependencies
└── README.md                # Project overview

---

## 🚀 **Features Implemented**

- **Natural Language Question Answering:**  
  - Extracts accurate answers from Volkswagen documents.  
  - Cites the correct PDF file and page number.  

- **Support Ticket Creation:**  
  - Allows users to create support tickets if no relevant answer is found.  
  - Integrates with GitHub to track tickets.  

- **Conversation History:**  
  - Maintains a running history of the conversation for context.  

- **Smart Text Chunking:**  
  - Splits documents into meaningful chunks for better matching.  
  - Avoids repeating the same responses to similar questions.  

---

## 📦 **Dependencies**

Make sure to include the following in your `requirements.txt`:
PyMuPDF
sentence-transformers
streamlit
torch
requests

---

## 👨‍💻 **How to Use**

1. **Upload Your Documents:**  
   - Place your PDF files in the main directory of this repository.  

2. **Run the App:**  
   - Deploy to Hugging Face Spaces or run locally with:  
   ```bash
   streamlit run app.py

   	3.	Ask Questions:
	•	Type your question into the chat and receive responses with accurate citations.
	4.	Create Support Tickets:
	•	If no relevant answer is found, create a support ticket directly from the chat.

⸻

👩‍💻 Author

Built by Nazokat Gayimova.
