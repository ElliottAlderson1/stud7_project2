- HTTP request is made up of four parts (see below for examples):
     1. ``GET`` is the HTTP method type
     2. ``/cars`` is the API endpoint
     3. ``HTTP/1.1`` is the HTTP version
     4. ``api.example.com`` is the API host
- Below are return responses that can occur:
     - ``HTTP 200 OK`` means the request has been fulfilled and resulted in a new resource being created
     - ``HTTP 202 Accepted`` means the request has been accepted for processing but has not been completed
     - ``HTTP 204 No Content`` means the server has fulfilled the request but does not return an entity-body and might want to return updated meta-information
- The following request methods are available:
```
Version 1.0
GET
POST
HEAD
Version 1.1
PUT
DELETE
OPTIONS
TRACE
PATCH
CONNECT
```
![http_methods](uploads/9323e7f8ea4e523ddb1d67caf33b5df0/http_methods.png)
- **GET**: The GET method requests a representation of the specified resource. Requests using GET should only retrieve data.
     - GET request is used to read/retrieve data from a web server. GET returns an HTTP status code of 200 (OK) if the data is successfully retrieved from the server.
- **POST**: POST request is used to send data (file, form data, etc.) to the server. On successful creation, it returns an HTTP status code of 201.
The POST method submits an entity to the specified resource, often causing a change in state or side effects on the server.
     - The data sent to the server is typically in the following form:
          - Input fields from online forms.
          - XML or JSON data.
          - Text data from query parameters.
- **HEAD**:  The HEAD method asks for a response identical to a GET request, but without the response body. The HTTP HEAD method simply returns metadata about a resource on the server. This HTTP request method returns all of the headers associated with a resource at a given URL, but does not actually return the resource.
     - The HTTP HEAD method is commonly used to check the following conditions:
          - The size of a resource on the server.
          - If a resource exists on the server or not.
          - The last-modified date of a resource.
          - Validity of a cached resource on the server.
- **PUT**: The PUT method replaces all current representations of the target resource with the request. A PUT request is used to modify the data on the server. It replaces the entire content at a particular location with data that is passed in the body payload. If there are no resources that match the request, it will generate one.
payload.
     - The HTTP PUT request method includes two rules:
          - A PUT operation always includes a payload that describes a completely new resource definition to be saved by the server.
          - The PUT operation uses the exact URL of the target resource.
          - If a resource exists at the URL provided by a PUT operation, the resource’s representation is completely replaced. If a resource does not exist at that URL, a new resource is created.
- **DELETE**: The DELETE method deletes the specified resource. A DELETE request is used to delete the data on the server at a specified location. The HTTP DELETE method is self-explanatory. After execution, the resource a DELETE operation points to is removed from the server. As with PUT operations, the HTTP DELETE method is idempotent and unsafe.
- **OPTIONS**: The CONNECT method establishes a tunnel to the server identified by the target resource. The server does not have to support every HTTP method for every resource it manages. Some resources support the PUT and POST operations. Other resources only support GET operations. The HTTP OPTIONS method returns a listing of which HTTP methods are supported and allowed.
- **TRACE**: The TRACE method performs a message loop-back test along the path to the target resource. The TRACE HTTP method is used for diagnostics, debugging and troubleshooting. It simply returns a diagnostic trace that logs data from the request-response cycle. The content of a trace is often just an echo back from the server of the various request headers that the client sent.
- **PATCH**: The PATCH method applies partial modifications to a resource. Sometimes object representations get very large. The requirement for a PUT operation to always send a complete resource representation to the server is wasteful if only a small change is needed to a large resource. The PATH HTTP method, added to the Hypertext Transfer Protocol independently as part of RFC 5789, allows for updates of existing resources. It is significantly more efficient, for example, to send a small payload rather than a complete resource representation to the server.
- **CONNECT**: The CONNECT method establishes a tunnel to the server identified by the target resource. The connect operation is used to create a connection with a server-side resource. The most common target of the HTTP method CONNECT is a proxy server, which a client must access to tunnel out of the local network. RESTful API designers rarely interact with the CONNECT HTTP request method.
- **Idempotent**: An HTTP method is idempotent if the intended effect on the server of making a single request is the same as the effect of making several identical requests. All safe methods are idempotent, as well as PUT and DELETE. To be idempotent, only the state of the server is considered.
- **Safe (HTTP Methods)**: An HTTP method is safe if it doesn't alter the state of the server. In other words, a method is safe if it leads to a read-only operation. Several common HTTP methods are safe: GET, HEAD, or OPTIONS. All safe methods are also idempotent, but not all idempotent methods are safe. For example, PUT and DELETE are both idempotent but unsafe. Safe methods don't need to serve static files only; a server can generate an answer to a safe method on-the-fly, as long as the generating script guarantees safety: it should not trigger external effects, like triggering an order in an e-commerce Website.
