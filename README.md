## HTTP Questions

__URLs__

* Name all of the parts of the url that you can remember.  In your own words describe what they do.
* Name the pieces of the following urls
	* `https://www.google.com/`

		- http is the protocol; www.google.com is the domain name

	* `https://workbook.galvanize.com/cohorts/41/learning_experiences/367`

			- subdomain is workbook, followed by domain name, followed by nested file paths

	* `http://locahost:5000/animals/puppies?onlycute=1&size=medium#firstpuppy`

			- This is a local server, with a relative file path that also contains a query string (after the question mark) that contains key value pairs that are found with a GET request from the back end (using a back-end framework like Node.js or Express.js). For example onlycute is a key and the value is 1 (presumably 'true'), while size and medium are the same. Query k/v pairs are separated by ampersands. After, anything following the hashtag: #SomewhereInTheDocument is an anchor to another part of the resource itself. An anchor represents a sort of "bookmark" inside the resource, giving the browser the directions to show the content located at that "bookmarked" spot. On an HTML document, for example, the browser will scroll to the point where the anchor is defined; on a video or audio document, the browser will try to go to the time the anchor represents. It is worth noting that the part after the #, also known as fragment identifier, is never sent to the server with the request.

	* `https://en.wikipedia.org/wiki/List_of_HTTP_status_codes#4xx_Client_Error`

			- Here, I am assuming the en is the type of language used for the website (en = english). This is also the subdomain. That means everything I get back will be in English. This is followed by the domain name, and file paths, as well as an anchor tag for status codes.

* Can a server use more than 1 port?

Yes, it can.

* Why is https different than http?

- Hyper Text Transfer Protocol Secure (HTTPS) is the secure version of HTTP, the protocol over which data is sent between your browser and the website that you are connected to. The 'S' at the end of HTTPS stands for 'Secure'. It means all communications between your browser and the website are encrypted.

Using HTTPS, the computers agree on a "code" between them, and then they scramble the messages using that "code" so that no one in between can read them. This keeps your information safe from hackers.

They use the "code" on a Secure Sockets Layer (SSL), sometimes called Transport Layer Security (TLS) to send the information back and forth.

* How does a server interpret the following url's query paramter.  What data structure does it create on the server?

```
http://locahost:5000/animals?puppies=fido&puppies=max&puppies=moxie
```

	 - Somewhere in the animals page, there is are search parameters for puppie names.
	 This creates, in the server, an object of animals, with puppies as the keys and their
	 (presumably) names as the values.

__HTTP Request/Response__

* Name at least 4 http verbs
  - get, put, post, patch, delete.

* What is each verb useful for in your own words
  - get: get information from a database (when a user enters a search query for example)
  - post: Submits data to be processed to a specified resource
  - put: uploads a representation of a specified URI
  - delete: deletes a specified resource
  - patch: can be used to updated a partial resource

