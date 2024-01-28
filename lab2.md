# Lab 2 Report

## Part 1 - Web Server

`ChatServer` is a web server that supports the following requests:
```
/add-message?s=<string>&user=<string>
```

Here is the code for `ChatServer`:

<img width="607" alt="image" src="https://github.com/katrinab2727/cse15l-lab-reports/assets/149338452/12bab86b-9082-428a-bd08-1b1e46cbe6a6">

<br>

Here is how the web server works when using `/add-message?s=Hello&user=jpolitz`:

<img width="641" alt="image" src="https://github.com/katrinab2727/cse15l-lab-reports/assets/149338452/279a1b19-720c-4a14-b5d7-20ee741b2795">

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

<br>

Here is how the web server works when using `/add-message?s=Hey&user=kbosler`:
<img width="596" alt="image" src="https://github.com/katrinab2727/cse15l-lab-reports/assets/149338452/94d19f80-d55c-4267-ad05-e697f56117c5">
