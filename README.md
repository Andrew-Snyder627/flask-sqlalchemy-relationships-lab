# Flask-SQLAlchemy Relationships Lab

## Overview

This Flask app models an event management system with multiple relationships between models using SQLAlchemy. It demonstrates:

- One-to-Many: Event ➡ Sessions
- One-to-One: Speaker ➡ Bio
- Many-to-Many: Session ↔ Speaker

You’ll find a fully working backend with proper migrations, seeded data, relationship querying, and tested RESTful endpoints.

---

## Entity Relationships

### 📊 Modeled ERD Relationships

- An `Event` **has many** `Sessions`
- A `Session` **belongs to one** `Event`
- A `Speaker` **has one** `Bio`
- A `Bio` **belongs to one** `Speaker`
- A `Session` **has many** `Speakers` through `session_speakers`
- A `Speaker` **has many** `Sessions` through `session_speakers`

---

## API Endpoints

### Events

- `GET /events`  
  Returns all events as JSON:

  ```json
  [
    {
      "id": 1,
      "name": "Tech Future Conference",
      "location": "New York"
    }
  ]
  ```

- `GET /events/<id>/sessions`  
  Returns all sessions for an event:
  ```json
  [
    {
      "id": 1,
      "title": "Intro to AI",
      "start_time": "2023-09-15T10:00:00"
    }
  ]
  ```

---

### Speakers

- `GET /speakers`  
  Returns all speakers:

  ```json
  [
    {
      "id": 1,
      "name": "Alex Johnson"
    }
  ]
  ```

- `GET /speakers/<id>`  
  Returns a speaker and their bio (or fallback):
  ```json
  {
    "id": 1,
    "name": "Alex Johnson",
    "bio_text": "Expert in scalable backend systems..."
  }
  ```

---

### Sessions

- `GET /sessions/<id>/speakers`  
  Returns all speakers in a session (with bio or fallback):
  ```json
  [
    {
      "id": 2,
      "name": "Jordan Brooks",
      "bio_text": "No bio available"
    }
  ]
  ```

---

## Tech Stack

- Python 3.13
- Flask
- Flask-SQLAlchemy
- Flask-Migrate
- SQLite (local dev)
- pytest

---

## Setup Instructions

1. Clone the repository:

   ```bash
   git clone <your-repo-url>
   cd flask-sqlalchemy-relationships-lab
   ```

2. Install dependencies:

   ```bash
   pipenv install
   pipenv shell
   ```

3. Navigate into `server/` and set env variables:

   ```bash
   cd server
   export FLASK_APP=app.py
   export FLASK_RUN_PORT=5555
   ```

4. Run migrations:

   ```bash
   flask db init
   flask db migrate -m "Initial migration"
   flask db upgrade
   ```

5. Seed the database:

   ```bash
   python seed.py
   ```

6. Run the app:

   ```bash
   flask run
   ```

7. Run tests:
   ```bash
   pytest
   ```

---

## Screenshot of Passing Tests

![Passing Tests](images/Screenshot%202025-07-25%20at%209.51.56 PM.png)

---

## Author

Andrew Snyder  
Bootcamp Lab – Flask SQLAlchemy Relationships  
Flatiron / 2025

---

## License

This lab was completed for educational purposes. No commercial use intended.
