# Docker

## Docker Básico

## Imagens

Abaixo temos dois exercícios para criação de imagens, o primeiro é mais simples e o segundo ligeiramente mais complexo. Lembre-se que o código deve ser copiado para dentro do contêiner.

### 01 - Flask

Flask é um microframework em Python para criar aplicações web bastante utilizado para APIs Rest.

Utilizar o código da aplicação em https://github.com/4linux/4542-python para construir uma imagem chamada **flask-site**.

- Basear a imagem em **alpine**
- Instalar os pacotes `py3-pip`
- Utilizar o **pip** para instalar as dependências da aplicação presentes em `requirements.txt`
  ```
  pip install -r /diretorio/aplicacao/requirements.txt
  ```
- O comando do contêiner deverá ser `python3 /diretorio/aplicacao/app.py`
- A aplicação, por padrão, escuta na interface local na porta 5000, estes parâmetros podem ser modificados pelas variáveis `APP_HOST` e `APP_PORT` respectivamente.

> **Observação:** Substituir `/diretorio/aplicacao` pelo caminho que achar mais conveniente.

### 02 - Dancer

Dancer é um framework em Perl para criar aplicações web bastante utilizado para APIs Rest.

A construção desta imagem é relativamente demorada pois centenas de testes são executados durante a instalação, sendo assim, utilize as camadas que achar necessário e preste atenção para evitar builds desnecessárias.

Utilizar o código da aplicação em https://github.com/4linux/4542-perl para construir uma imagem chamada **<usuario>/dancer**.

- Basear a imagem em **debian:buster-slim**
- Esta aplicação depende de um servidor **redis**, a comunicação é ditada pelas variáveis da aplicação, não é necessário usar senha.
- Instalar os pacotes `perl cpanminus make gcc`
- O comando para instalar as dependências do **perl** é `cpanm --installdeps /diretorio/aplicacao`
- O comando do contêiner deverá ser `plackup /diretorio/aplicacao/bin/app.psgi`
- Por padrão, a aplicação escuta na porta 5000

> **Observação:** Substituir `/diretorio/aplicacao` pelo caminho que achar mais conveniente.

Enviar a imagem para o Docker Hub.

## Docker Compose

Criar um **docker-compose.yml** capaz de subir o contêiner **<usuario>/dancer** criado anteriormente juntamente de um outro contêiner com **redis** e deixar a aplicação acessível na porta 8080 da sua máquina.