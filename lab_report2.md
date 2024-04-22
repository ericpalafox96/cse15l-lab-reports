# **Lab Report #2**
***

## Part 1
***
```
import java.io.IOException;
import java.net.URI;

class ChatHandler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.

    String s = "";

    public String handleRequest(URI url) {
        String query = url.getQuery();
        if (url.getPath().equals("/")){
            return "Please input a query";
        }
        else {
            if (url.getPath().contains("/add-message")) {
                String[] queries = url.getQuery().split("=");
                
                if(queries[0].equals("s")) {
                    s += queries[2] + ": " +  queries[1].replace("&user", "") + "\n";
                }
                return String.format("%s", s);
            }   
        }
        return "404 Not Found!"; 
    }
}

class ChatServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new ChatHandler());
    }
}
```

![Q1.1](l21.1.png)

![Q1.2](l21.2.png)

## Part 2
***
![Q2.1](l22.1.png)

![Q2.2](l22.2.png)

![Q2.3](l22.3.png)

## Part 3
***
