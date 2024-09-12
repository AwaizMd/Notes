# Request-Response Pattern
===========================================

A classic and elegant communication design pattern for backend requests, widely used in:

- Web
- DNS
- RPC
- SQL
- APIs
- GraphQL

## Anatomy of a Request

A request structure is defined by both the client and server, based on the protocol being used. A request typically consists of:

- **Method**: `GET`, `POST`, `PUT`, `DELETE`
- **Path**: The URL path
- **Protocol version**: HTTP/1.1, HTTP/2, etc.
- **Headers**: Key-value pairs providing meta-information
- **Body (optional)**: Payload for methods like `POST` or `PUT`

```js
const express = require('express');
const app = express();

app.use(express.json()); // For parsing JSON request body

// Handle GET request
app.get('/api/data', (req, res) => {
  console.log('GET Request Received');
  console.log('Headers:', req.headers);
  res.send({ message: 'Here is some data' });
});

// Handle POST request
app.post('/api/data', (req, res) => {
  console.log('POST Request Received');
  console.log('Headers:', req.headers);
  console.log('Body:', req.body);
  res.status(201).send({ message: 'Data received successfully!' });
});

app.listen(3000, () => {
  console.log('Server listening on port 3000');
});

```

## Anatomy of a Response

The response structure mirrors the request, containing:

- **Status code**: HTTP status codes like 200, 404, 500
- **Headers**: Key-value pairs for metadata
- **Body (optional)**: Data sent back to the client


```js

app.get('/api/status', (req, res) => {
  // Set custom headers
  res.set('X-Custom-Header', 'MyHeaderValue');

  // Send a status code and response body
  res.status(200).send({
    status: 'Success',
    message: 'Operation completed successfully',
  });
});


```

## Serialization and Deserialization

- **Serialization**: Converting data into a format suitable for network transmission, e.g., JSON, XML, or protocol buffers.
- **Deserialization**: Converting the transmitted data back into a usable format.
- **Cost**: Serialization and deserialization have performance costs, especially with large data.

```js
// Serialization: Converting JavaScript object to JSON
const data = { name: 'Alice', age: 30 };
const serializedData = JSON.stringify(data);
console.log('Serialized:', serializedData);

// Deserialization: Parsing JSON string to JavaScript object
const deserializedData = JSON.parse(serializedData);
console.log('Deserialized:', deserializedData);

```

## Request-Response Pattern Variations

- **Chunking**: Sending large files in smaller chunks.
- **Polling**: Clients repeatedly check for new data by sending requests at regular intervals.
- **Asynchronous Processing**: The server processes the request in the background and sends the response when the task completes.


```js

// chunking
const fs = require('fs');
const http = require('http');

const server = http.createServer((req, res) => {
  const readStream = fs.createReadStream('largeFile.txt'); // Large file

  res.writeHead(200, { 'Content-Type': 'text/plain' });
  
  // Pipe data in chunks to the response
  readStream.pipe(res);
});

server.listen(3000, () => {
  console.log('Server listening on port 3000');
});

// polling client

<!-- Client-side polling -->
<script>
  function pollServer() {
    fetch('/api/notifications')
      .then(response => response.json())
      .then(data => {
        console.log('New Notifications:', data);
      })
      .catch(err => console.error('Error:', err));
  }

  // Poll the server every 5 seconds
  setInterval(pollServer, 5000);
</script>


// Asynchronous Processing

app.get('/api/async', (req, res) => {
  console.log('Request received, processing...');

  // Simulate asynchronous processing
  setTimeout(() => {
    res.send({ message: 'Asynchronous processing complete!' });
  }, 3000); // 3 seconds delay
});


```

## Challenges and Limitations

- **Large files** can be difficult to send and process.
- **Long-running requests** may introduce latency and cause congestion.
- **Client disconnections** can result in incomplete requests or responses.
- **Polling inefficiency**: Repeated requests can congest the server.


```js

const multer = require('multer');
const upload = multer({ dest: 'uploads/' });

app.post('/upload', upload.single('file'), (req, res) => {
  console.log('File received:', req.file);
  res.send('File uploaded successfully!');
});

```
---

# Demo: Request-Response Pattern in Node.js

