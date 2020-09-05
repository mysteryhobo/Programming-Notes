# Caching

Resources: [https://medium.com/@codebyamir/a-web-developers-guide-to-browser-caching-cc41f3b73e7c](https://medium.com/@codebyamir/a-web-developers-guide-to-browser-caching-cc41f3b73e7c)

- Recently requested data is likely to get requested again
- Can be done all over the stack. (see types of caching below)
- I**n-Process Cache:** storing the data in the server process,
    - Cannot be shared between different servers
    - Server memory can overflow and cause issues
    - anytime the server is restart (deployment, or whatever) the cache is lost

- Out of process Cache: data is not stored in server memory
    - Cache can be shared between many servers
    - Is not lost on server restart
    - Slower than In-Process Cache

# Caching Strategies: (Not mutually exclusive)

### Reading Techniques:

1. Cache Aside:
    - Read from cache if not there read from db and write to the cache
    - work best on read-heavy workloads
    - write directly to the database

![https://miro.medium.com/max/580/1*Oxn6NVTlMoW25Kh6W4dT-w.png](https://miro.medium.com/max/580/1*Oxn6NVTlMoW25Kh6W4dT-w.png)

2. Read Through:

- Read from the cache if miss, the cache loads the data from the database then returns it to the application
- Good for read-heavy workloads
- Data model in cache must match database model (not exactly the case for cache-aside)

![https://miro.medium.com/max/700/1*616svTMDBscCYi30K0dgjQ.png](https://miro.medium.com/max/700/1*616svTMDBscCYi30K0dgjQ.png)

### Writing Techniques:

1. Write-Through:

- Data is Written to the cache first and then to the database
- Quite good when combined with read through.
- Data written to database from cache immediately

![https://miro.medium.com/max/700/1*X1ar9SskJKn3orcNmX-Fsg.png](https://miro.medium.com/max/700/1*X1ar9SskJKn3orcNmX-Fsg.png)

2. Write Around:

- Here, data is written directly to the database and only the data that is read makes it way into the cache.

![Caching%200e3669c4e0a74d9ba357fd6acfd76226/Untitled.png](Caching%200e3669c4e0a74d9ba357fd6acfd76226/Untitled.png)

3. Write-Back (also known as write-behind)

- Data is written to the cache and then after a delay it is written "back" to the database
- Good with write heavy workloads

![https://miro.medium.com/max/700/1*QVJVDsGyrSVEN5Wa8jP0kg.png](https://miro.medium.com/max/700/1*QVJVDsGyrSVEN5Wa8jP0kg.png)

# Types of Caching:

## Browser Caching:

- Browsers keep local copies of web pages in their cache to reduce load times
- The browser reads the headers of the http response from the web server.
- if there is a cache failure the data may be permanently lost

### Headers

- There are 4 headers commonly used for caching:
    - Etag
        - A hash of the file contents so once the file has expired the browser can check to see if a cached webpage is stale.
        - The browser sends the E tag to the server If the hash is the same, then the resource hasn’t changed and the server responds with a 304 response code (Not Modified) with an empty body. This lets the browser know it’s still safe to use the cached copy.
        - Only done once the file has expired

        ![https://miro.medium.com/max/700/1*hWsWByT7Vx3IOgSea_LcyA.png](https://miro.medium.com/max/700/1*hWsWByT7Vx3IOgSea_LcyA.png)

    - Cache-Control:

        Controls cache behavior, expiration, and validation.

        Cache Behavior

        - Cache-Control: public — the resource can be cached by any cache (browser, CDN, etc)
        - Cache-Control: private —   the resource can only be cached by the browser
        - Cache-Control: no-store — tells the browser to always request the resource from the server
        - Cache-Control: no-cache — This one is actually a bit misleading. This tells the browser to cache the file but not to use it until it checks with the server to validate we have the latest version. This validation is done with the ETag header. (Always Check)

        Expiration

        - Cache-Control: max-age=60 — This specifies the length of time in seconds the resource should be cached.
        - Cache-Control: s-max-age=60 — This is only used by intermediate caches like a CDN.

        Validation: 

        - Cache-Control: must-revalidate — This tells the cache it must verify the status of the stale resource before using it and expired ones should not be used.
    - Expires (OLD):
        - from the older HTTP 1.0 days but is still used on many sites.
        - This header field provides an expiration date after which the asset is considered invalid.
        - The browser will ignore this field if there’s a max-age directive in Cache-Control
        - Example: Expires: Wed, 25 Jul 2018 21:00:00 GMT
    - Last-Modified (OLD)
        - The Last-Modified header is also from the HTTP 1.0 days.
        - This field contains the date and time the resource was last modified.

    ### Cache Busting:

    When we invalidate a cached file and force the browser to retrieve the file from the server.

    - Typically done by changing the name of the file by:
        - Adding a version: assets/js/app-v2.min.js
        - fingerprinting: assets/js/app-d98ecf8427e.min.js
        - query strings: assets/js/app.min.js?version=2 (discouraged due to issues with proxy servers)

    ### **Best Practices:**

    Do:

    - Set long max-age values to reap the benefits of browser cache
    - Use fingerprinting or versioning for cache busting
    - Use the Cache-Control and ETag headers to control cache behavior for static assets

    Don't 

    - Use HTML meta tags to specify cache behavior
    - Use query strings for cache busting

    ### To **Prevent Caching:**

    To prevent a file from being cached use the following response header:

    Cache-Control: no-cache, no-store, must-revalidate

## ServerSide Caching (API Caching):

Cache API calls from the server to an API so you don't have to hit the API again

## Database Caching:

Usually built into the database to optimize reads and writes

## CDN or Intermediate Caches or Edge Caching:

Edge servers (also known as CDN servers) that sit between the origin server (my server) and the client and caches static files in the response so if the client needs it again it can respond faster because it is closer
- Examples: Cloudflare, AWS Cloudfront

[https://codeahoy.com/img/cache-aside.png](https://codeahoy.com/img/cache-aside.png)