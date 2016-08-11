# jQuery Simple WebSocket
Send and receive data through a fluent deferred interface, handling connections gracefully.

## Example

```
<script type="text/javascript" src="https://code.jquery.com/jquery-1.12.0.min.js"></script>
<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/jquery-json/2.5.1/jquery.json.min.js"></script>
<script type="text/javascript" src="jquery.simple.websocket.js"></script>
<script type="text/javascript">
    var webSocket = $.simpleWebSocket({ url: 'ws://127.0.0.1:3000/' });
    
    // reconnected listening
    webSocket.listen(function(message) {
        console.log(message.text);
    });

    webSocket.send({ 'text': 'hello' }).done(function() {
        // message send
    }).fail(function(e) {
        // error sending
    });
</script>
```

fluent:
```
var webSocket = $.simpleWebSocket({ url: 'ws://127.0.0.1:3000/' })
.listen(function(message) { console.log('listener1: '+message.text); })
.listen(function(message) { console.log('listener2: '+message.text); })
.listen(function(message) { console.log('listener3: '+message.text); })
.send({'text': 'hello'});
```

# Usage
```
var socket = $.simpleWebSocket({
                                 url: 'ws://127.0.0.1:3000/',
                                 protocols: 'your_protocol', // optional
                                 timeout: 20000, // optional, default timeout between connection attempts
                                 attempts: 60, // optional, default attempts until closing connection
                                 dataType: 'json' // optional (xml, json, text), default json
                               });

socket.connect();

socket.isConnected(); // or: socket.isConnected(function(connected) {});

socket.send({'foo': 'bar'});

socket.listen(function(data) {});

socket.remove(listenerCallback);

socket.removeAll();

socket.close();
```

### Web Chat Example
- start nodejs websocket server:
```
$ node tests/server.js
```
- open tests/example.html

# History
- jQuery Simple Web Socket has been forked from https://github.com/dchelimsky/jquery-websocket
- which originates from http://code.google.com/p/jquery-websocket/

