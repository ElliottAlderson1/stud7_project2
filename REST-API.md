***Common headers for RESTful architecture:***
- **Accept**: This header is used to specify the media types that the client can accept in the response. If the server cannot provide a response in one of the specified media types, it will return an error.
- **Content-Type**: The Content-Type header can be used to specify the media type of the data being sent in the request or response. This allows the client and server to agree on the format of the data being exchanged.
- **Authorization**: The Authorization header can be used to provide authentication information, such as an access token, to the server. This allows the server to verify that the client is authorized to access the requested resource.
- **Cache-Control**: The Cache-Control header can be used to specify caching behavior for the response. This allows the client and server to agree on how long the response should be cached and whether it can be cached at all
- If-None-Match: The If-None-Match header can be used to perform conditional requests. This allows the client to include an entity tag in the request, and the server will only return a response if the entity tag has changed since the last request
- User-Agent: This header is used to identify the client making the request, such as the browser or operating system being used.
- X-Requested-With: This header is used to indicate that a request was made using Ajax. It is often used by server-side frameworks to differentiate between traditional HTTP requests and Ajax requests.
- **Custom headers**: Custom headers can be used to provide additional information that is specific to the application or API being developed. For example, a custom X-Forwarded-For header can be used to indicate the IP address of the original client when requests are proxied through a load balancer.
- **Location**: This header is used in a 201 (Created) response to indicate the URL of the newly created resource.

- Query parameters pass information to an API and are added at the end of an endpoint URL, example: 
     - ``https://www.example.com/api/items?sort=asc&category=books``

- Common authentication methods for RESTful APIs include: 
     - Basic Auth
          - In this method, the user’s credentials (username and password) are sent in the header of the HTTP request in plain text, usually in the form of a Base64-encoded string. This method is not very secure and should only be used with HTTPS.
     - Oauth
          - It works by the user authorizing the third-party application to access their resources using an access token that is issued by the server.
     - JSON Web Tokens  (JWT)
          - This method involves the server generating a token (such as a JWT) after the user has authenticated. The token is then sent to the client, who includes it in the header of subsequent requests. The server then validates the token to ensure that the user is authorized to access the requested resources.

- Typical authentication steps:
     - Choose an authentication mechanism that is appropriate for your use case, such as Basic Authentication, Token-Based Authentication, OAuth2, or OpenID Connect.
     - Implement the authentication mechanism on the server-side. This typically involves setting up user accounts, generating tokens or credentials, and providing an API for clients to authenticate themselves.
     - Generate the appropriate headers on the client-side based on the authentication mechanism you are using. For example, if you are using Basic Authentication, you need to base64 encode the username and password and set the “Authorization” header to the resulting value. If you are using Token-Based 
Authentication, you need to generate a token and set the “Authorization” header to the token.
     - Include any additional headers required by your authentication mechanism. For example, OAuth2 requires a “Bearer” token prefix in the “Authorization” header.

- Error Handling:
     - ``Client Error 4xx`` means User sends a POST request but includes an unsupported media type
     - ``Server Error 5xx`` means the server, while acting as a gateway or proxy, received an invalid response from an inbound server

![restful_url](uploads/0ceb752e02cc0eca863fa392dd9325eb/restful_url.png)

- REST is set of constraints, RESTful is an API adhering to them:
![restful](uploads/54b27091a968a296b8d879077a6ea002/restful.png)
