# MongoDB para Desenvolvimento com Docker

Este repositorio contem o comando oficial para subir um MongoDB local em container para desenvolvimento pontual.

## Comando

```bash
docker run --name docker_mongo_dev --rm -d -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=mongo_usr -e MONGO_INITDB_ROOT_PASSWORD=mongo_pwd mongo:8.0
```

## Configuracao criada

- Usuario root: `mongo_usr`
- Senha root: `mongo_pwd`
- Porta local: `27017`

## Parar o container

```bash
docker stop docker_mongo_dev
```
