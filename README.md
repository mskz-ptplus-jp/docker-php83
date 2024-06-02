# Docker Compose for PHP 8.3

## Requiment

- [PHP 8.3](https://www.php.net/releases/8.3/)
- [Apache 2.4](https://httpd.apache.org/)
- [PostgreSQL](https://www.postgresql.org/) latest
  - [pgAdmin4](https://www.pgadmin.org/) latest
- [Mailpit](https://mailpit.axllent.org/) latest

## Provisioning

## Run

```
docker compose up -d
```

## Stop

```
docker compose down
```

## Remove

```
docker compose down --rmi all --volumes
```

## Infomation

see) [.env](.env)

|             | URL                     | note |
|-            |-                        |-     |
| site        | http://localhost:30080  ||
| SchemaSpy   | http://localhost:30080/schema/  | see) [SchemaSpy](#SchemaSpy) |
| mailpit     | http://localhost:30025  ||
| pgAdmin4    | http://localhost:38888  | pgadmin4@example.jp / 123 |
| xdebug      |                         | port 39080 |

## SchemaSpy

Run commands in terminal of app container

```
java -jar /opt/schemaspy.jar -configFile /var/www/schema/schemaspy.properties
```