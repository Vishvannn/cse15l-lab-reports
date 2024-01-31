# CSE 15L Lab 2

## Part 1 

### ChatServer.java


```
import java.io.IOException;
import java.net.URI;

class ChatHandler implements URLHandler {
    String chatMessages = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/add-message")) {
            String queryString = url.getQuery();
            String[] parameters = queryString.split("&");
            String message = null;
            String user = null;

            for (String param : parameters) {
                String[] parts = param.split("=");
                if (parts.length == 2) {
                    if (parts[0].equals("s")) {
                        message = parts[1];
                    } else if (parts[0].equals("user")) {
                        user = parts[1];
                    }
                }
            }

            if (message != null && user != null) {
                String chatMessage = user + ": " + message + "\n";
                chatMessages += chatMessage;
            }

            return chatMessages;
        } else {
            return "404 Not Found!";
        }
    }
    public class ChatServer {
    public static void main(String[] args) throws IOException {
        if (args.length == 0) {
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new ChatHandler());
    }

```

----
![image](https://github.com/Vishvannn/cse15l-lab-reports/assets/156368779/0c8ff130-5b56-49df-a0c8-cee2eab9aa09)

handleRequest(URI url) gets called when the server gets a request to add a message.

The method picks up the message "How are you" and the user "yash" from the URL.

The chatMessages field is updated with the new chat line, so it now includes the new message from "yash".

![image](https://github.com/Vishvannn/cse15l-lab-reports/assets/156368779/2c7c3263-d697-4b3d-a35d-9b936bc67379)

The handleRequest method is called again because there's a new web request to /add-message.

The method processes the message "I%20am%20good" from the user "jpolitz" from the URL's query parameters.

The chatMessages field gets another line added, which is "jpolitz: I am good\n". After this request, chatMessages includes three chat entries, showing a back-and-forth conversation.

----

## Part 2 - SSH

![image](https://github.com/Vishvannn/cse15l-lab-reports/assets/156368779/51d22fe2-d632-4251-8f8e-3d1c1715d29c)

> The absolute path to the private key for my SSH key for logging into ieng6 on my computer is: C:\Users\vishi\.ssh\id_rsa


![image](https://github.com/Vishvannn/cse15l-lab-reports/assets/156368779/a8527fc0-8dd8-4781-935c-fac814b575d6)

> The absolute path to the public key for my SSH key for logging into ieng6 on ieng6 is: /home/linux/ieng6/oce/7b/vsivanandan/.ssh/authorized_keys

![image](https://github.com/Vishvannn/cse15l-lab-reports/assets/156368779/25f21939-6f6d-43a6-91c9-c6d6c690a585)

> Above is a terminal interaction where I log into my ieng6 account without being asked for a password.

----

## Part 3 

I learned how to make a local or remote server.
I also learned 2 new terminal commands in mkdir and scp
I also learned that you can create a known host so you wont require a password when logging in



















