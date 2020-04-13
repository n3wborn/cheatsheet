# HTTPIE

Ce soft est dans la  meme veine que wget et curl.
Il est cependant un peu plus user friendly avec sa chouette interface
On le trouvera dans les depots habituels.
Quant au [site](https://httpie.org/) il montre des exemples sympas que voici:


**Hello World**

    http httpbin.org/get

**Custom HTTP method, HTTP headers and JSON data**

    http PUT httpbin.org/put X-API-Token:123 name=John

**Submitting forms**

    http -f POST httpbin.org/post hello=World

**See the request that is being sent using one of the output options**

    http -v httpbin.org/get

**Use Github API to post a comment on an issue with authentication**

    http -a USERNAME POST https://api.github.com/repos/jakubroztocil/httpie/issues/83/comments body='HTTPie is awesome! :heart:'

**Upload a file using redirected input**

    http httpbin.org/post < file.json

**Download a file and save it via redirected output**

    http httpbin.org/image/png > image.png

**Download a file wget style**

    http --download httpbin.org/image/png

**Use named sessions to make certain aspects or the communication persistent between requests to the same host**

    http --session=logged-in -a username:password httpbin.org/get API-Key:123

    http --session=logged-in httpbin.org/headers

**Set a custom Host header to work around missing DNS records**

    http localhost:8000 Host:example.com


