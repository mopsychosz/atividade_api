# atividade_api
API Cafeteria:

API simples feita em Node.js com Express, alinhada com o que aparece nas aulas 1, 2, 3 e 4:
Aula 1: princípios REST, URIs em plural e JSON
Aula 2: setup do ambiente, primeira API, Postman e scripts npm
Aula 3: endpoints GET, busca por ID, filtro, ordenação e paginação
Aula 4: endpoint POST, `express.json()`, geração de ID e validações

Setup do ambiente:

Segundo as aulas iniciais, o ambiente mínimo fica assim:
Node.js instalado
npm funcionando
Postman instalado
Git configurado

Como rodar:

bash
npm install
npm start

Para desenvolvimento com reinício automático:
bash
npm run dev

Servidor:
http://localhost:3000

Lista de todos os endpoints:

1. GET /

Método: GET /
URL completa: http://localhost:3000/
Body:{}

Resposta esperada:
json
{
  "mensagem": "API cafeteria funcionando.",
  "status": "sucesso",
  "timestamp": "2026-04-07T00:00:00.000Z",
  "rotas": {
    "me": "GET /api/me",
    "data": "GET /api/data",
    "random": "GET /api/random",
    "listar": "GET /api/produtos",
    "filtrar": "GET /api/produtos?categoria=bebida_quente",
    "ordenar": "GET /api/produtos?ordem=preco&direcao=asc",
    "paginar": "GET /api/produtos?pagina=1&limite=2",
    "buscarPorId": "GET /api/produtos/1",
    "criar": "POST /api/produtos"
  }
}

2. GET /api/me

Método: GET /api/me
URL completa: http://localhost:3000/api/me
Body: {}

Resposta esperada:
json
{
  "nome": "Thiago Galtra",
  "profissao": "Professor/Empresario",
  "hobbies": [
    "programar",
    "jogar",
    "testar API"
  ],
  "linguagens": [
    "JavaScript",
    "Python"
  ]
}

3. GET /api/data

Método: GET /api/data
URL completa: http://localhost:3000/api/data
Body:{}

Resposta esperada:
json
{
  "data_hora": "2026-04-07T00:00:00.000Z"
}

4. GET /api/random

Método: GET /api/random
URL completa: http://localhost:3000/api/random
Body:{}

Resposta esperada:
json
{
  "numero": 42
}

5. GET /api/produtos

Método: GET /api/produtos
URL completa: http://localhost:3000/api/produtos
Body:{}

Resposta esperada:

json
[
  {
    "id": 1,
    "nome": "café expresso",
    "categoria": "bebida_quente",
    "preco": 8,
    "estoque": 50
  }
]

6. GET /api/produtos?categoria=bebida_quente

Método: GET /api/produtos?categoria=bebida_quente
URL completa: http://localhost:3000/api/produtos?categoria=bebida_quente
Body: {}

Resposta esperada:

json
[
  {
    "id": 1,
    "nome": "café expresso",
    "categoria": "bebida_quente",
    "preco": 8,
    "estoque": 50
  },
  {
    "id": 2,
    "nome": "cappuccino",
    "categoria": "bebida_quente",
    "preco": 12,
    "estoque": 30
  }
]

7. GET /api/produtos?ordem=preco&direcao=asc

Método: GET /api/produtos?ordem=preco&direcao=asc
URL completa: http://localhost:3000/api/produtos?ordem=preco&direcao=asc
Body:{}

Resposta esperada:

json
[
  {
    "id": 3,
    "nome": "pão de queijo",
    "categoria": "salgado",
    "preco": 6,
    "estoque": 40
  }
]

(O Pão de Queijo será retornado primeiro por ser o item de menor valor).

8. GET /api/produtos?pagina=1&limite=2

Método: GET /api/produtos?pagina=1&limite=2
URL completa: http://localhost:3000/api/produtos?pagina=1&limite=2
Body:{}

