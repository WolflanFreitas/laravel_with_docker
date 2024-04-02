# Tutorial de como rodar o Laravel em um container Docker

## Requisitos

- Docker
- Docker Compose
- Composer
- Laravel
- PHP
- MySQL
- Nginx

## Criar projeto Laravel

1 - Criar e entrar no diretório do projeto

```bash
mkdir example-dir && cd example-dir
```

2 - Rodar o comando para criar o projeto Laravel

```bash
docker run -u ${UID}:${UID} --rm -v $(pwd):/app composer create-project --prefer-dist laravel/laravel .
```
