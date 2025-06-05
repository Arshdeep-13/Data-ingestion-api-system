# ⚙️ Data Ingestion API System (MERN Stack)

This project implements a RESTful **Data Ingestion API system** using the MERN stack (MongoDB, Express.js, Node.js). It allows ingestion of IDs with different priorities, processes them asynchronously in batches of 3, and respects a strict rate limit of 1 batch every 5 seconds.

---

## 📌 Features

- ✅ Submit ingestion requests with a list of IDs and priority (HIGH, MEDIUM, LOW)
- ✅ Automatically split IDs into batches of 3
- ✅ Process batches asynchronously with a delay of 1 batch every 5 seconds
- ✅ Higher priority ingestion requests get processed first
- ✅ Track ingestion and batch status in real time
- ✅ Fully RESTful API endpoints

---

## 🛠️ Tech Stack

| Technology      | Purpose                                              |
| --------------- | ---------------------------------------------------- |
| **MongoDB**     | NoSQL database to store ingestion and batch statuses |
| **Express.js**  | Web framework for handling HTTP requests             |
| **Node.js**     | Server-side runtime environment                      |
| **Mongoose**    | MongoDB ORM for modeling                             |
| **UUID**        | Generate unique IDs for ingestions and batches       |
| **setInterval** | Background batch processing                          |
| **dotenv**      | Environment configuration management                 |

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/mern-ingestion-api.git
cd mern-ingestion-api
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Setup Environment Variables

Create a .env file:

```bash
MONGO_URI=mongodb+srv://arshdeeprooprai:Arshdeep%40LoopAi@cluster0.pbx3xz1.mongodb.net/?retryWrites=true&w=majority&appName=Cluster0
```

Or use your cloud Mongo URI (MongoDB Atlas)

### 4. Start the Server

```bash

npm start
Server will run at http://localhost:8000
```

## 📦 API Endpoints

## 📥 POST /ingest

Submit a new ingestion request.

Request Body:

```json
{
  "ids": [1, 2, 3, 4, 5],
  "priority": "HIGH"
}
```

Response:

```json
{
  "ingestion_id": "abc123"
}
```

## 📊 GET /status/:ingestion_id

Check the status of an ingestion request.

Response:

```json
{
  "ingestion_id": "abc123",
  "status": "triggered",
  "batches": [
    {
      "batch_id": "uuid1",
      "ids": [1, 2, 3],
      "status": "completed"
    },
    {
      "batch_id": "uuid2",
      "ids": [4, 5],
      "status": "triggered"
    }
  ]
}
```

## 🧪 Running Tests

Add your tests using Jest or Supertest:

```bash
npm test
Or test endpoints using Postman or curl.
```

### ✅ Sample Curl Commands

```bash
# Ingest request

curl -X POST http://localhost:5000/ingest \
-H "Content-Type: application/json" \
-d '{"ids": [1, 2, 3, 4, 5], "priority": "HIGH"}'

# Status check

curl http://localhost:5000/status/abc123
```

✍️ Author
Arshdeep Rooprai
GitHub: Arshdeep-13
