🔗 URL Shortener in C++
# cpp-url-shortener

A lightweight URL shortening service written in C++ using [`cpp-httplib`](https://github.com/yhirose/cpp-httplib) and [`nlohmann/json`](https://github.com/nlohmann/json). This project mimics the basic functionality of services like [bit.ly](https://bit.ly) or [TinyURL](https://tinyurl.com).

## 🔗 Features

- Convert long URLs into short aliases
- Retrieve the original URL from a shortened version
- Simple hash-based storage (no external database)
- RESTful API using HTTP POST and GET
- Tested using [Postman](https://www.postman.com/)

---

## 🛠️ Tech Stack

- C++17
- [cpp-httplib](https://github.com/yhirose/cpp-httplib) - Lightweight HTTP server
- [nlohmann/json](https://github.com/nlohmann/json) - JSON parsing
- Windows (WinSock2 required for `cpp-httplib`)

---

## 📦 Dependencies

- C++ compiler (e.g., g++)
- `cpp-httplib` header-only library
- `nlohmann/json` header-only library
- WinSock2 (`-lws2_32` required for Windows)

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/cpp-url-shortener.git
cd cpp-url-shortener
2. Compile the Code
bash
Copy
Edit
g++ -Icpp-httplib -Ijson/include -o shortenurl shortenurl.cpp -lws2_32
3. Run the Server
bash
Copy
Edit
./shortenurl
Server will start at http://localhost:8080

📨 API Endpoints
POST /shorten
Description: Shortens a long URL.

Request:

http
Copy
Edit
POST /shorten?longUrl=https://example.com
Response:

json
Copy
Edit
{
  "shortUrl": "a1B"
}
GET /:shortUrl
Description: Retrieves the original URL.

Request:

http
Copy
Edit
GET /a1B
Response (found):

json
Copy
Edit
{
  "url": "https://example.com",
  "statusCode": 302
}
Response (not found):

json
Copy
Edit
{
  "url": "",
  "statusCode": 404
}
📁 Project Structure
pgsql
Copy
Edit
cpp-url-shortener/
│
├── shortenurl.cpp       # Main server logic
├── cpp-httplib/         # Header-only HTTP server
├── json/                # nlohmann/json library
└── README.md            # Project documentation
🧪 Testing
You can use Postman or cURL to test the API.

Example using curl:

bash
Copy
Edit
curl -X POST "http://localhost:8080/shorten?longUrl=https://openai.com"
curl http://localhost:8080/a1B
📌 Notes
The project uses an in-memory hash table and is not persistent.

Base62 encoding ensures short and human-readable aliases.

Hash collisions are resolved using linear probing (open addressing).

📃 License
This project is licensed under the MIT License. See LICENSE file for details.

🙌 Acknowledgements
cpp-httplib

nlohmann/json

✨ Future Improvements
Add persistent storage (e.g., file or database)

Implement URL validation

Add expiration support for short URLs

Add a simple web UI

yaml
Copy
Edit

