#  Food Delivery Chatbot – Setup Instructions

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
- The backend is not live permanently. A frontend demo is available here: https://chatpaata.netlify.app

---

 Everything is now ready for testing and demonstration.