* What does idempotent mean?
  - Idempotence is a funky word that often hooks people. Idempotence is sometimes a confusing concept, at least from the academic definition.

  From a RESTful service standpoint, for an operation (or service call) to be idempotent, clients can make that same call repeatedly while producing the same result. In other words, making multiple identical requests has the same effect as making a single request. Note that while idempotent operations produce the same result on the server (no side effects), the response itself may not be the same (e.g. a resource's state may change between requests).

  The PUT and DELETE methods are defined to be idempotent. However, there is a caveat on DELETE. The problem with DELETE, which if successful would normally return a 200 (OK) or 204 (No Content), will often return a 404 (Not Found) on subsequent calls, unless the service is configured to "mark" resources for deletion without actually deleting them. However, when the service actually deletes the resource, the next call will not find the resource to delete it and return a 404. However, the state on the server is the same after each DELETE call, but the response is different.

  GET, HEAD, OPTIONS and TRACE methods are defined as safe, meaning they are only intended for retrieving data. This makes them idempotent as well since multiple, identical requests will behave the same.

* Name the 5 http status code ranges.  What are they used for in general?
  - 1 1xx Informational.
  - 2 2xx Success.
  - 3 3xx Redirection.
  - 4 4xx Client Error.
  - 5 5xx Server Error.

* If a server returns a http status code of 301 and a location of `https://www.google.com/`, what does the browser do?
  - The HTTP response status code 301 Moved Permanently is used for permanent URL redirection,
    meaning current links or records using the URL that the response is received for should be updated. The new URL should be provided in the Location field included with the response.

* For the following HTTP headers, decide if the following header is used for requests, responses or both:
	* Accept
    - For requests;
    - The Accept request-header field can be used to specify certain media types which are acceptable for the response. Accept headers can be used to indicate that the request is specifically limited to a small set of desired types, as in the case of a request for an in-line image.
	* Content-type
    - For responses;
    - The Content-Type entity-header field indicates the media type of the entity-body sent to the recipient or, in the case of the HEAD method, the media type that would have been sent had the request been a GET.
	* User-agent
    - For requests;
    - The User-Agent appears in an HTTP Request Header, not an HTTP Response one. In general, the request is sent from browser to the web application. So the user-agent variable is filled by the browser. Different browsers will fill up this field with different values.
	* Set-cookies
    - For responses;
    - The Set-Cookie header is sent by the server in response to an HTTP request, which is used to create a cookie on the user's system. The Cookie header is included by the client application with an HTTP request sent to a server, if there is a cookie that has a matching domain and path.
	* Cache-control
    - For requests and responses;
    - The Cache-Control general-header field is used to specify directives for caching mechanisms in both, requests and responses. Caching directives are unidirectional, meaning that a given directive in a request is not implying that the same directive is to be given in the response.
	* Cookie
    - For requests;
    - An HTTP cookie (web cookie, browser cookie) is a small piece of data that a server sends to the user's web browser, that may store it and send it back together with the next request to the same server. Typically. it is used to know if two requests came from the same browser allowing to keep a user logged-in, for example. It remembers stateful information for the stateless HTTP protocol.

* Is the following a http request or response?  How do you know for each?

  - response, because the server replied with a 200 'ok' status code;
```
HTTP/1.1 200 OK
Access-Control-Allow-Origin: *
Vary: Accept
Content-Type: text/html; charset=utf-8
Content-Length: 722
ETag: W/"2d2-Wu0We9N5g35FXWY+gOATLA"
Date: Tue, 08 Mar 2016 20:37:11 GMT
Connection: keep-alive

<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <link rel="stylesheet" href="/style.css">
    <title>Student Roster</title>
  </head>
  <body>
    <main>
      <h1>Student Roster</h1>

        <section>
          <h3>Daenerys Targaryen</h3>
          <span>Student Id: nys8fbohl</span>
          <h4>Hobby: Motherhood</h4>
          <img src="https://i.imgur.com/KlycRG5.jpg" alt="Daenerys Targaryen" />
        </section>

        <section>
          <h3>Tyrion Lannister</h3>
          <span>Student Id: njehukbohe</span>
          <h4>Hobby: Traveling</h4>
          <img src="https://i.imgur.com/fFMusdC.png" alt="Tyrion Lannister" />
        </section>

    </main>
  </body>
</html>
```

```
DELETE /students/n1vmyrw3x HTTP/1.1
Host: g22-students.herokuapp.com
Accept: application/json
Cache-Control: no-cache
Postman-Token: 0041e3c3-efdb-f0c3-b2f4-2d79f6d0f44b
```

__JSON__

* Describe what JSON is.  What is it used for.
  - JSON stands for javascript object notation. It is a 'lightweight' method of
    storing and reading through information. It is easily accessible and very
    readable.
* Convert the following map into a javascript object then console log the age.

var map = {
	"company" : "Github",
	"age": 7,
	"categories" : "Services,Internet,Software"
};

function mapToObject(obj) {
        var newObj = {};
        for (var key in obj) {
          if(obj.hasOwnProperty(key)){
    		newObj[key] = obj[key]
        }
      }
      	console.log(obj.age)
        return obj;
    }

```
{ "company" : "Github", "age": 7, "categories" : "Services,Internet,Software"}
```
* Convert the following to a javascript object.  Console log each company name.
var data = {
	"Companies":
	[
		{"company": "Github", "age": 7, "categories": "Services,Internet,Software"},
        {"company": "Airbnb", "age": 6, "categories": "Hotels,Travel"},
        {"company": "Square", "age": 7, "categories": "FinTech,Hardware + Software,Finance"},
        {"company": "Dropbox", "age": 11, "categories": "Cloud Data Services,Storage,Web"}
    ]
}

data.Companies.forEach(function(company) {
 console.log(company['company']);
});

```
{ "Companies":[ { "company": "Github", "age": 7, "categories": "Services,Internet,Software"},
              { "company": "Airbnb", "age": 6, "categories": "Hotels,Travel"},
              { "company": "Square", "age": 7, "categories": "FinTech,Hardware + Software,Finance"},
              { "company": "Dropbox", "age": 11, "categories": "Cloud Data Services,Storage,Web Hosting"}
            ]
}
```
* The following is javascript.  Convert the object to a string and console log it.

- JSON.stringify(myObj)

```
var myObj = {
  company: "Galvanize",
  age: 3,
  categories: "Education"
};
```
__MISC__

* Describe what DNS is.
  - Domain Name Servers (DNS) are the Internet's equivalent of a phone book. They maintain a directory of domain names and translate them to Internet Protocol (IP) addresses. This is necessary because, although domain names are easy for people to remember, computers or machines, access websites based on IP addresses.

* In the terminal, type `man curl`.  Look at the man page for curl.  What do the following flags do? `-v`, `-X`.  (Hint: to search for a string, type `/` then the text you want, then enter.  To quit the man page, type `q`).
  - v = verbose: Be  more  verbose/talkative  during  the  operation.  Useful for
              debugging and seeing what's going on "under the  hood".  A  line
              starting  with  '>'  means "header data" sent by curl, '<' means
              "header data" received by curl that is hidden in  normal  cases,
              and  a  line starting with * means additional info provided by
              curl.
  -  --request <command>
              (HTTP) Specifies a custom request method to use when communicat-
              ing  with the HTTP server.  The specified request method will be
              used instead of the method otherwise  used  (which  defaults  to
              GET).  Read  the HTTP 1.1 specification for details and explana-
              tions. Common additional HTTP requests include PUT  and  DELETE,
              but related technologies like WebDAV offers PROPFIND, COPY, MOVE
              and more.
              Normally you don't need this option. All  sorts  of  GET,  HEAD,
              POST and PUT requests are rather invoked by using dedicated com-
              mand line options.

              This option only changes  the  actual  word  used  in  the  HTTP
              request,  it does not alter the way curl behaves. So for example
              if you want to make a proper HEAD request, using  -X  HEAD  will
              not suffice. You need to use the -I, --head option.

              The method string you set with -X will be used for all requests,
              which if you for example use -L, --location may cause unintended
              side-effects  when  curl doesn't change request method according
              to the HTTP 30x response codes - and similar.

* What is TCP/IP?  How does it interact with HTTP?

  - TCP/IP, Transmission Control Protocol/Internet Protocol, is a suite of communications protocols used to interconnect network devices on the Internet. TCP/IP implements layers of protocol stacks, and each layer provides a well-defined network services to the upper layer protocol.

  - TCP also has layers. The application layer sends and receives data from HTTP, while the Transport layer provides security for HTTP

* Does HTTP break the data that is being sent into small packets?  If not, what protocol is responsible for it?

  - No, the TCP, or Transmission Control Protocol is responsible for that.
