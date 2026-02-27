# subscription-backend-api

# Side notes about API

Uma função (handler) para acessar o banco ja basta porque não é nada que está exposto publicamente ( o backend acessando o banco direto por uma função sem ser via API), mas na hora do frontend acessar o banco, ai já é vira requisição HTTP, o que seria inseguro deixar sem uma API

# Complete Backend Course

# APIs

APIs contém:

Methods:

Métodos são os que já conhecemos, GET,POST,PUT,DELETE

Endpoints:

tipo GET /users, POST /users/{id}

Headers:

Headers contém informações extras sobre a request ou response.

Status code:

Toda chamada de API tem status code. (200 OK, 404...)

## Types of API

### RESTful APIs

São stateless, é a API que mais vamos ver, são as que usam urls e HTTP protocols normal. 
### GraphQL APIs

Super eficiente para lidar com large datasets

# Backend 

Backend is about managing data

# Hands-on

## Preparing the codebase

Instalamos ExpressJS (Framework de NodeJS)

(removemos bin e controllers folder)

Alteramos algumas configs no package.json

Instalamos eslint para manter a codebase clean conforme o projeto vai crescendo

## Create Express.js server

### Primeira Rota da API

```
import express from 'express';

  

const app = express ();

  

app.get('/', (req, res) => {

  res.send('Welcome to the Subscription Tracker API!');

  

});

  

app.listen(3000,() => {

    console.log('Server running on port 3000');

})

  

export default app;
```


O que eu fiz aqui foi criar minha primeira rota então basicamente, o app.listen é para fazer o servidor escutar na porta 3000, e o app.get é usando o app e um método http, por isso que o callback function do primeiro é res.send e o segundo é só um print no console.

 esse app tem tantas funcionalidades, isso é por fazer const app = express  onde o express é um framework que atribui coisas a essa constante chamada app
 
![[Pasted image 20260225152038.png]]
## Config - Set up Environments

Aqui configuramos um env.js e dois arquivos .env.development.local e .env.production.local, que são variáveis de ambiente, mudando o valor da PORTA que o servidor estará escutando, para alterar entre ambientes.

## Creating Routes

"You can have multiple routers for the same endpoint, but they need to be different methods (GET,POST)"

Aqui nós criamos um arquivo routes/ e dentro criamos rotas:

auth.routes.js
user.routes.js
subscription.routes.js

Todas essas rotas precisam ser instânciadas (importadas) no arquivo main que é o app.js

![[Pasted image 20260225162505.png]]

## MongoDB

User: rodrigoDB
Senha: Chacha75!!

Aqui precisamos adicionar a connection string do banco na variavel de ambiente de development 

precisamos criar uma folder chamada DATABASE e fazer o import do mongoose dentro do file mongodb.js

instanciar a função connectToDatabase e chamar ela no app.js

## Creating Models

"Models in our application let us know how the data looks like"

Models são basicamente as tabelas e entidades que teremos no banco, para isso criamos:

models/subscription.model.js
models/user.model.js

em cada uma definimos o schema de usuário e o schema de subscription

## Error Handler Middlewares

Middlewares são funções que ficam no meio do caminho entre a requisição e a resposta

Intercepetam a requisição antes de chegar na handler final.

Handler = Toda função que executa alguma coisa, essa é a definição de um Handler.

Error Handler é justamente essa função que fica entre a req e a res para pescar erros no caminho.

Precisamos criar uma folder middlewares/error.middleware.js

## JWT Auth


Para criar uma autenticação, nós já fizemos as rotas anteriormente e agora estamos criando controllers

Controllers são as funções (handlers) que performarão uma ação em determinada rota, estamos criando handlers para rotas.

controllers/auth.controller.js

O que é uma request body ? 

Request body é um objeto que contenha os dados vindo do lado do cliente. (POST request)

## Authorization
