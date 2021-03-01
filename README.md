

# CRUD API com AWS Lambda e DynamoDB (NodeJS)

CRUD API com AWS Lambda e DynamoDB (NodeJS) é uma aplicação que demonstra a utilização de AWS Lambda, API Gateway e DynamaDB para criação de APIs.

  - [Arquitetura](https://github.com/fgouveia708/aws-nodejs-lambda-api-dynamodb#arquitetura)
  - [Caso de uso](https://github.com/fgouveia708/aws-nodejs-lambda-api-dynamodb#caso-de-uso)
  - [Setup](https://github.com/fgouveia708/aws-nodejs-lambda-api-dynamodb#setup)
  - [Deployment](https://github.com/fgouveia708/aws-nodejs-lambda-api-dynamodb#deployment)
  - [Uso](https://github.com/fgouveia708/aws-nodejs-lambda-api-dynamodb#uso)

## Arquitetura

![](https://raw.githubusercontent.com/fgouveia708/aws-nodejs-lambda-api-dynamodb/master/serverless.png)

## Caso de uso

- API para Web Application
- API para Mobile Application

## Setup

1. Instalar [NodeJS](https://nodejs.org/en/)
2. Instalar [Serverless](https://www.serverless.com/)

```bash
npm install serverless -g
```

3. Instalar todas dependências do projeto
   
```bash
npm install
```

## Deployment

1. Configurar AWS credentials:
   
```bash
export AWS_ACCESS_KEY_ID="..."
export AWS_SECRET_ACCESS_KEY="..."
export AWS_SESSION_TOKEN="..."
```

1. Publicar aplicação:

```bash
serverless deploy
```

O resultado esperado deve ser semelhante a:

```bash
Serverless: Packaging service...
Serverless: Excluding development dependencies...

Service Information
service: serverless-lambda-api-with-dynamodb
stage: dev
region: us-east-1
stack: serverless-lambda-api-with-dynamodb-dev
resources: 37
api keys:
  None
endpoints:
  POST - https://xxxxxxxxxx.execute-api.us-east-1.amazonaws.com/dev/contact
  GET - https://xxxxxxxxxx.execute-api.us-east-1.amazonaws.com/dev/contacts
  GET - https://xxxxxxxxxx.execute-api.us-east-1.amazonaws.com/dev/contact/{id}
  PUT - https://xxxxxxxxxx.execute-api.us-east-1.amazonaws.com/dev/contact/{id}
  DELETE - https://xxxxxxxxxx.execute-api.us-east-1.amazonaws.com/dev/contact/{id}
functions:
  create: serverless-lambda-api-with-dynamodb-dev-create
  getAll: serverless-lambda-api-with-dynamodb-dev-getAll
  get: serverless-lambda-api-with-dynamodb-dev-get
  update: serverless-lambda-api-with-dynamodb-dev-update
  delete: serverless-lambda-api-with-dynamodb-dev-delete
layers:
  None
```

## Uso

Você pode criar, recuperar, atualizar ou excluir contatos com os seguintes comandos:

### Criar um contato

```bash
curl -X POST https://XXXXXXX.execute-api.us-east-1.amazonaws.com/dev/contact --data '{"name":"Robert","email":"email@email.com","phone":"01234567890"}'
```

Exemplo do resultado:
```bash
{"id":"379c41f0-787b-11eb-8759-37b6eff35e6e","name":"Robert","email":"email@email.com","phone":"01234567890","createdAt":1614375617422,"updatedAt":1614375617422}
```

### Buscar todos os contatos

```bash
curl https://XXXXXXX.execute-api.us-east-1.amazonaws.com/dev/contacts
```

Exemplo do resultado:
```bash
[{"id":"379c41f0-787b-11eb-8759-37b6eff35e6e","name":"Robert","email":"email@email.com","phone":"01234567890","createdAt":1614375617422,"updatedAt":1614375617422},{"id":"379c41f0-787b-11eb-8759-37b6eff35e6e","name":"Mary","email":"email@email.com","phone":"01234567890","createdAt":1614375617422,"updatedAt":1614375617422}]
```

### Buscar um contato

```bash
# Substitua a parte <id> por uma id real da sua tabela de contatos
curl https://XXXXXXX.execute-api.us-east-1.amazonaws.com/dev/contact/<id>
```

Exemplo do resultado:
```bash
{"id":"379c41f0-787b-11eb-8759-37b6eff35e6e","name":"Robert","email":"email@email.com","phone":"01234567890","createdAt":1614375617422,"updatedAt":1614375617422}
```

### Atualizar um contato

```bash
# Substitua a parte <id> por uma id real da sua tabela de contatos
curl -X PUT https://XXXXXXX.execute-api.us-east-1.amazonaws.com/dev/contact/<id> --data '{"id":"379c41f0-787b-11eb-8759-37b6eff35e6e","name":"Robert","email":"email@email.com","phone":"01234567890","createdAt":1614375617422,"updatedAt":1614375617422}'
```

Exemplo do resultado:
```bash
{"id":"379c41f0-787b-11eb-8759-37b6eff35e6e","name":"Robert","email":"email@email.com","phone":"01234567890","createdAt":1614375617422,"updatedAt":2314375617422}
```

### Excluir um contato

```bash
# Substitua a parte <id> por uma id real da sua tabela de contatos
curl -X DELETE https://XXXXXXX.execute-api.us-east-1.amazonaws.com/dev/contact/<id>
```

Sem resultado
