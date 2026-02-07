# Nginx Log Analyzer

A lightweight, high-performance Bash script designed to parse and analyze Nginx access logs. Using `awk` and standard Unix processing tools, this script provides instant insights into traffic patterns, potential security threats, and server performance.

## 🚀 Features

The analyzer extracts and summarizes the **top 5** occurrences for the following metrics:
* **IP Addresses:** Identify your most active visitors or potential DDoS sources.
* **Requested Paths:** See which API endpoints or pages are hit most frequently.
* **HTTP Status Codes:** Quickly spot `404 Not Found` spikes or `500 Internal Server Errors`.
* **User Agents:** Understand the browsers, bots, or devices accessing your server.


## 📋 Prerequisites

* A Linux/Unix-based environment (Bash).
* Standard utilities: `awk`, `sort`, `head`.
* An `nginx.log` file located in the same directory as the script.


## 🛠️ Usage

1.  **Git clone this repo**
    ```git
    git clone https://github.com/2Kelvin/nginx-logs-analyser.git
    ```
2.  **Grant execution permissions**:
    ```bash
    chmod +x analyzer
    ```
4.  **Run the script**:
    ```bash
    ./analyzer
    ```


## 🔍 How It Works

The script leverages `awk`'s associative arrays to count occurrences efficiently.

| Metric | Logic |
| :--- | :--- |
| **IP Addresses** | Aggregates the 1st column (`$1`) of the log file. |
| **Paths** | Targets the 7th column (`$7`), usually the request URI. |
| **Status Codes** | Aggregates the 9th column (`$9`) representing HTTP responses. |
| **User Agents** | Uses a custom field separator `-F\"` to isolate the string within quotes at the end of the log line. |


## 📄 Example Output

