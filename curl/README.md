# Curl / HTTP Formatting

Curl GET/POST endpoints from app served on `localhost:8080`
```
curl -X [method] [url]
curl -X GET "http://localhost:8080/api/v1/stuff"
curl -X POST "http://localhost:8080/api/v1/entry" ...
```

Curl URL with a space in a parameter (replace _space_ with `%20`)
```
curl -X GET "http://localhost:8080/api/v1/authors/J.K.%20Rowling"
```