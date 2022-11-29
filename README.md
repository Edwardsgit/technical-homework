# technical-homework

JavaScript XHR
The XMLHttpRequest object, or XHR, is a JavaScript API that allows us to transfer data between a client and a server. This makes it possible to request and receive web page updates without refreshing, leading to an improved experience for users. In this lesson, we will be exploring the use of XHR by using it to access GitHub.

Objectives
1 Explain how XHR helps us write dynamic programs
2 Practice initializing an XHR request
3 Practice handling an XHR response
4 Understand how JavaScript fetches data from remote resources

XMLHttpRequest


XMLHttpRequest was named at a time when XML was all the rage, but it can be used with any type of data, including JSON, which is the current de facto standard.

Definition: JSON stands for JavaScript Object Notation. Browsers and servers are only able pass strings of text to each other. By using JavaScript Object Notation, we can structure this text in a way that a browser or server can read as a regular JavaScript object.

XHR helps us write dynamic programs by allowing us to fetch data from a server based on user events, and update parts of pages without requiring a full-page refresh. This provides users with a smooth, engaging experience that doesn't require them to stop what they're doing to get new information.

Creating the XHR Request
The first thing we want to do is get a list of our public repositories. A little research on the Github List Repositories API tells us we can request a user's public repositories via a GET request to https://api.github.com/users/:username/repos, so let's try it out.

Top-tip: API documentation will often use a colon to precede a dynamic value in a RESTful URL, like :username. That's your hint to supply your own value.

 Parsing the XHR Response

Since the Github API deals strictly in JSON, we know that our response will be well-formed JSON, so it should be easy for us to work with.

Let's parse this response and list out the repositories on the page. We'll start by giving ourselves a place in the DOM to put the data.

 const xhttp = new XMLHttpRequest();
  xhttp.onload = function() {
 
   console.log(this.responseText);

  }
  xhttp.open("GET", "https://api.github.com/users/changetocoding");
  xhttp.send();



The key lies in the responseText property. We can look at it and understand that it's JSON, but to our JavaScript interpreter, it's just a string of text. And while we know that all JSON is just a string of text, we have to tell JavaScript that it's working with JSON.

The way we tell the interpreter that we're working with JSON is to parse it with JSON.parse.

 const xhttp = new XMLHttpRequest();
  xhttp.onload = function() {
 
   console.log(JSON.parse(this.responseText));

  }
  xhttp.open("GET", "https://api.github.com/users/changetocoding");
  xhttp.send();
