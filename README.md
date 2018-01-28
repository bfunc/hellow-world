# Distributed Messaging Guide 
Clone Pattern from ZeroMQ explained

![Both Server and Client consists of three sockets](http://res.cloudinary.com/bfunc/image/upload/v1517130840/ZeroMQ_semantics_bvzzxt.jpg "Clone Pattern")

Both Server and Client consists of three sockets: 

#### Server
* PUB - which is used to publish state updates to all subscribed clients
* PULL - which each individual client pushes its state changes to, and which server ultimately ends up publishing to all clients
* ROUTER - which is used to answer client requests to get server’s current absolute state. 

#### Client
Client also has three sockets, which are almost exact opposites of server’s socket set. 
* SUB - When client first starts, it uses a SUB socket to subscribe to all state changes that a server will publish
* REQ - after that, it creates a REQ socket to get server’s current absolute state which it will then remember and apply published updates to to stay in sync, and finally it uses
* PUSH - socket to send client's own state changes to the server.

