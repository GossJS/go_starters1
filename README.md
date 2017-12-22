# go_starters1
golang

- сервер с докером предположим 95.213.200.238
- `docker run --name go -p 4321:4321 -itd golang:1.10beta1-alpine3.7 tail -f /dev/null`
- `docker exec -it go sh`
- `vi web.go`
```golang
package main

import (
"fmt"
"net/http"
)

func handler(w http.ResponseWriter, r *http.Request) {
  fmt.Fprintf(w, "Hi there, I love %s!", r.URL.Path[1:])
}

func main() {
  http.HandleFunc("/", handler)
  http.ListenAndServe(":4321", nil)
}
```
- `go run web.go`
- или извне контейнера: `docker exec -it go go run web.go`
- в браузере http://95.213.200.238:4321/apples/
