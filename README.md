docker-compose + nginx + various backends listening on different domains

`docker-compose up`

```
✓ 19:47 alexis @ unicorn in ~ $ curl localhost:8080
<ul><li><a href="/foo">foo</a></li><li><a href="/bar">bar</a></li></ul>
✓ 19:47 alexis @ unicorn in ~ $ curl --connect-to foo.corp:80:127.0.0.1:8080 --connect-to bar.corp:80:127.0.0.1:8080 bar.corp/bar
<html>
  <head>
    <title>Hello from bar!</title>
  </head>
  <body>
    <p>Hello from bar!</p>
    <p><a href="/foo">Wanna see /foo?</a></p>
  </body>
</html>
✓ 19:47 alexis @ unicorn in ~ $ curl --connect-to foo.corp:80:127.0.0.1:8080 --connect-to bar.corp:80:127.0.0.1:8080 bar.corp/foo
<html>
<head><title>404 Not Found</title></head>
<body>
<center><h1>404 Not Found</h1></center>
<hr><center>nginx/1.27.2</center>
</body>
</html>
✓ 19:47 alexis @ unicorn in ~ $ curl --connect-to foo.corp:80:127.0.0.1:8080 --connect-to bar.corp:80:127.0.0.1:8080 foo.corp/foo
<html>
  <head>
    <title>Hello from foo!</title>
  </head>
  <body>
    <p>Hello from foo!</p>
    <p><a href="/bar">Wanna see /bar?</a></p>
  </body>
</html>
```
