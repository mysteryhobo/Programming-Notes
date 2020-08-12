# Authentication

## Sessions:

Sessions does not necessarily mean authenticated sessions

2 main express.js libraries: 

- Cookie-Session: [https://www.npmjs.com/package/cookie-session](https://www.npmjs.com/package/cookie-session)
    - Stateless
    - Session ID is stored in a cookie on the browser
- Express-session: [https://www.npmjs.com/package/express-session](https://www.npmjs.com/package/express-session)
    - Stateful
    - Session ID stored in cookie on the client
    - Session data stored on the server (in memory by default)
    - Loses sessions on server shutdown

## Authentication

- Cookie based authentication:
    - Needs to be stateful, there must be some storage of the user
    - Passport.js Integrates with either? of the above session middlewears to create a stateful authenticated session.

- Token based authentication:
    - Most popular is JWT (JSON web tokens)
    - Stateless, JWT is only stored on the client
        - validating the token does not require it to be stored on the server
    - You cannot revoke the sessions though unless you store them (in which case why not just use cookies)
    - JWT can contain some data in them but it is readable with anyone with access
    - JWTs are great for passing authentication between apis
    - JWTs are a lot bigger than cookies
    - Token can be stored in window.sessionStorage on the client

    ## **Scalability**

    **Session based authentication:** Because the sessions are stored in the server’s memory, scaling becomes an issue when there is a huge number of users using the system at once.

    **Token based authentication:** There is no issue with scaling because token is stored on the client side

    ## **Multiple Devices**

    **Session based authentication:** Cookies normally work on a single domain or subdomains and they are [normally disabled by browser](https://medium.com/building-contently/tracking-people-across-multiple-domains-when-cookies-just-arent-enough-b270cc95beb1) if they work cross-domain (3rd party cookies). It poses issues when APIs are served from a different domain to mobile and web devices.

    **Token based authentication:** There is no issue with cookies as the JWT is included in the request header.

## Authorization:

- OAuth:
    - Meant for service to service authorization
    - User can login to their account on some service which would then allow them access to another service
    - This is Authorization because google is authorizing the app (service to service) to access the users google account

    Steps:

    1. Service makes request to google to access users account
    2. google asks user to login to their account
    3. if Successful google creates a JWT and gives it to the service so the service can make future requests to google without needing to prompt the user again
    4. Service then uses the token to access the users account

## **Email Confirmation:**

- Generate a JWT
- Add JWT to a url as a query parameter and send it to the users email
- Add route to server to handle the request made by clicking the link
    - verify the JWT and set the confirmedEmail flag on the user.