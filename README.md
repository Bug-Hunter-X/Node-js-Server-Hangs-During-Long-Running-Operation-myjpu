# Node.js Server Hang During Long-Running Operation

This repository demonstrates a common issue in Node.js where a server becomes unresponsive due to a long-running operation blocking the event loop.  The problem is that the request handler doesn't yield control, preventing other requests from being processed. 

The `server.js` file shows the problematic code. The `serverSolution.js` file presents a solution using asynchronous operations to prevent the hang.

## How to reproduce:

1. Clone this repository.
2. Navigate to the directory.
3. Run `node server.js`. Make multiple requests to `http://localhost:3000`.
4. Notice that after a request, no further requests are responded to while the first request is being processed. 
5. Then Run `node serverSolution.js`. Make multiple requests to `http://localhost:3000`. 
6. Observe that requests are processed concurrently without blocking.

## Solution:

The solution involves using asynchronous programming techniques like promises or async/await to prevent blocking the event loop.