# Lab 2 Report

## Part 1 - Web Server

`ChatServer` is a web server that supports the following requests:
```
/add-message?s=<string>&user=<string>
```

An example of what the server can do is after the request:
```
/add-message?s=Hello&user=jpolitz
```

then the page shows:
```
jpolitz: Hello
```

Here is the code for `ChatServer`