Resposta esperada:

json
{
  "dados": [
    {
      "id": 1,
      "nome": "café expresso",
      "categoria": "bebida_quente",
      "preco": 8,
      "estoque": 50
    },
    {
      "id": 2,
      "nome": "cappuccino",
      "categoria": "bebida_quente",
      "preco": 12,
      "estoque": 30
    }
  ],
  "paginacao": {
    "pagina_atual": 1,
    "itens_por_pagina": 2,
    "total_itens": 5,
    "total_paginas": 3
  }
}

9. GET /api/produtos/:id

Método: GET /api/produtos/1
URL completa: http://localhost:3000/api/produtos/1
Body:{}

Resposta esperada:

json
{
  "id": 1,
  "nome": "café expresso",
  "categoria": "bebida_quente",
  "preco": 8,
  "estoque": 50
}

Resposta se não encontrar:

json
{
  "erro": "Produto não encontrado."
}

10. POST /api/produtos

Método: POST /api/produtos
URL completa:** http://localhost:3000/api/produtos

Body:
json
{
  "nome": "torta de maçã",
  "categoria": "doce",
  "preco": 14,
  "estoque": 12
}

Resposta esperada:

json
{
  "id": 6,
  "nome": "torta de maçã",
  "categoria": "doce",
  "preco": 14,
  "estoque": 12
}

Exemplos de requisição no Postman:

Collection salva no arquivo
postman_collection.json

Requisições prontas na collection:
GET /
GET /api/me
GET /api/data
GET /api/random
GET /api/produtos
GET /api/produtos?categoria=bebida_quente
GET /api/produtos?ordem=preco&direcao=asc
GET /api/produtos?pagina=1&limite=2`
GET /api/produtos/1
POST 1 - café xxpresso
POST 2 - cappuccino
POST 3 - pão de queijo
POST 4 - bolo de cenoura
POST 5 - frappuccino
POST invalido

5 recursos criados via POST

Os 5 exemplos de criação via POST que estão na collection:

json
[
  {
    "nome": "café expresso",
    "categoria": "bebida_quente",
    "preco": 8,
    "estoque": 50
  },
  {
    "nome": "cappuccino",
    "categoria": "bebida_quente",
    "preco": 12,
    "estoque": 30
  },
  {
    "nome": "pão de queijo",
    "categoria": "salgado",
    "preco": 6,
    "estoque": 40
  },
  {
    "nome": "bolo de Cenoura",
    "categoria": "doce",
    "preco": 10,
    "estoque": 15
  },
  {
    "nome": "frappuccino",
    "categoria": "bebida_gelada",
    "preco": 18,
    "estoque": 20
  }
]

Explicação das validações implementadas:

No POST /api/produtos, a API valida
nome obrigatório
categoria obrigatória
preco obrigatório
estoque numérico quando enviado
nome com pelo menos 3 caracteres
categoria com pelo menos 3 caracteres
preco deve ser número
preco deve ser maior que zero
estoque não pode ser negativo

Também usei express.json() para ler o body JSON e proximoId para gerar IDs automaticamente, exatamente no estilo mostrado na aula 4.

Exemplo de erro:
json
{
  "erro": "Campos obrigatórios: nome, preco, categoria."
}

Testes manuais no localhost
Para rodar a API localmente:

bash
npm install
npm start

#Depois disso, teste manualmente no Postman usando:

GET http://localhost:3000/
GET http://localhost:3000/api/me
GET http://localhost:3000/api/data
GET http://localhost:3000/api/random
GET http://localhost:3000/api/produtos
GET http://localhost:3000/api/produtos?categoria=bebida_quente`
GET http://localhost:3000/api/produtos?ordem=preco&direcao=asc`
GET http://localhost:3000/api/produtos?pagina=1&limite=2
GET http://localhost:3000/api/produtos/1
POST http://localhost:3000/api/produtos
