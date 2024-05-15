# Node.js Interview Prep

## What is Node.js?

Node.js is a JavaScript runtime environment that executes JavaScript code outside the browser. It is made with the combination of Chrome V8 engine, libUV, and some other dependencies. The libUV library is written in C++ and it makes Node.js asynchronous and responsible for event loop.

## Why Node.js?

Node.js and Java are both powerful technologies for building server-side applications, but they have some differences in their approach and use cases. Here are some reasons why you might choose Node.js over Java:

- **JavaScript familiarity:** Node.js is built on top of JavaScript, which is a popular programming language that many developers are already familiar with. This can make it easier to get started with Node.js and reduce the learning curve for building server-side applications.

- **Performance:** Node.js is known for its high-performance capabilities, particularly when it comes to handling a large number of concurrent connections. This makes it well-suited for applications that require real-time data processing, such as chat applications or streaming services.

- **Scalability:** Node.js is designed to be scalable, with the ability to handle multiple requests at the same time. This makes it a good choice for building applications that need to handle a high volume of traffic.

- **Lightweight:** Node.js is relatively lightweight compared to other server-side technologies like Java, which can make it easier to deploy and maintain.

- **Active community:** Node.js has a large and active community of developers, which means that there are plenty of resources available for learning and troubleshooting. This can be particularly helpful for developers who are new to server-side programming.

## Disadvantages of Node.js

While Node.js has many advantages, it also has some potential disadvantages that developers should consider when choosing a technology for their projects. Here are some of the disadvantages of Node.js:

- **Limited multi-threading:** Node.js uses a single thread to handle all requests, which can limit its ability to handle heavy CPU-bound workloads.

- **Immaturity of some modules:** The Node.js ecosystem is large and rapidly evolving, which can lead to issues with module quality and compatibility. Some modules may be poorly documented or lack community support, making it difficult to use them effectively.

- **Debugging:** Debugging Node.js applications can be challenging, especially when it comes to complex, asynchronous code.

- **Security concerns:** Because Node.js is built on top of the V8 engine, which is written in C++, it can be vulnerable to certain types of security vulnerabilities, such as buffer overflow attacks.

- **Scalability limitations:** While Node.js can scale well for certain types of applications, it may not be the best choice for applications that require massive scaling, such as those that handle large amounts of data or traffic.

It's important to note that these disadvantages are not inherent to Node.js itself, but rather represent potential issues that developers should consider when choosing a technology for their projects. In many cases, these issues can be mitigated or worked around by using best practices and leveraging the strengths of the platform.


# Architecture of Node.js

## Dependencies of Node.js

There are 2 major dependencies of Node.js:

### V8 Engine

It is responsible for executing JavaScript code. Without V8, it would be impossible to execute JavaScript code. It converts JavaScript code to machine code.

### LibUV

It is an open-source library focused on asynchronous I/O. It provides access to compute OS, filesystem, and networking. LibUV implements two important features of Node.js: event loop and thread pool.

- **Event Loop**: Responsible for handling easy tasks like executing callback functions, timers, or compression.
- **Thread Pool**: Used for more heavy work like asynchronous I/O, file access, and compression.

Node.js also utilizes other dependencies like:

- **Http Parser**: For parsing HTTP.
- **C-ares**: For DNS requests.
- **OpenSSL**: For cryptography.
- **Zlib**: For compression.

## REPL in Node.js

To start the Node.js REPL, simply use the `node` command.

### Readline Command

You can read input from the terminal and output something to the terminal through this command.

### Read and Write Files Synchronously

```javascript
let textIn = fs.readFileSync('./Files/input.txt', 'utf-8');
console.log(textIn);
let content = `Data read from input.txt: ${textIn}. \nDate created ${new Date()}`;
fs.writeFileSync('./Files/output.txt', content);
```
