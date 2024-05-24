# Docker for PHP 8.3

## Provisioning

### Configure ngrok for HTTPS

1. Go to the ngrok dashboard and set up <YOUR_AUTH_TOKEN>.
    - https://dashboard.ngrok.com/get-started/your-authtoken

2. Create ngrok.yaml
    ```
    version: "2"
    authtoken: <YOUR_AUTH_TOKEN>
    tunnels:
    app:
        proto: http
        addr: app:80
        host_header: rewrite
    ```

## Run

```
docker compose up -d
```

## Stop

```
docker compose down
```

## Infomation

see) [.env](.env)

|             | URL                     | note |
|-            |-                        |-     |
| site        | http://localhost:30080  ||
| site(https) | http://localhost:34040  |Get started, Access URL in browser.<br>Make a request of HTTPS tunnel. |
| mailpit     | http://localhost:30025  ||
| pgAdmin4    | http://localhost:38888  | pgadmin4@example.jp / 123 |
| xdebug      |                         | port 39080 |
