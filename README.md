# Parallel Computing Search Engine

## Project Overview

This is a **multi-threaded search engine** implementation using Java that demonstrates parallel computing principles. The project uses a **client-server architecture** with an **inverted index data structure** to efficiently search for words across multiple text files concurrently.

### What is it?

The Parallel Computing Search Engine is a distributed system that:
- **Builds an inverted index** from a dataset of text files using multiple threads
- **Searches for keywords** efficiently across all indexed files
- **Measures performance** by tracking how long indexing takes with different numbers of threads
- **Uses thread pooling** on the server side to handle multiple concurrent clients

### Why is it implemented?

This project demonstrates several important parallel computing concepts:

1. **Thread Pooling**: The server uses a fixed thread pool to manage multiple client connections efficiently
2. **Task Distribution**: Files are divided among worker threads for parallel processing
3. **Concurrent Data Structures**: `ConcurrentHashMap` is used to safely store the inverted index across multiple threads
4. **Performance Analysis**: The system measures and reports indexing time to analyze performance gains from parallelization
5. **Client-Server Communication**: Shows how to implement network communication between multiple clients and a server

### Architecture

**Components:**

- **Server** (`MultiThreadedServer.java`): Accepts client connections using a thread pool
- **Client** (`Client.java`): Connects to the server and sends search requests
- **ClientHandler** (`ClientHandler.java`): Handles individual client requests on the server
- **FileManager** (`FileManager.java`): Reads files and populates the inverted index
- **FileProcessor** (`FileProcessor.java`): Distributes file processing across multiple threads
- **FileProcessorThread** (`FileProcessorThread.java`): Worker thread that processes assigned files
- **InvertedIndex** (`InvertedIndex.java`): Thread-safe data structure mapping words to files

---

## Setup and Running Instructions

### Prerequisites

- Java Development Kit (JDK) 11 or higher installed
- IntelliJ IDEA or any Java IDE (optional but recommended)
- The dataset folder with test files (included in the repository)

### Step 1: Clone the Repository

```bash
git clone https://github.com/mounlie/search_engine_parallel_computing
cd search_engine_parallel_computing
```

### Step 2: Open the Project in Your IDE

1. Open your preferred Java IDE (IntelliJ IDEA, Eclipse, VS Code, etc.)
2. Open the project folder
3. Ensure the `dataset` folder is in the project root directory

### Step 3: Run the Server

1. Navigate to `src/server/MultiThreadedServer.java`
2. Click "Run" or press the Run button in your IDE
3. You should see the message: `Server is running. Waiting for connections...`

The server will listen on **localhost:8888** and use a thread pool of 5 threads to handle client connections.

### Step 4: Run the Client

1. Open a terminal or new run configuration
2. Navigate to `src/client/Client.java`
3. Click "Run" or press the Run button in your IDE
4. Follow the on-screen prompts:

   ```
   Enter num of threads: <enter a number, e.g., 1, 2, 4, 8>
   Time for building XXXX ms, threads: X
   Enter the word: <enter a word to search for, e.g., "python">
   Matching files:
   [list of files containing the word]
   Do you want to search for more words? (yes/no): <yes or no>
   ```

### Step 5: Run Multiple Clients (Optional)

You can run multiple client instances simultaneously to test the server's ability to handle concurrent connections:

1. Start the server once
2. Run the Client class multiple times (in separate terminal windows or IDE run configurations)
3. Each client can perform searches independently while the server handles all connections
