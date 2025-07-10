# Food Ordering ChatBot with FastAPI and Dialogflow

This project implements a food ordering chatbot backend using FastAPI, connected to Dialogflow for natural language understanding. It allows users to place, remove, complete, and track food orders through conversational interaction.

---

## Features

- **Dialogflow Integration**  
  Understands natural language inputs with support for multiple intents.

- **FastAPI Backend**  
  Handles HTTP POST requests from Dialogflow with structured intent handlers.

- **MySQL Support**  
  Can connect to a MySQL database (see `db_helper.py`), or simulate DB operations in memory.

- **Intent Handlers**
  - `add_to_order`: Adds food items to a session.
  - `remove_from_order`: Removes items from an order.
  - `complete_order`: Confirms and stores an order.
  - `track_order`: Provides status of a placed order.



##  Directory Structure

backend/            - FastAPI backend code  
db/                 - MySQL database dump (import using MySQL Workbench)  
dialogflow_assets/  - Dialogflow agent with training phrases and intents  
frontend/           - Website code (hosted on Netlify)

---

##  Module Installation

### Option 1: Install individually
pip install mysql-connector  
pip install "fastapi[all]"

### Option 2: Install all at once using requirements.txt
pip install -r backend/requirements.txt

---


## 🗂️ Dialogflow Agent

The `dialogflow_assets/` folder contains:

- `training_phrases.txt`: Sample training queries for different user intents
- `dialogflow_agent.zip`: A full export of the Dialogflow agent

### 🔁 How to Import Agent into Dialogflow

1. Go to [Dialogflow Console](https://dialogflow.cloud.google.com/)
2. Click on ⚙ **Settings** of your agent
3. Go to the **Export and Import** tab
4. Click **"Restore from ZIP"**
5. Upload `dialogflow_agent.zip` from this repo

This will restore all your intents, entities, and training data.


##  Run FastAPI Backend Server

1. Open terminal and navigate to the `backend` directory:
cd backend

2. Start the server:
uvicorn main:app --reload

---

##  Ngrok for HTTPS Tunneling (Required for Dialogflow)

1. Download ngrok from: https://ngrok.com/download  
2. Extract the ZIP file and place `ngrok.exe` in a folder  
3. Open Command Prompt, go to that folder, and run:
ngrok http 8000

4. Copy the HTTPS forwarding URL (e.g., https://xxxx.ngrok-free.app)  
   Paste it into your Dialogflow Fulfillment webhook URL  
   (append `/webhook` if that’s your endpoint)

---

## ⚠️ Important Notes

- Ngrok creates a temporary tunnel. If your terminal closes or you see a “session expired” message, you’ll need to restart ngrok.
- After restarting ngrok, update the webhook URL in Dialogflow Fulfillment with the new HTTPS URL.
- The backend is not live permanently. A frontend demo is available here:https://chatpaata.netlify.app/

---

 Everything is now ready for testing and demonstration.






