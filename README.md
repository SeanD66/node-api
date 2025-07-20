<h2>Node-API</h2>
<pre>This repository consists of building a simple web application using Docker, JS, and JSON.</pre>

<h2>Author</h2>
<pre>
Sean Daweng
</pre>

<h2>Node-API overview</h2>
<pre>
Tools: docker
Goal: Containerize a basic Node-API web app
Skills: Multi-stage builds, Utilizing index.js, and package.json
</pre>

<h2>Repository Structure</h2>
<pre>
docker-beginner-sandbox/
    ├── node-api/
    |    ├── index.js
    │    ├── package.json
    │    └── Dockerfile
</pre>

<h2>Steps:</h2>

1) Create a structured directories to start this project.
<pre>
mkdir docker-beginner-sandbox/
cd docker-beginner-sandbox
mkdir node-api
cd node-api
touch index.js
touch package.json
touch Dockerfile
</pre>

2) Get into package.json file by:
<pre>
vim package.json
</pre>
Insert the content inside package.json file
<pre>
{
  "name": "node-api-sandbox",
  "version": "1.0.0",
  "main": "index.js",
  "dependencies": {
    "express": "^4.18.2"
  }
}
</pre>
Close the file and save during the vim session:
<pre>
:wq
</pre>

3) Edit javascript.js:
<pre>
vim javascript.js
</pre>
Enter the contents inside the javascript.js file:
<pre>
const express = require('express');
const app = express();
const PORT = 4000;

app.get('/', (req, res) => res.send('Hello from Dockerized Node API!'));

app.listen(PORT, () => console.log(`Server listening on port ${PORT}`));
</pre>
Close and save the file during vim session:
<pre>
:wq
</pre>

4) Open and edit Dockerfile:
<pre>
vim Dockerfile
</pre>
Enter the contents to Dockerfile:
<pre>
FROM node:18-alpine
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
CMD ["node", "index.js"]
</pre>
Close the Dockerfile and save by:
<pre>
:wq
</pre>

5) Build and run node-api:
<pre>
cd node-api
docker build -t node-api-sandbox .
docker run-p 4000:4000 node-api-sandbox
</pre>

6) Open http://localhost:4000 from your local browser.




