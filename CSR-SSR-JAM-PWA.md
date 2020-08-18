# CSR / SSR / JAM / PWA

## History of Web Development

## Generation 0: Static Site

- No dynamic content just static html
- Only html and css

## **Generation 1: Dynamic Sites**

- No Javascript on the client
- Non-interactive pages linked together by anchor tags
- All content generated per-request on the server using some server side language

## **Generation 2: CSR SPAs**

javascript is sent to the browser to handle the first and every subsequent render.

Bad for seo (probably better now, since google has added support for javascript)

Slow initial render (needs to run the javascript before first page is visible)

only need to make one request to get all pages

subsequent requests for dynamic content

SPA: Single page application

- A single page of html is loaded by the browser and this page can be updated/changed using javascript to represent every "page" of a website.

## **Generation 3: SSR and CSR**

SSR for first render - page visible immediately 

javascript gets mounted on page - page then becomes interactable

Better for SEO since html is sent to browser instead of javascript and empty html page

To do server side rendering on react: 

1. render the component to a string, ReactDomServer.renderToString(<Component>);
2. inject the html string into your bare html page using some templating engine or template strings
3. write the client side javascript to pick up where the server left off? rerenders?

May lead to harder development since you cannot access the window object from the server and you can't access the global object from the client

### **Universal (Sometimes just called SSR):**

Running the same code on the client and the server

Possible with javascript with node since both node and the browser can interpret javascript.

Can you even do SSR platforms other than node? since they don't use the same language as the client.

ServerLess Pre-Rendering:

- Server side rendering a page for the first time but then caching it for all subsequent requests

## JAMStack

Javascript for interactive webpage

API for Data source and User Interaction

Markdown for pre-generated content

3 types of pages:

- Static pages (only html content): landing pages
- Build time (pre-rendered files): html file generated from markdown
- Page that needs dynamic data from an api
    - Javascript will make a request to a api to get the data
    - Page shows a spinner while waiting for the data.

Advantages:

- Cheaper / Easier Scaling
- Very fast static files
- Easier development since front-end is separated from the backend.

Cons:

- Slower dynamic pages. (There is no server to server side render the dynamic data)
- Dynamic content won't show up in SEO (because it is only rendered by the client after an api call)

Netlify: A Popular CDN with Jamstack

**Static Site Generator:** 

Tool that takes in markdown content and generates html pages

Can include javascript and styles

Gatsby.js: 

Static site generator using react and graphql

- Uses react to create the static site content and then serves it to the user as SPA
- Static content is good for SEO, SPA is good for user intractability

## Progressive Web Applications

Mobile app like experience but for a web app

- Install on mobile home screen
- App works when offline
- Push notifications
- Runs in the browser