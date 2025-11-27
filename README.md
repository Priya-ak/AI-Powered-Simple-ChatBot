# 🤖 ChatBot – Streamlit + LangChain + Ollama

ChatBot is a simple and powerful AI chatbot built using **Streamlit**, **LangChain**, and **Ollama**.  
It uses the **Llama2 model running locally** to answer user queries in real time.

---

## 🚀 Features

- 🧠 Runs **Llama2** locally using Ollama  
- 💬 Chat-style conversation using LangChain  
- ⚡ Real-time response generation  
- 🎨 Clean and simple UI using Streamlit  
- 🔧 Easy to run and customize  

---

## 📂 Project Structure

```bash
📁 priya-chatbot
│
├── main.py
├── requirements.txt
└── README.md
```
## 🛠️ Installation & Setup
1️⃣ Install dependencies
```
pip install -r requirements.txt
```
Or manually:
```

pip install streamlit langchain langchain-community
```
2️⃣ Install Ollama (required)

Download Ollama from:

👉 https://ollama.com/download

Then pull the Llama2 model:
```
ollama pull llama2
```
3️⃣ Run the Chatbot
```
streamlit run main.py
```
Your chatbot will open in the browser at:
```
http://localhost:8501
```
🧩 Code (main.py)
```
from langchain_core.prompts import ChatPromptTemplate
from langchain_core.output_parsers import StrOutputParser
from langchain_community.llms import Ollama
import streamlit as st

st.title("Priya ChatBot 🤖")

input_txt = st.text_input("Please enter your queries here...")

prompt = ChatPromptTemplate.from_messages(
    [
        ("system", "You are a helpful AI assistant. Your name is Kaila."),
        ("user", "User query: {query}")
    ]
)

llm = Ollama(model="llama2")
output_parser = StrOutputParser()

chain = prompt | llm | output_parser

if input_txt:
    response = chain.invoke({"query": input_txt})
    st.write(response)
```
📦 Requirements.
```
streamlit
langchain
langchain-community
```
🧠 How It Works

1.User enters a question

2.LangChain builds a structured prompt

3.Llama2 (via Ollama) generates a response

4.Streamlit displays the result

📸 Screenshot



🤝 Contributing

Contributions and suggestions are welcome.

📜 License

This project is licensed under the MIT License.
