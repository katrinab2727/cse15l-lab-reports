# Lab 2 Report

## Part 1 - Web Server

`ChatServer` is a web server that supports the following requests:
```
/add-message?s=<string>&user=<string>
```

Here is the code for `ChatServer`:

<img width="607" alt="image" src="https://github.com/katrinab2727/cse15l-lab-reports/assets/149338452/12bab86b-9082-428a-bd08-1b1e46cbe6a6">

<br>

Here is what the web server shows when using `/add-message?s=Hello&user=jpolitz`:

<img width="653" alt="image" src="https://github.com/katrinab2727/cse15l-lab-reports/assets/149338452/301d19b4-619f-43fd-91d9-23d5097879e3">


**Methods Called**
* `handleRequest(URI url)`: Takes in a URI parameter where the path and query are located
* `url.getQuery()`: Retrieves the query from the url, which is the part of the url after the `?`
* `url.getPath()`: Retrieves the path from the url
* `url.getPath().contains("/add-message")`: Checks if the path retrieved from the url contains "/add-message" that is needed for the server to function properly
* `query.substring(2, query.indexOf("&"))`: Retrieves the `String` from index 2 to the index of "&" in the query, representing the message to be shown in the chat
* `query.substring(query.indexOf("&") + 6, query.length)`: Retrieves the `String` from the index of "&" + 6 to get rid of the user part of the query to get the username to be shown in the chat
* `String.format(list)`: Returns the formatted `String`, which in this case, returns `list` as is that contains all the chats and users in the web server
* `Integer.parseInt(args[0])`: Used to turn the input from the terminal that represents the port number to an `Integer`
* `Server.start(port, new Handler())`: Used to start the server by using the given port number while creating a new `Handler` object for the server

**Values**
* `int port = 4000` 
* `URI url = https://0-0-0-0-4000-j272bidijnptkom0kott8e0i5s.us.edusercontent.com/add-message?s=Hello&user=jpolitz`
* `String user = "jpolitz"`
* `String message = "Hello"`
* `String query = "s=Hello&user=jpolitz"`
* `String list = "jpolitz: Hello\n"`

Before this request was run, the value of port was `null` and the `Strings` were empty. These values were all changed once the request was made.
<br>

Here is what the web server shows when using `/add-message?s=Hey&user=kbosler`:
<img width="634" alt="image" src="https://github.com/katrinab2727/cse15l-lab-reports/assets/149338452/ba957602-713a-4357-ad87-dcf127469dad">


**Methods Called**
* `handleRequest(URI url)`: Takes in a URI parameter where the path and query are located
* `url.getQuery()`: Retrieves the query from the url, which is the part of the url after the `?`
* `url.getPath()`: Retrieves the path from the url
* `url.getPath().contains("/add-message")`: Checks if the path retrieved from the url contains "/add-message" that is needed for the server to function properly
* `query.substring(2, query.indexOf("&"))`: Retrieves the `String` from index 2 to the index of "&" in the query, representing the message to be shown in the chat
* `query.substring(query.indexOf("&") + 6, query.length)`: Retrieves the `String` from the index of "&" + 6 to get rid of the user part of the query to get the username to be shown in the chat
* `String.format(list)`: Returns the formatted `String`, which in this case, returns `list` as is that contains all the chats and users in the web server

**Values**
* `int port 4000` (same port)
* `URI url = https://0-0-0-0-4000-j272bidijnptkom0kott8e0i5s.us.edusercontent.com/add-message?s=Hey&user=kbosler`
* `String user = "kbosler"`
* `String message = "Hey"`
* `String query = "s=Hey&user=kbosler"`
* `String list = "jpolitz: Hello\nkbosler: Hey\n"`

Before this request was made, the values of the fields were what they were before as stated above.

## Part 2 - SSH
**Absolute Path to my Private Key**

<img width="388" alt="image" src="https://github.com/katrinab2727/cse15l-lab-reports/assets/149338452/b5f94be3-75d8-41db-8b4d-0be04cef7664">
<br>
<img width="236" alt="image" src="https://github.com/katrinab2727/cse15l-lab-reports/assets/149338452/fbcbb017-0d75-4031-90b1-f77dbf79a864">

The `/c/Users/katri/.ssh` directory contains `id_ed25519` (private key), `id_ed25519.pub`, and `known_hosts` on my local computer.

<br>

**Absolute Path to my Public key for my SSH key for logging into ieng6**

<img width="272" alt="image" src="https://github.com/katrinab2727/cse15l-lab-reports/assets/149338452/240006ae-df0e-4944-bb15-c307ffe5fed2">

`/home/linux/ieng6/oce/95/kbosler/.ssh` is the path that contains `authorized_keys`(where the copy of my public key is located), `id_rsa`, and `id_rsa.pub` that allows me to log into my `ieng6`.

<br>

<img width="480" alt="image" src="https://github.com/katrinab2727/cse15l-lab-reports/assets/149338452/912c3b65-2168-48b5-8d58-386bb06dbdf5">
<br>
Here is the code using `scp` to copy my public key to the `ieng6` account

<br>

<br>

**Logging into my `ieng6` account without being asked for a password**
<br>
<img width="439" alt="image" src="https://github.com/katrinab2727/cse15l-lab-reports/assets/149338452/a9d74b63-b826-4080-8338-585279967541">

## Part 3 - Reflection
I have learned a lot about building and running a server from the last couple of labs. I learned about certain methods such as `getQuery()` and `getPath()` and how to use them to create a web server. Also, it was nice to be able to make a key and not have to keep using a password to log into `ieng6` remotely by creating a public and private key. Learning the commands `scp` and `mkdir` is useful as I have seen in lab.

