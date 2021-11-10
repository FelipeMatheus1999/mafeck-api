# json-server-base

Base URL: https://mafeck-api.herokuapp.com/
Esse é o repositório com a base de JSON-Server + JSON-Server-Auth já configurada, feita para ser usada no desenvolvimento das API's nos Capstones do Q2.

## Endpoints

Existem 3 endpoints que podem ser utilizados para cadastro, 2 endpoints que podem ser usados para login, 1 para criar uma pessoa, 1 para criar os comentários e 1 para atualizar.

### Cadastro

POST /register <br/>
POST /signup <br/>
POST /users

body: {
       "username": "teste",
       "email": "teste@gmail.com",
       "password": "123456Aa@"
       }

response: {
              "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InRlc3RlQGdtYWlsLmNvbSIsImlhdCI6MTYzNjU1MjUwNywiZXhwIjoxNjM2NTU2MTA3LCJzdWIiOiIyIn0.pG3YWQF3h4uxGor-HKG3wN36WZKLtGMeNTNAA4kaAEg",
              "user": {
                "email": "teste@gmail.com",
                "username": "teste",
                "id": 2
              }
            }

Qualquer um desses 3 endpoints irá cadastrar o usuário na lista de "Users", sendo que os campos obrigatórios são os de email e password.
Você pode ficar a vontade para adicionar qualquer outra propriedade no corpo do cadastro dos usuários.

### Login

POST /login <br/>
POST /signin

body: {
        "email": "teste@gmail.com",
        "password": "123456Aa@"
        }

response: {
              "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InRlc3RlQGdtYWlsLmNvbSIsImlhdCI6MTYzNjU1MjUwNywiZXhwIjoxNjM2NTU2MTA3LCJzdWIiOiIyIn0.pG3YWQF3h4uxGor-HKG3wN36WZKLtGMeNTNAA4kaAEg",
              "user": {
                "email": "teste@gmail.com",
                "username": "teste",
                "id": 2
              }
            }

Qualquer um desses 2 endpoints pode ser usado para realizar login com um dos usuários cadastrados na lista de "Users"

### Create People

POST /users/userId/people, Authorization: true.

body: {
      "name": "teste1",
      "cpf": "055.321.435.80",
      "genre": "masculíno",
      "naturalness": "Cearense",
      "nationality": "Brasileiro",
      "father's name": "Pedro Arruda da silva",
      "mother's name": "Maria Ericka da silva",
      "qualification": "",
      "company": "Kenzie",
      "phone": "9-9423.4566",
      "type": "PF",
      "marital status": "Casado",
      "address": {
        "road": "Cágado",
        "zip code": "355399.10",
        "district": "Ben fica",
        "house number": "456"
      },
      "comments": [],
    }

response: {
          "name": "teste1",
          "cpf": "055.321.435.80",
          "genre": "masculíno",
          "naturalness": "Cearense",
          "nationality": "Brasileiro",
          "father's name": "Pedro Arruda da silva",
          "mother's name": "Maria Ericka da silva",
          "qualification": "",
          "company": "Kenzie",
          "phone": "9-9423.4566",
          "type": "PF",
          "marital status": "Casado",
          "address": {
            "road": "Cágado",
            "zip code": "355399.10",
            "district": "Ben fica",
            "house number": "456"
          },
          "comments": [],
          "userId": "2",
          "id": 3
        }

Nesse endpoint você pode criar uma pessoa. É preciso está logado para criar uma pessoa.

### Patch People

PATCH /people/peopleId, Authorization: true.

Esse endpoint atualiza o usuário e o array de comentários. É preciso está logado para atualizar.

atualizar pessoa
body :{
        "name": "teste",
        "cpf": "055.321.435.80",
        "genre": "masculíno",
        "naturalness": "Cearense",
        "nationality": "Brasileiro",
        "father's name": "Pedro Arruda da silva",
        "mother's name": "Maria Ericka da silva",
        "qualification": "",
        "company": "Kenzie",
        "phone": "9-9423.4566",
        "type": "PF",
        "marital status": "Casado",
        "address": {
            "road": "Cágado",
            "zip code": "355399.10",
            "district": "Ben fica",
            "house number": "456"
        }
    }
    
response: {
          "name": "teste",
          "cpf": "055.321.435.80",
          "genre": "masculíno",
          "naturalness": "Cearense",
          "nationality": "Brasileiro",
          "father's name": "Pedro Arruda da silva",
          "mother's name": "Maria Ericka da silva",
          "qualification": "",
          "company": "Kenzie",
          "phone": "9-9423.4566",
          "type": "PF",
          "marital status": "Casado",
          "address": {
            "road": "Cágado",
            "zip code": "355399.10",
            "district": "Ben fica",
            "house number": "456"
          },
          "comments": [
            {
              "comment": "teste",
              "id": 1
            }
          ],
          "userId": "2",
          "id": 1
        } 

atualizar comentários
body: {"comment": "comment...", "id": 1}

response: {
          "name": "teste",
          "cpf": "055.321.435.80",
          "genre": "masculíno",
          "naturalness": "Cearense",
          "nationality": "Brasileiro",
          "father's name": "Pedro Arruda da silva",
          "mother's name": "Maria Ericka da silva",
          "qualification": "",
          "company": "Kenzie",
          "phone": "9-9423.4566",
          "type": "PF",
          "marital status": "Solteiro",
          "address": {
            "road": "Cágado",
            "zip code": "355399.10",
            "district": "Ben fica",
            "house number": "456"
          },
          "comments": [
            {
              "comment": "teste",
              "id": 1
            }
          ],
          "userId": "2",
          "id": 1
        }

### Remove People

DELETE /people/peopleId, Authorization: true.
body: null

response: 200 OK: {}
