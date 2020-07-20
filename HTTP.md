# HTTP

### Codes:

- 100: Info
- 200: Success
    - 200: Ok
    - 201: Created
    - 202: Accepted
    - 204: No Content
- 300: Redirect
    - 301: Moved Permanently
    - 302: Moved Temporarily
    - 304: Not Modified (document not updated since "If-Modified-Since" date. use the cached version on the browser instead)
- 400: Client Error
    - 400: Bad Request
    - 401: Authorization Error
    - 402: Payment required
    - 403: Forbidden (Authorization)
    - 404: Not found
- 500: Server Error
    - 501: Not implemented

### Headers:

- Request Headers:
    - User-Agent: specifies the type of client
    - Accept-Language: Language of the user
    - If-Modified-Since: return new version if changed since otherwise use cached
    - Cookie: any cookies store in the browser for that domain
    - Authorization: authorization data for the user

- Response Headers:
    - Cache-Control: caching settings for the browser to follow (max-age, public, etc..)
    - Content-type: dictates how the browser can interpret the sent-data
    - Set-Cookie: Set a cookie stored on the browser

### B**ody Parser:**

- Middleware that decodes http body for node js (either url-encoded or JSON)

### **Cors: Cross Origin Resource Sharing**

- Security measure enforced by browsers to restrict Requests of data to a server from a different origin
- sent in the headers with the webpage
- Not an issue of the web page and the api come from the same server (the same origin)
- But a website may opt-in to making requests from api that are not its origin
- Headers are sent to the client stating what it may access.
    - Restrict Origins with: 'Access-Control-Allow-Origin': '*'
    - Restrict Headers with: 'Access-Control-Allow-Headers': 'Origin, Content-Type...'
    - Restrict Methods with: 'Access-Control-Allow-Methods': 'PUT, POST, DELETE'