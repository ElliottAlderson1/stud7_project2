**How to-Steps**
Build virtual environment (``python3 -m venv <name of venv>``), ``cd`` into it and activate it (``source bin/activate``). Once in there make sure the virtual environment is using the latest version of PIP: `pip install --upgrade pip`. 

The install the request package into the VE: `pip install requests`

Create a new script where the API call will be generated.

- Process to start using the requests library for python it can be installed using ``$python -m pip install requests``, use the library in code using the ``import requests``
- You can also use URLLIB3 which simplifies interacting with web services. Install using ``pip install urllib3``, use the library in code using the ``import urllib3``

- When building an API in a script it must have the following components (each of these will be their own variables):
     - Method
     - URL
     - Headers
     - Parameters
     - Body

- Example structure listed below:
```python
METHOD = 'GET'
API_URL = 'https://api.github.com/search/repositories'
HEADERS = {
        'Accept': 'application/json',
        'Content-Type': 'application/json'
}
PARAMETERS = {
        'q': 'language:python'
}
```
- Generate your constants first which will be METHOD, API_URL and header. Call upon the function using the ``requests.request()`` method.
     - EX: ``<request variable> = requests.request(method=METHOD, url=API_URL, headers=HEADERS, verify=False)`` (The ``verify=False`` bypasses untrusted SSL certificates, will be fixed below)
     - If using parameters will read like ``variable = requests.request(method=METHOD, url=API_URL, headers=HEADERS, verify=False, params=PARAMETERS)``
     - Use the ``urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)`` command to disable untrusted HTTP error in regards to untrusted SSL certs
- To run your script interactively use ``python3 -i <script name>``
- Something of note:
```
The status code of an HTTP response simply indicates whether or not the request was successful.  
Status codes consist of three digits, where the first digit indicates the overall category of the status, and the last two digits specify exactly what happened.  
For example, the 2XX series of codes are all defined as being "successful", all 3XX status codes are redirects, and all 4XX status codes are client errors.
```
- To get the returned status code of the script when ran use ``print(<request variable>.status_code)``
- To see all of the attributes returned by the script use the example below:
```python
for att in dir(request variable):
...    print(att) <- (This is an interactive prompt, be sure to tab otherwise will return error)
```
- Important aspects to look at when returning code are below (use the name as a parameter such as ``<request variable.cookies`` or ``<request variable.headers``:
     - status_code
     - cookies 
     - encoding 
     - headers 
     - json
     - text
     - request
- To clean up output of JSON print you can use the example command:
     - ``print(json.dumps(<request variable>.json(), indent=4))``
     - Can use the ``<request variable>.text`` as an alternative
- Something to note:
```
Even though the HTTP response object contained JSON data, when we use the .json() method, it returns that JSON data formatted with Python conventions, like single quotes instead of double quotes. 
Also, JSON uses null for empty values, but these would be converted to None in Python.
```
- You print certain aspects of the result using the example below:
     - `'<request variable>.request.headers`` for header information
     - `'<request variable>.request.method`` for method information
     - `'<request variable>.request.url`` for URL information
- Break out information in the following process:
     - Create a list of the keys in the json file, example ``variable = <request variable>.json()``
     - You can then set variables to access certain indexes in that list
- When adding parameters can sort and filter amount of content, example below:
```python
PARAMETERS = {
        'q': 'language:python',
        'sort': 'stars',
        'per_page': 1,
        'order': 'asc',
}
```