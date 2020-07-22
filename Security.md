# Security

Authentication: [Authentication](https://www.notion.so/Authentication-6411cfd0e61a4945a4f0c744c56b2bd6) 

Data Management

- Encrypt Sensitive Data (B-crypt)
- Passwords, emails, SIN

Authorization (Access Control):

- Principle of least privilege
- Role-based, group-based, policy-based

Secure Headers:

- Use Helmet: [https://helmetjs.github.io/](https://helmetjs.github.io/)

Code Secrets:

- Environment variables: use .env file, keep it secret and don't commit it
- can also use a deployment management software to handle environment configurations

XSS & CSRF:

- Cross Site Scripting: Updating a web page with user data with validating it allowing user script to run on other clients,
    - then they could redirect you or access your cookies, ect..
- Cross Site Request Forgery: ???
- Don't use eval() or document.write()
- set up CORS
- Use secure: requires https for cookies
- Use httponly: prevents js access to cookies

HTTPS: (See http notes)

- Encrypts HTTP Requests
- Transport Layer Security (TLS), although formerly it was known as Secure Sockets Layer (SSL)

Logging:

- Install proper logging so you can detect a breach
- Monitoring logs for suspicious activity

3rd Party Libraries:

- npm audit to check for vulnerabilities and update libraries that are out of date

Injections:

- Use an ORM to prevent injections or create your own parameterized queries
- Sanitize Input: Assume all data is Evil and sanitize it before use

Request Limiting

- prevent DDOS attacks by limiting the number of requests an ip can make to the api