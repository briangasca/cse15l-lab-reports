# Lab Report 2
by Brian Gasca

# Part 1
---

The webserver called `ChatServer` can take in requests and output them in a way that it would be like chatting in a chatbox.
You use the url path `/add-message?s=<string>&user=<string>` to add messages, replacing `<string>` with your own
words of choice.


**Code**
---

```Java
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // Fields
    String user; //user to be changed later
    String message; //message to be changed later
    String[][] stored = new String[100][100]; //Create 2d array with a good amount of space.
    int stored_count = 0; //keeps track of items in stored field

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
**1st Example**
---
After using the url `http://localhost:4050/add-message?s=hello!&user=bgasca`, this is what the webpage displayed:
* The method that was called was the `handleRequest` method from the `Handler` class. 
* The `main` method was also used to start the server earlier. `handleRequest` takes an argument `url` of the `URI` class,
meaning it's just taking the url as a parameter, which in this case is `http://localhost:4050/add-message?s=hello!&user=bgasca`.
* Many fields were changed:
- `path` is defined as `/add-message?s=hello!&user=bgasca`
- `user` was changed to `bgasca`, 
- `message` was changed to `hello`, 
- `stored[0][0]` was changed to reference `user`
- `stored[0][1]` was changed to reference `message`
- `stored_count` was incremented from `0` to `1`
- `return_string` changed from `""` to `"bgasca : hello\n"`
- `query` is defined as `s=hello!&user=bgasca`
- `parse` is defined as `["s","hello!&user","bgasca"]`
- `sub_parse` is defined as `["hello!,user]`
  
![add-message1](https://raw.githubusercontent.com/briangasca/cse15l-lab-reports/main/images/Screenshot%202024-01-28%20at%2010.12.00%20PM.png)

---
**2nd Example**
---
After using a different url, `http://localhost:4050/add-message?s=good evening!&user=jpolitz`, this is what the webpage displayed:
* The method that was called was the `handleRequest` method from the `Handler` class.
* The `main` method was also used to start the server earlier. Much like earlier, `handleRequest` takes an argument `url` of the `URI` class,
meaning it's just taking the url as a parameter, which in this case is `http://localhost:4050/add-message?s=good evening!&user=jpolitz`.
* Many fields were changed again:
- `path` is defined as `/add-message?s=good evening!&user=jpolitz`
- `user` was changed to `jpolitz`, 
- `message` was changed to `good evening`, 
- `stored[1][0]` was changed to reference `user`
- `stored[1][1]` was changed to reference `message`
- `stored_count` was incremented from `1` to `2`
- `return_string` changed from `"bgasca : hello\n"` to `"bgasca : hello\njpolitz : good evening\n"`
- `query` is defined as `s=good evening!&user=jpolitz`
- `parse` is defined as `["s","good evening!&user","jpolitz"]`
- `sub_parse` is defined as `["good evening!,user]`

![add-message2](https://github.com/briangasca/cse15l-lab-reports/blob/main/images/Screenshot%202024-01-28%20at%2010.12.50%20PM.png?raw=true)

## Part 2
---

**Private Key**

Using `cd`, I find the directory in where my private ssh key is located. I go to the `.ssh` file and use `ls` to see if my private key is there, and it is.
Using `pwd`, I'm able to get the absolute path in where this file is located, so the absolute path is `/Users/briangasca/.ssh/`

![private-key-location](https://github.com/briangasca/cse15l-lab-reports/blob/main/images/Screenshot%202024-01-28%20at%2010.49.54%20PM.png?raw=true)

**Public Key**

Connecting to the `ieng6` server, I `cd` into the `.ssh` directory that is located there, then `ls` to find the keys. There are two files, `authorized_keys` and
`known_hosts`. I'm pretty certain `authorized_keys` is a file containing all the keys that are authorized, however I cannot `cd` to it because it's not a directory.
Using `pwd`, I can find that the absolute path for the public ssh keys on the `ieng6` server is `/home/linux/ieng6/oce/9f/bgasca/.ssh`.

![public-key-location](https://raw.githubusercontent.com/briangasca/cse15l-lab-reports/main/images/Screenshot%202024-01-28%20at%2011.01.43%20PM.png)
![public-key-location2](https://raw.githubusercontent.com/briangasca/cse15l-lab-reports/main/images/Screenshot%202024-01-28%20at%2011.12.09%20PM.png)

**Terminal Interaction**

In this image, I am able to connect to the `ieng6` server without a password! All I have to type is `ssh bgasca@ieng6.ucsd.edu` and I am not prompted
with any password request, instead it just connects  me.

![terminal-interaction](https://raw.githubusercontent.com/briangasca/cse15l-lab-reports/main/images/Screenshot%202024-01-28%20at%2011.04.34%20PM.png)

## Part 3
---
**What I Learned**

I learned a good amount of concepts from this lab, for example it was quite a challenge for me to implement the `ChatServer` logic because I didn't know
too much about the `.split()` method that I could use to parse strings. After I learned about it more, it became easier to implement. I also learned that
`mkdir` is a command that will create a directory for you and `scp` can be used to copy files locally to remote servers. I imagine `scp` will be very useful
down the line as we interact with our `ieng6` servers more.
