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








