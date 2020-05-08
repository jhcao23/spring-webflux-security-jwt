1. chrome will automatically send `username/password` with header (in a form of `Authorization: Basic WEIRD_TOKEN_LIKE_dXNlcjp1c2Vy`) after 1st time login. It's not because the Application doing cache or cookie things.
    The magic part is actually done by `org.springframework.security.web.server.authentication.ServerHttpBasicAuthenticationConverter`.
    Actually the `WEIRD_TOKEN` part is encoded automatically in web then decoded in server side using `Base64.getDecoder().decode()` method.
2. How does the frontend (web) do the encoding automatically? Not sure - I guess it's a builtin method of browser.
    But this is reasonable and no javascript involved as the `curl` command doesn't do magic.
    [Mozilla specs also mentions this](https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication#Basic_authentication_scheme "Mozilla Official website").   