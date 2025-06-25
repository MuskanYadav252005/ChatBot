# ChatBot
# Food Order Chatbot Backend (FastAPI + Dialogflow)

This repository contains the backend for a food ordering chatbot developed using FastAPI. It interacts with Dialogflow via webhook to manage food orders. The backend handles operations such as adding items to the order, removing items, completing the order, and tracking the order status.

---

## Features

- Add food items to an in-progress order
- Remove specific items from an ongoing order
- Finalize an order and persist it in a database
- Track the status of a completed order using Order ID

---

## Technology Stack

- FastAPI for building RESTful APIs
- Dialogflow ES for conversational interface
- SQLite (or any database) for order storage
- Ngrok for exposing the local server to the internet

---

## Project Structure

```bash
.
├── main.py               # FastAPI server and intent handler
├── db_helper.py          # Database interaction logic
├── generic_helper.py     # Utility functions (e.g., session ID extraction)
├── requirements.txt      # List of dependencies
├── extra/                # Additional helper files (if any)
└── __pycache__/          # Compiled Python files (auto-generated)
```

---

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/MuskanYadav252005/ChatBot.git
cd ChatBot/backend
```

### 2. Set Up a Virtual Environment

```bash
python -m venv venv
venv\Scripts\activate     # For Windows
# or
source venv/bin/activate  # For Mac/Linux
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Start the FastAPI Server

```bash
uvicorn main:app --reload --port 8050
```

### 5. Expose Server with Ngrok

```bash
ngrok http 8050
```

Copy the HTTPS URL from Ngrok and configure it as your webhook URL in the Dialogflow console.

---

## Dialogflow Setup

1. Create a Dialogflow agent.
2. Define the following intents:
   - `order.add - context: ongoing-order`
   - `order.remove - context: ongoing-order`
   - `order.complete - context: ongoing-order`
   - `track.order - context: ongoing-order`
3. Enable webhook fulfillment for each intent.
4. Set the webhook URL under **Fulfillment > Webhook** using the Ngrok HTTPS URL.
5. Use session-based contexts to manage the state of each user’s order.

---

## Example Fulfillment Response

```json
{
  "fulfillmentText": "Your order has been placed. Order ID is #124. You can pay the total amount upon delivery."
}
```

---

## Notes

- All ongoing orders are stored in memory during the session using a dictionary.
- Completed orders are saved in a persistent database using helper functions in `db_helper.py`.
- The code can be extended to support a more robust database like PostgreSQL or MongoDB.

---

## Contributing

Contributions are welcome. Please open an issue or submit a pull request for any improvements or bug fixes.

---

## License

This project is licensed under the MIT License.

---

## Author

**Muskan Yadav**  
[GitHub Repository](https://github.com/MuskanYadav252005/ChatBot)


