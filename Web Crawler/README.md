<H1>Web Crawler</H1>

**The goal of this project:**
<br>Implement a web crawler that gathers data from a fake social networking website and collect 5 secret flags that have been hidden on it

**Approach:**
<br>The program runs by obtaining the Username and password from the user
<br>The IP address of the server is resolved from the hostname by the gethostbyname() function.
<br>A GET message is sent to the server with host and other details
<br>Server responds with 200-OK message with “csrftoken” and “Session-ID”
<br>Client gets the “csrftoken”,”Session-ID” from the GET message and “Username” and “Password” from the command line and sends these information in a POST message.
<br>Server responds with 302-FOUND message along with the URL to which further requests are to be sent. 
<br>Client sends a GET message to the new location with “csrftoken” and “Session-ID”.
<br>Server responds with 200-OK and sends the requested page. The retrieved page is parsed to find links and they are stored in a list(“mainlist”). The no of links found in a page are stored in a separate list(Sublist_legth)
<br>A sublist is created which accepts part of the mainlist(equal to the number of links denoted by each value of Sublist_length). It is traversed to find further links in the subsequent pages and they are stored in the “mainlist”.
<br>Each entry in the mainlist is allowed only after checking if the entry starts with ‘/fakebook/’ and if it is not already present in the list.
<br>Each page is parsed to check if there is any flag present. If yes, the flag is retrieved and stored in a separate list named “secret_flags”.
<br>Each response from the server is checked and errors are handled as below:
<pre>1. If the response is “301 MOVED PERMANENTLY”, the new location is retrieved and the request is redirected.
<br>2. If the response is “403 FORBIDDEN”, an error is thrown to the user and connection is terminated.
<br>3. If the response is “404 NOT FOUND”, an error is thrown to the user and connection is terminated.
<br>4. If the response is “500 INTERNAL SERVER ERROR”, socket is re-established and the request is sent again. </pre>

**Running the code:**
<br>python webcrawler.py [username] [password]
