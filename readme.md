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

Alternativo - Poderá também criar o projeto sem informar a pasta antes

```bash
docker run -u ${UID}:${UID} --rm -v $(pwd):/app composer create-project --prefer-dist laravel/laravel "nome_do_projeto"
```

3 - Copiar os arquivos docker-compose.yml, Dockerfile e a pasta .docker para dentro do diretório do projeto

4 - Rodar o comando para criar o container

```bash
docker compose up -d
```

5 - Acessar o container

```bash
docker compose exec php bash
```

6 - Rodar o comando para instalar as dependências do Laravel

```bash
composer install
```

7 - Rodar o comando para criar a chave do Laravel

```bash
php artisan key:generate
```

8 - Acessar o projeto no navegador

```
http://localhost:8080
```

## Comandos úteis

- Rodar o container

```bash
docker compose up -d
```

- Acessar o container

```bash
docker compose exec php bash
```

- Parar o container

```bash
docker compose down
```

- Ver os containers rodando

```bash
docker ps
```

- Ver os containers parados

```bash
docker ps -a
```

- Ver os volumes

```bash
docker volume ls
```

- Ver as imagens

```bash
docker images
```

- Ver os logs do container

```bash
docker compose logs -f
```

- Ver os logs do container de forma específica

```bash
docker compose logs -f php
```

- Executar npm install

```bash
docker compose run --rm node npm install
```

- Instalar pacote composer

```bash
docker compose run --rm composer require "nome_do_pacote"
```

- Listar portas em uso

```bash
sudo lsof -i -P -n | grep LISTEN
```

- Instalar dependências em projeto existente

  ```bash
  docker run --rm \
    -u "$(id -u):$(id -g)" \
    -v "$(pwd):/var/www/html" \
    -w /var/www/html \
    laravelsail/php83-composer:latest \
    composer install --ignore-platform-reqs
  ```

- Instalar dependências em projeto existente com npm

  ```bash
  docker run --rm \
    -u "$(id -u):$(id -g)" \
    -v "$(pwd):/var/www/html" \
    -w /var/www/html \
    laravelsail/node:latest \
    npm install
  ```

  ````bash
  sudo docker compose run -u root php bash
  ````

- Instalar Portainer

  ```bash
  docker run -d -p 9000:9000 -p 8000:8000 -p 9443:9443 \ --name portainer \ --restart=always \ -v /var/run/docker.sock:/var/run/docker.sock \ -v portainer_data:/data portainer/portainer-ce:latest
  ```
