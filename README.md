api = application programming interface (interface= set of rules or methods)

A customer who wants soup doesn't go into the kitchen to cook. They don't even have to know how to make soup! They only have to know how to ask the waiter for soup, expecting the waiter to bring back soup.

APIs work the same way, but there are different names for the players involved. Instead of soup, the requester might ask for data or execution of a service.  
Networking term 	            Description 	                                    Restaurant analogy
Client           	The requester. Ex: browser, web app, mobile app 	               Customer
API 	            Simplified interface for interacting with the backend 	           Waiter
Server            	The backend where the processing happens 	                      Kitchen

  Types of APIs
Medium

While this course will focus on Web APIs, it is important to know that "API" can apply to a broad range of interfaces.

    Hardware APIs
    Interface for software to talk to hardware.
    Example: How your phone's camera talks to the operating system. 

    Software Library APIs
    Interface for directly consuming code from another code base.
    Example: Using methods from a library you import into your application.

    Web APIs
    Interface for communicating across code bases over a network.
    Example: Fetching current stock prices from a finance API over the internet.

Multiple API types may be used to achieve a task. For example, uploading a photo to Instagram makes use of various APIs:

    Hardware API for the app to talk to your camera

    Software library API for the image to be processed with filters

    Web API for sending your image to Instagram's servers so your friends can like it!

 Access

APIs also vary in the scope of who can access them.

    Public APIs (aka Open APIs)
    Consumed by anyone who discovers the API

    Private APIs
    Consumed only within an organization and not made public

    Partner APIs
    Consumed between one or more organizations that have an established relationship
#tasks
This REST API allows you to CRUD (Create, Read, Update, Delete) books in a public library database
1. go to workspace in postman and choose a blank one
2. Collections are places to organize your API requests in Postman. They serve as executable documentation of API endpoints, its present in the workspace only create one
3. Request methods
When we make an HTTP call to a server, we specify a request method that indicates the type of operation we are about to perform. These are also called HTTP verbs.
Some common HTTP request methods correspond to the CRUD operations mentioned earlier. You can see a list of more methods here.
Method name 	Operation
a.GET 	Retrieve data (Read)
b.POST 	Send data (Create)
c.PUT/PATCH 	Update data (Update)
* PUT usually replaces an entire resource, whereas PATCH usually is for partial updates
d.DELETE 	Delete data (Delete)
#note: These are just conventions - it all depends on how the API is coded. To know which method to use, always read the documentation for the API you're working with!
       In addition to a request method, a request must include a request URL that indicates where to make the API call. A request URL has three parts: a protocol (such as http:// or https://), host (location of the server), and path (route on the server). In REST APIs, the          path often points to a reference entity, like "books"
  #REQUEST PARAMETERS
  1.VARIABLES:Postman allows you to save values as variables to reuse them and easily hide sensitive information like API Keys.We will use a variable to replace our base URL so that we don't have to type that repeatedly. Once a variable is defined, you can access its value                 using double curly brace syntax like this: {{variableName}}
         HOW TO DO: SELECT THE URL Dont include the / after .com ,there set as variable will come give its name and for books( scope will be collctor in present case)
               variables are avilable in the collection
                parts:1.Initial Value - the value initially set when someone forks or imports your collection. Note that if you share your collection with others, they will see this value, so don't put any secrets here!
                      2.Current Value - Postman always resolves the variable to this value. This is local to your Postman account, and not public. It is good to keep secrets like API Keys ONLY in this column and not include them in the Initial Value column.

  2.QUERY PARAMETERS: some APIs allow you to refine your request further with key-value pairs called query parameters.
               Query parameter syntax:
               Query parameters are added to the end of the path. They start with a question mark ?, followed by the key-value pairs in the format: <key>=<value>. For example, this request might fetch all photos that have landscape orientation:
               GET https://some-api.com/photos?orientation=landscape
               If there are multiple query parameters, each is separated by an ampersand &. Below two query parameters to specify the orientation and size of the photos to be returned: GET https://some-api.com/photos?orientation=landscape&size=500x400
          When to use query parameters?
               The answer is always: read the API documentation! Sometimes, query parameters are optional and allow you to add filters or extra data to your responses. Sometimes, they are required in order for the server to process your request. APIs are implemented                          differently to fulfill different needs.
          Eg: 1.duplicate the get books using the 3 dots,in the key section put genre and value fiction (single query)
              2.(Multiple query parameters): check your postman
  3.Path Variable: Another way of passing request data to an API is via path variables (a.k.a. "path parameters"). A path variable is a dynamic section of a path and is often used for IDs and entity names such as usernames.
                  At first, it is easy to confuse these two parameter types. Let's compare them side by side. 
               Path Variable 	                             --                                       Query parameters
               ex: /books/abc123 	                             --                                  ex: /books?search=borges&checkedOut=false
               Located directly after a slash in the path. It can be anywhere on the path    --	      Located only at the end of a path, right after a question mark ?
               Accepts dynamic values          	                       ---                      Accepts defined query keys with potentially dynamic values.
               * Often used for IDs or entity names 	                    ---                         * Often used for options and filters
  
          When to use path variable?

          Always read the API documentation! If a path parameter is required, the documentation will mention this.Note that some API documentation uses colon syntax to represent a wildcard in the path like /users/:username, while some use curly braces like /users/     {username}.      They both mean the same thing: that part of the path is dynamic!
  *3*. According to the API documentation, we can get a specific book by hitting the path GET /books/:id, where we replace :id with the book's id.
       a.Make sure the request method is set to GET, and paste in this endpoint as the request URL: {{baseUrl}}/books/:id
              Postman automatically adds a "Path Variables" editor in the Params tab of the request for any path variables in the request URL prefixed with a colon :
              #note:  A common error is adding accidental white space in your query or path parameter values.

  #Sending data with POST
  1.
