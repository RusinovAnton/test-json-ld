# Test dynamic JSON-LD


## Using testing-tool
Testing if google search engine could parse dynamically added json-ld content.

https://search.google.com/structured-data/testing-tool/u/0/#url=https%3A%2F%2Frusinovanton.github.io%2Ftest-json-ld%2Findex.html


## Using fetch as google bot

![image]()

```html
HTTP/1.1 200 OK
Server: GitHub.com
Content-Type: text/html; charset=utf-8
Last-Modified: Fri, 29 Dec 2017 13:38:11 GMT
Access-Control-Allow-Origin: *
Expires: Fri, 29 Dec 2017 13:50:50 GMT
Cache-Control: max-age=600
X-Fastly-Request-ID: c539e7a7ab8b20737f40e7dab1bcb4de105289f5
X-GitHub-Request-Id: E980:1F36C:4DE4BBB:5283F75:5A4645E2
Content-Length: 1111
Accept-Ranges: bytes
Date: Fri, 29 Dec 2017 13:40:50 GMT
Via: 1.1 varnish
Age: 0
Connection: keep-alive
X-Served-By: cache-sea1041-SEA
X-Cache: MISS
X-Cache-Hits: 0
X-Timer: S1514554850.476255,VS0,VE4
Vary: Accept-Encoding

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Testing dynamic json-ld</title>
  <script type="text/javascript">
    const data = {
      "@context": "http://schema.org",
      "@type": "Movie",
        "name": "Dynamic"
    };
    const script = document.createElement('script');
    script.setAttribute('type', 'application/ld+json');
    script.text = JSON.stringify(data);
    document.head.append(script);
  </script>
  <script type="text/javascript">
    fetch('./data.json')
      .then(res => res.json())
      .then(data => {
        const script = document.createElement('script');
 
        script.setAttribute('type', 'application/ld+json');
        script.text = JSON.stringify(data);
        document.head.append(script);
      });
  </script>
  <script type="application/ld+json">
    {
      "@context": "http://schema.org",
      "@type": "Movie",
        "name": "Static"
    }
  </script>
</head>
<body>
  <h1>Hello</h1>
</body>
</html>
```
