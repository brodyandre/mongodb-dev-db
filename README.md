# MongoDB para Desenvolvimento com Docker

Repositorio com setup padronizado para subir um MongoDB local em container, com foco em desenvolvimento pontual e onboarding rapido de times.

## Objetivo

Disponibilizar um comando unico para criar um ambiente MongoDB local com credenciais fixas para desenvolvimento:

- Usuario root: `mongo_usr`
- Senha root: `mongo_pwd`

## Pre-requisitos

- Docker instalado e em execucao
- Porta `27017` disponivel na maquina local

## Comando oficial

```bash
docker run --name docker_mongo_dev --rm -d -p 127.0.0.1:27017:27017 -e MONGO_INITDB_ROOT_USERNAME=mongo_usr -e MONGO_INITDB_ROOT_PASSWORD=mongo_pwd mongo:8.0
```

## O que este comando provisiona

- Container: `docker_mongo_dev`
- Imagem: `mongo:8.0`
- Usuario administrador (root): `mongo_usr`
- Senha do administrador: `mongo_pwd`
- Exposicao de porta: `localhost:27017`
- Remocao automatica do container ao parar (`--rm`)

## String de conexao

Use a URI abaixo nas aplicacoes locais:

```txt
mongodb://mongo_usr:mongo_pwd@localhost:27017/?authSource=admin
```

## Operacao do dia a dia

1. Subir o banco:

```bash
docker run --name docker_mongo_dev --rm -d -p 127.0.0.1:27017:27017 -e MONGO_INITDB_ROOT_USERNAME=mongo_usr -e MONGO_INITDB_ROOT_PASSWORD=mongo_pwd mongo:8.0
```

2. Ver logs:

```bash
docker logs -f docker_mongo_dev
```

3. Acessar o shell do MongoDB:

```bash
docker exec -it docker_mongo_dev mongosh -u mongo_usr -p mongo_pwd --authenticationDatabase admin
```

4. Parar o ambiente:

```bash
docker stop docker_mongo_dev
```

## Escopo e limitacoes

- Esta configuracao e exclusiva para desenvolvimento local.
- Nao ha persistencia garantida de dados apos parada/remocao.
- Nao utilizar este setup como baseline de producao.