```javascript
const http = require('http');

const server = http.createServer((req, res) => {
  // Request received
  console.log(`Request received: ${req.method} ${req.url}`);

  // Process the request
  const responseBody = `Hello, World! You requested ${req.url}`;

  // Send the response
  res.writeHead(200, { 'Content-Type': 'text/plain' });
  res.end(responseBody);

  console.log(`Response sent: ${responseBody}`);
});

server.listen(3000, () => {
  console.log('Server listening on port 3000');
});
```

# Synchronous vs Asynchronous Execution
=====================================

### Synchronous Execution

* Like a sine wave where the request and response are in sync and going in the same direction.
* Synchronous I/O: the caller sends a request and blocks, meaning it cannot do anything else until it receives a response.

### Asynchronous Execution

* When the client and server are not in sync.
* Asynchronous I/O: the caller sends a request and moves on, allowing other processes to execute in the meantime.
* Preferable in programming because it allows for more efficient use of resources.

Examples of Synchronous and Asynchronous I/O
------------------------------------------

### Synchronous I/O Example

* Program asks OS to read from disk and the program manager is taken off the CPU until the read operation is complete.

### Asynchronous I/O Example

* Program sends a request to read from disk and moves on to other tasks while the read operation is being performed.
* The program can then check if the response is ready using a polling mechanism or by using a callback function.

### Asynchronous Programming
-----------------------

* When a function is marked as async, allowing the program to move on to other tasks while the function is being executed.
* Asynchronous backend processing: the backend puts a request into a queue and immediately responds to the client with a job ID, allowing the client to check back later for the results.

### Asynchronous Commits in Postgres
-------------------------------

* When the database writes the transaction to the wall (journal of changes) and immediately returns success to the client, without waiting for the write operation to disk to succeed.
* Can increase performance, but at the cost of consistency.

### Asynchronous Replication
-----------------------

* When the primary database writes to the secondary databases asynchronously, allowing for faster write operations but at the cost of consistency.

### Asynchronous vs Synchronous in the Operating System
------------------------------------------------

* In the operating system, writes to the disk are stored in the OS file system cache and are flushed to disk asynchronously.
* However, databases often require strong consistency and may use the fsync property to force writes to disk synchronously, bypassing the OS cache.

Demonstration of Synchronous and Asynchronous Execution in Node.js
----------------------------------------------------------------

* The lecture includes a demonstration of synchronous and asynchronous execution in Node.js using the fs module to read a file.
* In the synchronous example, the program blocks and waits for the file to be read before moving on to the next task.
* In the asynchronous example, the program moves on to the next task and uses a callback function to handle the response from the file read operation.


# Push Concept in Backend Engineering
=====================================

## Key Points

### Real-time Connection

In a push model, the client establishes a connection with the server, and the server sends data to the client as soon as it becomes available. This eliminates the need for the client to continuously poll the server for updates, resulting in a real-time or near-real-time experience.

### Pros

* **Real-time Updates**: Clients receive information instantly, which is ideal for applications requiring immediate feedback or data updates (e.g., chat applications, live sports scores).
* **Efficiency**: Reduces the need for clients to repeatedly request updates, which can be more efficient in terms of network and server load.

### Cons

* **Client Must Be Online**: The client needs to maintain an active connection to receive updates. If the client is offline, it won’t receive notifications or updates until it reconnects.
* **Scalability Issues**: Handling a large volume of simultaneous connections can be challenging. For instance, a server may struggle to manage millions of active connections or push notifications, leading to performance issues.
* **Resource Intensive**: Servers must manage and maintain many open connections and handle the real-time data flow, which can be resource-intensive.
* **Requires Bi-Directional Communication**: Many push technologies rely on protocols that support two-way communication, such as WebSockets. This is more complex than traditional request-response protocols.
* **Client Limitations**: Not all clients may be able to handle large volumes of incoming data or notifications efficiently.

## Examples

* **Push Notifications**: Common in mobile applications and websites to notify users of new messages, updates, or alerts.
* **Live Updates**: Applications like stock trading platforms or social media feeds use push mechanisms to deliver real-time updates to users.

## Scalability and Alternatives

* **Long Polling**: In some cases, long polling can be used as an alternative to push. Long polling involves the client sending a request to the server, which holds the request open until new data is available. This approach can be less resource-intensive for the server compared to managing numerous persistent connections.
* **Message Brokers**: Systems like Kafka are used to manage and distribute large volumes of messages efficiently. They can handle high throughput and provide features like message queuing and streaming, which helps in managing push notifications for millions of users more effectively.

