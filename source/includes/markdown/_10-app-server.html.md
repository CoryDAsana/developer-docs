<hr class="full-line">
<section class="platform-ui-alpha">

# App server

> Sample server code (do not use in production)

```shell
(an app server cannot be handled via curl)
```

```javascript--nodejs
// https://expressjs.com/en/starter/hello-world.html
const express = require('express')
const app = express()
const port = 3000

app.get('/', (req, res) => {
  res.send('Hello World!')
})

app.listen(port, () => {
  console.log(`Example app listening at http://localhost:${port}`)
})
```

```python
# https://flask.palletsprojects.com/en/1.1.x/quickstart/
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello, World!'
```

```ruby
# https://www.rubyguides.com/2016/08/build-your-own-web-server/
require 'socket'
server  = TCPServer.new('localhost', 80)
loop {
  client  = server.accept
  request = client.readpartial(2048)
  puts request
}
```

```java
// https://www.codejava.net/java-se/networking/java-socket-server-examples-tcp-ip
ServerSocket serverSocket = new ServerSocket(6868);
Socket socket = serverSocket.accept();

OutputStream output = socket.getOutputStream();
PrintWriter writer = new PrintWriter(output, true);
writer.println("Hello World");

socket.close();
```

```php
// https://www.php.net/manual/en/tutorial.firstpage.php
<?php
echo 'Hello World';
?>
```

An app server is required for working with [webhooks](/docs/webhooks)
and [app components](/docs/overview-of-app-components). An app server refers to
the server Asana directly sends requests to. This is different from the service
it may be connecting to in the end (e.g., Slack, Jira).

<hr>

## App server requirements

For some features, Asana needs to send requests to an app. In order for an app to
use these features, they will need to implement an app server. App servers are simply servers 
that an app controls. The server needs to be accessible via [HTTP requests](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods),
successfully return [response codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status), and sometimes return valid JSON bodies to
requests from Asana. Some requests will be sent from the client (i.e., an Asana user's browser), while other requests will be sent from Asana's servers. 

App servers define their own paths. Apps will need to declare the endpoints for Asana. For webhooks, 
this happens when you create a new webhook. For app components, some are declared on app creation while others are 
dynamically declared in responses to requests from Asana.

You should test/debug your app server with a tool like [Postman](https://www.postman.com/) or 
[Insomnia](https://insomnia.rest/).

In short:

 * App Servers need to accept HTTP requests and be accessible via URLs.
 * Request payloads will be JSON and app servers should respond with JSON (if a response 
 is needed).
 * Successful requests should respond with either a `200` or `204` status code. Some app components 
 have additional error handling for codes like `400`.
 * If an app server is down or throws a `500`, we will likely retry the request.

 <hr>

## Error handling and retry

If we attempt to send a request to an app server and we receive an error status code, or the 
request times out, we will retry delivery with exponential backoff. 

The tolerance threshold for retries vary between [webhooks](/docs/overview-of-webhooks) and [app components](/docs/overview-of-app-components). Refer to the 
documentation for each for detailed tutorials.

</section>