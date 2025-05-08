🔗 URL Shortener in C++
This is a simple URL Shortener server written in C++, using cpp-httplib for HTTP functionality and nlohmann/json for JSON serialization.

It accepts a long URL and returns a unique shortened version, then allows retrieval of the original URL via the shortened one.

🚀 Features
Convert long URLs to short codes using hashing + Base62

Store mappings in memory using unordered_map

Exposes RESTful API endpoints:

POST /shorten?longUrl=<URL>: returns a short URL

GET /<shortCode>: redirects (returns original URL in JSON)

🔧 Requirements
C++ compiler with C++11 support

Windows OS (uses winsock2.h)

External libraries:

cpp-httplib

nlohmann/json

🛠️ Installation & Compilation
Clone this repository:

git clone https://github.com/your-username/url-shortener-cpp.git
cd url-shortener-cpp
Make sure you have the required libraries:

Place httplib.h from cpp-httplib in the project folder

Place json.hpp from nlohmann/json in the include folder

Compile:

g++ -I./cpp-httplib-master/ -I./json-develop/include -o shortenurl shortenurl.cpp -lws2_32
▶️ Usage
Run the server:

./shortenurl
Example API Calls:

Shorten URL:

POST http://localhost:8080/shorten?longUrl=https://example.com
Response: "aB3kZ1" (short code)
Retrieve URL:

GET http://localhost:8080/aB3kZ1
Response: {
  "url": "https://example.com",
  "statusCode": 302
}
📁 Project Structure

shortenurl.cpp        # Main source code
cpp-httplib-master/   # Directory containing httplib.h
json-develop/include/ # Directory containing json.hpp
📌 Notes
Currently, the short URL data is stored in memory only — restarting the server resets mappings.

No collision detection is implemented; hash collisions may overwrite URLs.

This implementation is intended for learning or demonstration purposes.