## Challenges

* **High Load Management**: For example, a YouTube channel with millions of subscribers sending notifications about new video uploads would require a robust system to handle the notification load. Efficient load distribution and scaling strategies are crucial to manage such high volumes.


# Short Polling in Distributed Systems
=====================================================================

Short polling is a simple and popular communication design pattern used for checking the status of long-running backend tasks. It works by having the client poll the server repeatedly to check if the task has been completed.

## Concept of Short Polling

- **Client Request**: The client sends a request.
- **Immediate Response**: The server returns a job ID (or handle).
- **Async Backend Processing**: The server processes the task asynchronously.
- **Polling**: The client polls the server periodically to check task status using the job ID.
- **Completion**: Once the task is complete, the server responds with the result during the next poll.

### Example Use Case
**YouTube Video Upload**: 
When uploading a video, YouTube assigns an upload ID. The backend processes the upload, while the client periodically checks the status.

---

## Steps in Short Polling

1. **Client Submits Request**:
   - The request is submitted to the server.
   - The server generates a job ID and immediately returns it.

2. **Background Processing**:
   - The server processes the task asynchronously (e.g., adds it to a queue).

3. **Polling**:
   - The client checks the status at regular intervals using the job ID.

4. **Job Completion**:
   - Once the job is complete, the server returns the result during the next poll.

5. **Client Disconnection Handling**:
   - Even if the client disconnects, the job continues on the backend.

---

## Advantages

- **Simplicity**: Easy to implement for both client and server.
- **Suitable for Long-running Requests**: Ideal for tasks that take time to complete.
- **Asynchronous Handling**: Clients can disconnect and reconnect later.

## Disadvantages

- **Network Overhead**: Very chatty, causing high network traffic.
- **Resource Wastage**: Polling consumes backend and network resources.
- **Scaling Issues**: High load as the number of clients increases.

---

## Example Implementation

```js
// Node.js and Express Backend Example

const express = require('express');
const app = express();
const jobs = {};  // Stores job ID and its progress

// Submit a new job
app.post('/submit', (req, res) => {
    const jobId = Date.now();  // Generate unique job ID based on time
    jobs[jobId] =  0 ;  // Initialize progress

    // Start processing the job asynchronously
    updateJob(jobId);

    // Respond with the job ID
    res.json({ jobId });
});

// Update job progress every 5 seconds
function updateJob(jobId) {
    setTimeout(() => {
        jobs[jobId].progress += 10;  // Increment progress by 10%

        if (jobs[jobId].progress < 100) {
            updateJob(jobId);  // Continue updating if not complete
        }
    }, 3000);
}

// Check job status
app.get('/status', (req, res) => {
    const jobId = req.query.jobId;
    if (jobs[jobId]) {
        res.json({ progress: jobs[jobId].progress });
    } else {
        res.status(404).send('Job not found');
    }
});

// Start the server
app.listen(8080, () => {
    console.log('Server running on port 8080');
});

```
### Real-world Examples

   - **File Upload**: Polling can check the status of large file uploads in cloud storage.
   - **Banking Transactions**: Used to check the status of long-running transactions.
   - **CI/CD Systems**: Polling checks the status of build jobs in systems like Jenkins.


<table>
  <tr>
    <th>Pros</th>
    <th>Cons</th>
  </tr>
  <tr>
    <td>Simple and easy to implement</td>
    <td>Chatty, leading to high network traffic</td>
  </tr>
  <tr>
    <td>Good for long-running processes</td>
    <td>Wastes backend and network resources</td>
  </tr>
  <tr>
    <td>Client disconnection is safe</td>
    <td>Scaling to thousands of clients can create bottlenecks</td>
  </tr>
  <tr>
    <td>Asynchronous backend handling</td>
    <td>High resource consumption and cloud billing issues</td>
  </tr>
</table>


**Conclusion**

Short polling is a straightforward solution for long-running asynchronous tasks. However, its network inefficiencies make it more suitable for smaller-scale applications. For larger systems, techniques like long polling or event-driven architectures (e.g., Kafka, WebSockets) are more efficient.

