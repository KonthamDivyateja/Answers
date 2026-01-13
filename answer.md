 # Answers

## 1. Node.js Architecture

Node.js is a JavaScript runtime that allows developers to run JavaScript outside the browser. It is designed to be asynchronous, non-blocking, and efficient for scalable applications.

### JavaScript Engine (V8)
V8 is Google’s JavaScript engine used by Node.js.
 It converts JavaScript code into machine code.
 It executes synchronous JavaScript operations.
 It handles memory management and garbage collection.

### Node.js Core APIs
 Core APIs are built-in modules provided by Node.js.
 Examples include `fs`, `http`, `path`, `events`, and `crypto`.
 These APIs help interact with files, network, and system resources.
 They are implemented using JavaScript and C++.

### Native Bindings
 Native bindings connect JavaScript with low-level C/C++ code.
 They allow Node.js to access system-level features.
 Used internally by modules like `fs` and `crypto`.
 They improve performance for heavy operations.

### Event Loop
 The event loop handles asynchronous operations.
 It checks different queues and executes callbacks.
 It allows Node.js to be non-blocking while using a single thread.
 Implemented internally using libuv.

---

## 2. libuv

### What is libuv?
 libuv is a C library used by Node.js.
 It provides support for asynchronous I/O operations.
 It works across multiple operating systems.

### Why Node.js Needs libuv
 JavaScript alone cannot handle async system-level tasks.
 libuv manages background tasks efficiently.
 It helps Node.js remain fast and non-blocking.

### Responsibilities of libuv
 Managing the event loop
 Handling asynchronous I/O
 Managing the thread pool
 Handling timers and callbacks
 Providing cross-platform compatibility

## 3. Thread Pool

### What is a Thread Pool?
 A thread pool is a set of background threads.
 Used to perform heavy or blocking operations.
 Node.js uses a default thread pool size of 4.

### Why Node.js Uses a Thread Pool
 To prevent blocking the main event loop.
 To handle CPU-intensive and blocking tasks.
 To improve performance and responsiveness.

### Operations Handled by the Thread Pool
 File system operations (`fs`)
 Cryptography tasks
 Compression (`zlib`)
 Some DNS operations

## 4. Worker Threads

### What Are Worker Threads?
Worker threads allow JavaScript code to run in parallel.
 Each worker has its own event loop and memory.
 Mainly used for CPU-intensive tasks.

### Why Worker Threads Are Needed
 To avoid blocking the main thread.
 To perform heavy computations efficiently.
 To improve application scalability.

### Difference Between Thread Pool and Worker Threads
 Thread pool is managed internally by Node.js.
 Worker threads are created explicitly by developers.
 Thread pool is for internal async tasks.
 Worker threads are for custom parallel execution.

## 5. Event Loop Queues

### Macro Task Queue
Contains tasks like:
  - `setTimeout`
  - `setInterval`
  - I/O callbacks
 Executed after the current execution completes.

### Micro Task Queue
 Contains tasks like:
  - `Promise.then`
  - `process.nextTick`
 Executed immediately after the current operation.

### Execution Priority
 Micro tasks are executed before macro tasks.
 Event loop always clears the micro task queue first.

### Examples
- Micro Task: Promise callbacks
- Macro Task: Timers and I/O callbacks
