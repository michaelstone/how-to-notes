# HSTS - HTTP Strict Transport Security

## TL;DR

Security enhancement for web applications to prevent attacks related to data being transmitted over insecure HTTP unintentionally.

## Scenario

1. A user navigates to a site via a HTTP url (e.g. http://hsbc.co.uk). The initial request is redirected (301 moved permanently) to the HTTPS url. However, a malicious user can intercept and potentially modify this request via a man in the middle attack. (see SSL Stripping)  

2. Sites inadvertently serves resources over insecure HTTP, allowing malicious code to be injected to the browser.


## Prevention

- Where browser support exists, websites can return the strict-transport-security header to force the browser to always use HTTPS for the site regardless. HTTP requests are automatically converted to HTTPS without the need for a redirect from the server.

- A preloaded list of sites is being added to browsers to remove the need for an initial header instruction over a potentially insecure connection.

- chrome://net-internals/#hsts 

## Challenges

- Preload list permanently affects users (or until max-age reached) if problems related to certification configuration arise
- All resources, including all images, stylesheets served need to be requested using HTTPS. (see Automatic HTTPS Rewrites, Cloudflare)

## Browsers

### Chrome
Version 56 - Sites with a password or credit card input fields marked as 'not secure' if not served over HTTPS.
Version 62 - Any sites with an input box marked as 'not secure' if not served over HTTPS.


## Resources

- https://www.owasp.org/index.php/HTTP_Strict_Transport_Security_Cheat_Sheet
- https://hstspreload.org/
- https://www.troyhunt.com/understanding-http-strict-transport/
- https://www.chromium.org/hsts

### SSL Stripping
- https://www.youtube.com/watch?v=MFol6IMbZ7Y
