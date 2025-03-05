## Teste de Avaliação - Backend

Leonardo do Amaral

## Passos para implementar a API

1. Configurar o banco de dados no .env
DB_CONNECTION=mysql\
DB_HOST=127.0.0.1\
DB_PORT=3306\
DB_DATABASE=api_crud_bindflow\
DB_USERNAME=root\
DB_PASSWORD=

2. Rodar a migration
php artisan migrate

## Como usar:
1. inicie o servidor local com "php artisan serve"
deve iniciar no endereço "http://127.0.0.1:8000"

2. Criar um Usuário (Registro)

Para acessar as rotas privadas, crie um usuário.

POST http://127.0.0.1:8000/api/register

{
  "name": "Teste",
  "email": "teste@gmail.com",
  "password": "123456"
}

o retorno esperado:

{
  "token": "seu-bearer-token"
}

Copie esse token para usar nas próximas requisições.

3. Fazer login

POST http://127.0.0.1:8000/api/login
{
  "email": "teste@gmail.com",
  "password": "123456"
}

resposta:
{
  "token": "seu_token"
}
Copie esse token para usar nas próximas requisições.

4. Criar um Produto (POST)

POST http://127.0.0.1:8000/api/products
Authorization: Bearer seu_token\
{\
  "nome": "Creatina",\
  "sku": "123456",\
  "valor": 149.99\
}\

5.  Listar Produtos (GET)
GET http://127.0.0.1:8000/api/products
Authorization: Bearer seu_token

6. Buscar um Produto Específico (GET)
GET http://127.0.0.1:8000/api/products/{id}
Authorization: Bearer seu_token

7. Atualizar um Produto (PUT)
PUT http://127.0.0.1:8000/api/products/{id}
Authorization: Bearer seu_token\
{\
  "nome": "Creatina Monohidratada",\
  "sku": "654321",\
  "valor": 99.99\
}\

8. Deletar um Produto (DELETE)
DELETE http://127.0.0.1:8000/api/products/{id}
Authorization: Bearer seu_token

9. Logout
POST http://127.0.0.1:8000/api/logout
Authorization: Bearer seu_token
