# Lab 2 Report

## Part 1 - Web Server

`ChatServer` is a web server that supports the following requests:
```
/add-message?s=<string>&user=<string>
```

Here is the code for `ChatServer`:

<img width="607" alt="image" src="https://github.com/katrinab2727/cse15l-lab-reports/assets/149338452/12bab86b-9082-428a-bd08-1b1e46cbe6a6">

Here is how the web server works when using `/add-message?s=Hello&user=jpolitz`:

<img width="641" alt="image" src="https://github.com/katrinab2727/cse15l-lab-reports/assets/149338452/279a1b19-720c-4a14-b5d7-20ee741b2795">

**Methods Called**
* `handleRequest(URI url)`: Takes in a URI parameter 

