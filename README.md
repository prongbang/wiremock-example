# Wiremock Example

```
  _      ___                        __  
 | | /| / (_)______ __ _  ___  ____/ /__
 | |/ |/ / / __/ -_)  ' \/ _ \/ __/  '_/
 |__/|__/_/_/  \__/_/_/_/\___/\__/_/\_\

 -> wiremock server started on :8000

```

- Docker

```
$ docker-compose up
```

- Golang

```
$ go get -u github.com/prongbang/wiremock/v2
$ wiremock
```

## Server running 

- [http://localhost:8000](http://localhost:8000)

## Login 

#### Success

```bash
curl --header "Content-Type: application/json" \
  --request POST \
  --data '{"username":"admin","password":"pass"}' \
  http://localhost:8000/api/v1/login
```

- Result

```json
{"message": "success"}
```

#### Fail

```bash
curl --header "Content-Type: application/json" \
  --request POST \
  --data '{"username":"admin","password":"1234"}' \
  http://localhost:8000/api/v1/login
```

- Result

```json
{
  "errors":{
    "password":"The password not match"
  },
  "message":"validation error",
  "status":"error"
}
```

### Create User

```bash
curl --request POST http://localhost:8000/api/v1/user
```

- Result

```json
{"message": "success"}
```

### Get User by ID

```bash
curl http://localhost:8000/api/v1/user/1
```

- Result

```json
[
  {
    "id": 1,
    "name": "Leanne Graham",
    "username": "Bret",
    "email": "Sincere@april.biz",
    "address": {
      "street": "Kulas Light",
      "suite": "Apt. 556",
      "city": "Gwenborough",
      "zipcode": "92998-3874",
      "geo": {
        "lat": "-37.3159",
        "lng": "81.1496"
      }
    },
    "phone": "1-770-736-8031 x56442",
    "website": "hildegard.org",
    "company": {
      "name": "Romaguera-Crona",
      "catchPhrase": "Multi-layered client-server neural-net",
      "bs": "harness real-time e-markets"
    }
  }
]
```