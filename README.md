# Producer and Consumer RabbitMQ

Este projeto contém uma solução Producer e uma solução Consumer utilizando RabbitMQ. Ele utiliza Docker e Docker Compose para facilitar o ambiente de desenvolvimento e implantação.

## Estrutura do Projeto

- `producer-rabbitmq/`: Contém o código fonte e o Dockerfile para a solução Producer.
- `consumer-rabbitmq/`: Contém o código fonte e o Dockerfile para a solução Consumer.
- `docker-compose.yml`: Arquivo de configuração do Docker Compose para orquestrar os serviços.

## Pré-requisitos

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Configuração

1. Clone este repositório:

```bash
git clone https://github.com/seu-usuario/producer-and-consumer-rabbitmq.git
cd producer-and-consumer-rabbitmq
```

2. Certifique-se de ter o Docker e o Docker Compose instalados.

## Executando o Projeto

Para iniciar todos os serviços, execute o seguinte comando na raiz do projeto:

```bash
docker-compose up --build
```

Este comando fará o build das imagens Docker para o Producer e Consumer, e iniciará o RabbitMQ junto com os dois serviços.

## Serviços

  - Producer RabbitMQ: Serviço que envia mensagens para o RabbitMQ.
  - Producer RabbitMQ: Serviço que envia mensagens para o RabbitMQ.
  - Consumer RabbitMQ: Serviço que consome mensagens do RabbitMQ.
  - RabbitMQ Service: Serviço RabbitMQ com interface de gerenciamento acessível via http://localhost:15672 (usuário: user, senha: password).

# Configuração do Docker Compose

```

version: '3.8'

services:
  producer-rabbitmq:
    image: ${DOCKER_REGISTRY-}producerrabbitmq
    build:
      context: .
      dockerfile: producer-rabbitmq/Dockerfile

  consumer-rabbitmq:
    image: ${DOCKER_REGISTRY-}consumerrabbitmq
    build:
      context: .
      dockerfile: consumer-rabbitmq/Dockerfile

  rabbitmq-service:
    container_name: rabbitmq-service
    tty: true
    hostname: rabbitmq
    ports:
      - "15672:15672"
      - "5672:5672"
    image: rabbitmq:3-management
    environment:
      - RABBITMQ_DEFAULT_USER=user
      - RABBITMQ_DEFAULT_PASS=password

 ```

## Acessando a Interface de Gerenciamento do RabbitMQ

Você pode acessar a interface de gerenciamento do RabbitMQ em http://localhost:15672 usando as credenciais fornecidas na configuração do Docker Compose (usuário: user, senha: password).
