# TRUE-CARDS
#### Run development build

Run

```
docker-compose --file docker-compose-dev.yml --env-file ./api/.env up
```

Rebuild after local packages install

```
docker-compose --file docker-compose-dev.yml --env-file ./api/.env up --build -V
```

#### Run production build

```
docker-compose --file docker-compose-prod.yml --env-file ./api/.env up
```

Rebuild after local packages install

```
docker-compose --file docker-compose-prod.yml --env-file ./api/.env up --build -V
```
