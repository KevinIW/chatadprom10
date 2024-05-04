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


</details>