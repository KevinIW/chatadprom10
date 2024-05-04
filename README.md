<details>

<summary>Modul 10 tutorial 2</summary


2.1 Original code of broadcast chat.

Server :

![alt text](image.png)

Client 1 :

![alt text](image-1.png)

Client 2:

![alt text](image-2.png)

Client 3:

![alt text](image-3.png)

First add this

[[bin]]
name = "server"

[[bin]]
name = "client"

The Cargo.toml file is the manifest file for Rust's package manager, Cargo. It contains all the metadata that Cargo needs to compile your project.

If we want to run client.rs and server.rs as binaries, you need to specify them under the [[bin]] section in the Cargo.toml file. This is because by default, Cargo only compiles src/main.rs as a binary

then run 

cargo run --bin server and cargo run --bin client 

then start chatting in 3 terminal in the client.rs


2.2 Modifying the websocket port

To modify the port to be 8080, we need to change the port number where the server binds and where the client connects

We change this code in server.rs

let listener = TcpListener::bind("127.0.0.1:8080").await?; in main function then in client.rs

we change this code 

 ClientBuilder::from_uri(Uri::from_static("ws://127.0.0.1:8080"))
            .connect()
            .await?;

The WebSocket protocol is a computer communications protocol, providing full-duplex communication channels over a single TCP connection. It is designed to be implemented in web browsers and web servers, but it can be used by any client or server application. The WebSocket protocol makes more interaction between a browser and a website possible, facilitating live content and the creation of real-time games.

 The server is binding to a TCP listener on a specific port (in this case, 8080), and the client is connecting to the server using the WebSocket protocol at the same port. thus it apply websocker protocol


 2.3 Small changes. Add some information to client

Server:

![alt text](image-4.png)

Client 1:
![alt text](image-5.png)

Client 2:
![alt text](image-6.png)

CLient 3:
![alt text](image-7.png)

In this new code first we modified the client code like this  
                match incoming {
                    Some(Ok(msg)) => {
                        if let Some(text) = msg.as_text() {
                            println!("Kevin's Computer - From server: {}", text);
                        }
                    },

We modified it so we can display the sender information along with the message content.
This modification allows each client to show messages along with details about the sender, providing context about the origin of each message.

In the server side with modify 

                        println!("From client {addr:?} {text:?}");
                            let newChat = addr.to_string() + ": " + text;
                            bcast_tx.send(newChat.into())?;

we need to show information about the sender (in this case, the client's IP address and port) to the message before broadcasting it to all clients.
This modification ensures that each client receives messages along with details about who sent the message.



</details>