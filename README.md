# Distributed Web Crawler & Content Parser

An intermediate-to-advanced, highly concurrent web crawler architecture designed to safely extract web content at scale without task duplication. 

## 🛠️ Tech Stack & Architecture
* **Language & Runtime:** Python (Google Colab Environment)
* **Concurrency Engine:** Asynchronous I/O using `asyncio` and `aiohttp` for non-blocking network requests.
* **Distributed Queue System:** Centralized state tracking using **Redis Sets** (`crawler:frontier` and `crawler:visited`) to manage shared atomic message-popping and guarantee zero duplicate crawls across multiple workers.
* **Content Extraction Pipeline:** Structural HTML tokenization and deep hyperlink discovery utilizing `BeautifulSoup4` and `lxml`.
* **Persistence Layer:** Structured relational archiving using a local `SQLite` database.

## 📈 System Performance & Benchmarks
* **Throughput:** Processes **90+ unique pages per minute** utilizing 3 concurrent worker tasks.
* **Persistence:** Successfully logs unique target URL pathways, page titles, and description metadata into a local relational database storage layout without operational conflicts.
* **Politeness Constraints:** Built-in custom request-delay pacing mechanisms and back-off delays to respect target domain server resource boundaries.

## 📁 Repository Structure
* `Distributed_Crawler.ipynb`: The complete Google Colab notebook containing the background Redis daemon configuration, the SQLite persistence layer, the asynchronous multi-worker orchestration engine, and data validation query scripts.

## 🚀 How to Run (Inside Google Colab)
1. Upload the `.ipynb` file to your Google Drive and open it with Google Colab.
2. Run **Cell 1** to install dependencies and downloand the background Linux `redis-server` system packages.
3. Execute **Cell 2** to launch the Redis database server system process in daemon mode.
4. Execute **Cell 3** to start the concurrent worker loop. Press the "Stop" icon next to the running cell at any point to halt crawling and inspect your saved database file!
