# Tutorial de como rodar o Laravel em um container Docker

## Passo a passo

1 - Criar e entrar no diretório do projeto

```bash
mkdir example-dir && cd example-dir
```

2 - Rodar o comando para criar o projeto Laravel

```bash
docker run -u ${UID}:${UID} --rm -v $(pwd):/app composer create-project --prefer-dist laravel/laravel .
```

3 - Copiar os arquivos docker-compose.yml, Dockerfile e a pasta .docker para o diretório do projeto

4 - Rodar o comando para criar o container

```bash
docker compose up -d
```

5 - Acessar o container

```bash
docker compose exec php bash
```
