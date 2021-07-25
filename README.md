# TRUE-CARDS
#### Development build

Run

```
docker-compose --file docker-compose-dev.yml --env-file ./api/.env up
```

Rebuild after local packages install

```
docker-compose --file docker-compose-dev.yml --env-file ./api/.env up --build -V
```

#### Production build

Run

```
docker-compose --file docker-compose-prod.yml --env-file ./api/.env up
```

Rebuild after local packages install

```
docker-compose --file docker-compose-prod.yml --env-file ./api/.env up --build -V
```
