# Case Study: AI Support Agent (RAG) for a Discord Gaming Community

This project is a case study of an autonomous AI agent, built using n8n, designed to act as a 24/7 support moderator in an online game's Discord server.

---

## 🎯 The Business Problem

Online gaming Discord servers receive a constant flow of repetitive questions (FAQs) from players about game mechanics, rules, NFTs, and more. Human moderation is limited by time and cost, resulting in slow responses and frustrated users.

The challenge was to create a solution that provides:
- Instant and accurate responses, 24/7  
- Consistent information based *only* on the official game documentation  
- A natural conversational experience for players  

---

## 🛠️ Solution Architecture

I developed an AI agent in n8n using a **RAG (Retrieval-Augmented Generation)** architecture to ensure responses are fully grounded in factual data.

The logical flow works as follows:

1. **Webhook + Classification (Gemini):** Incoming Discord messages are received. An initial AI model classifies the user’s intent (e.g., “SMALL TALK” or “GAME-RELATED QUESTION”).  
2. **Vector Search (RAG):** If it is a question, the system queries a **vector database (Pinecone)** to retrieve the most relevant sections of the official game documentation.  
3. **Memory (PostgreSQL):** The agent accesses a SQL database to retain conversation history, enabling contextual understanding.  
4. **Response Generation (OpenAI Agent):** The main agent receives the original question, conversation history, and retrieved documents, then generates a coherent and accurate response.  
5. **Action (Discord API):** The final response is sent back to the Discord channel.  

---

## 🖼️ Workflow Visualization

Below is a screenshot of the workflow architecture built in n8n. (Sensitive information such as database names and API keys has been omitted for confidentiality.)

<img width="1560" height="528" alt="image" src="https://github.com/user-attachments/assets/daa03897-be75-4196-b934-d1b5bbf95afa" />

---

## 🔑 Technical Highlights

- **Platform:** n8n  
- **AI & LLMs:** OpenAI (Main Agent), Google Gemini (Classification)  
- **Architecture:** RAG (Retrieval-Augmented Generation)  
- **Vector Database:** Pinecone  
- **Conversation Memory:** PostgreSQL  
- **Integration:** Discord API  

---

## 📈 Business Impact

- **24/7 Support:** The community now receives instant responses at any time of day  
- **Workload Reduction:** Reduced repetitive questions directed to human moderators by over 70%  
- **Information Consistency:** Ensures all players receive the same official information, eliminating misinformation  
