**Procedures/Commands**

- Create a basic API call
     1. Create an empty request
     2. Configure the request method
     3. Configure the URL: https://api.coinbase.com/v2/currencies #EXAMPLE
     4. Configure the HTTP headers (Baseline)
          - Accept = application/json
          - Content_type = application/json
     5. Execute the API call
**Components**:

- Towards the top, you'll see the method selection dropdown and URL bar. The default method selected is ``GET``
- Below these two options, you'll see a few tabs that you can click on:
  - **Query**: This tab is used to configure parameters, or filters, for your API call.
  - **Headers**: This tab is where you'd configure any custom HTTP headers you'd like to use. Think of HTTP headers as custom configuration options that you can add to an HTTP request.
  - **Authentication**: This tab, like it sounds, is where you'd configure certain authentication methods.
  - **Body**: This tab is used to specify any data that you'd like to send in your API call. This is typically only required when using methods that actually change the data on the remote API endpoint, e.g., `POST`, `PATCH`, and `DELETE`.
* Lastly, on the right half of the pane, you'll see the area where API call results will populate. This pane will show you the raw data returned from an API call as well as the components of the HTTP response itself, such as the status code, headers, and cookies.