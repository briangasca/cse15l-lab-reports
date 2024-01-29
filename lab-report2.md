# Lab Report 2
by Brian Gasca

# Part 1
---

> The webserver called `ChatServer` can take in requests and output them in a way that it would be like chatting in a chatbox.
> You use the url path `/add-message?s=<string>&user=<string>` to add messages, replacing `<string>` with your own
> words of choice.
>
**Code**
---
```Java
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // Instance variables
    String user;
    String message;
    String[][] stored = new String[100][100];
    int stored_count = 0;

    public String handleRequest(URI url) {
        String path = url.getPath();

        if(path.equals("/")){
            return "Home"; //default path
        } else if (path.equals("/add-message")){
            String query = url.getQuery();
            String[] parse = query.split("="); //Separate strings where "=" was between them.
            if(parse[0].equals("s")){
                String[] sub_parse = parse[1].split("&"); //Split again where "&" was between them.
                message = sub_parse[0]; //This was to get the message string ^

                user = parse[2]; // User parse was already good to go, so just set it here.
                stored[stored_count][0] = user; // Store values in a 2d array.
                stored[stored_count][1] = message;
                stored_count++; //Increment how much we have stored
                String return_string = "";
                for(int i = 0; i < stored_count; i++){ //Loop through to display all the messages that have been sent.
                    return_string += String.format("%s : %s\n", stored[i][0],stored[i][1]);
                }

                return return_string; //Display
            }

        }
        return "Invalid argument";
    }
}
//Server Startup
class ChatServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```

**Using `add-message`**
---
