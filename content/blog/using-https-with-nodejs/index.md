---
title: Securing Apps with HTTPS protocol
date: 2021-05-14
description: NodeJS offers a convenient and easy abstraction to create a web
  server. One of the first and foremost steps to secure the apps we're building
  is to run them with https protocol.
---

In this blog, we'll see how easily we can secure an app that is running on NodeJS by adding the `HTTPS` protocol.

Many of the NodeJs developers would have started their journey with NodeJs by seeing the following code.

```
const http = require("http");
const portNumber = 4500;
const server = http.createServer((req, res) => {
  res.writeHead(200, { "Content-Type": "text/plain" });
  res.end("Hello, World");
});

server.listen(portNumber, () => {
  console.log(`Web Server is running at http://localhost:${portNumber}`);
});

```
The above 5(<10 with formatting) lines of code will create a web server that listens on port number 4500, and responds with the message Hello, World for every request.

The hello-world server runs on the `HTTP` protocol. This means the data exchange between the client and the server happens in plain text format.

To secure the data that is being transferred between the client and the server, `HTTPS` is the defeacto protocol as the S in `HTTPS` stands for secure and the data is transferred in an encrypted format.

So, how can we create a so-called `HTTPS` server? Like any other encryption program, `HTTPS` server also needs a secret key and an SSL certificate.

>Where do I get a certificate from? Luckily with tools like [openssl](https://www.openssl.org/) it is very easy for one to generate a certificate for development purposes. For PRODUCTION application purposes, always use a certificate that is signed by a certificate issuing authority.  

Once the certificate is in place, with the below code, we can create an `HTTPS` server and see how easily we are able to create a web server that handles the traffic securely.

```
const https = require("https");
const fs = require("fs");
const portNumber = 2443;
const options = {
  pfx: fs.readFileSync("certs/self-signed-cert.pfx"),
  passphrase: "sample",
};

const server = https
  .createServer(options, (req, res) => {
    res.writeHead(200, { "Content-Type": "text/plain" });
    res.end("Hello, World");
  })
  
server.listen(portNumber);

```

- Remember that even though the server is running on `HTTPS` protocol, you will need to take a lot of precautions to secure the data and your server(using things like rate limiting to prevent from DoS attacks) and have a defensive coding approach when working with browser-based internet-facing applications. Always look up the [OWASP-NODEJS-CHEATSHEET](https://cheatsheetseries.owasp.org/cheatsheets/Nodejs_Security_Cheat_Sheet.html) and implement the best practices to the possible extent. 