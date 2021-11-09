# json-server-base

Base URL: https://mafeck-api.herokuapp.com/
Esse é o repositório com a base de JSON-Server + JSON-Server-Auth já configurada, feita para ser usada no desenvolvimento das API's nos Capstones do Q2.

## Endpoints

Existem 3 endpoints que podem ser utilizados para cadastro, 2 endpoints que podem ser usados para login, 1 para criar uma pessoa, 1 para criar os comentários e 1 para atualizar.

### Cadastro

POST /register <br/>
POST /signup <br/>
POST /users

Qualquer um desses 3 endpoints irá cadastrar o usuário na lista de "Users", sendo que os campos obrigatórios são os de email e password.
Você pode ficar a vontade para adicionar qualquer outra propriedade no corpo do cadastro dos usuários.

### Login

POST /login <br/>
POST /signin

Qualquer um desses 2 endpoints pode ser usado para realizar login com um dos usuários cadastrados na lista de "Users"

### Create People

POST /users/userId/people, Authorization: true.

Nesse endpoint você pode criar uma pessoa. É preciso está logado para criar uma pessoa.

### Patch People

PATCH /people/peopleId, Authorization: true.

Esse endpoint atualiza o usuário e o array de comentários. É preciso está logado para atualizar.

Ex:

atualizar pessoa:

{
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

atualizar comentários: 

{"comment": "comment...", "id": 1}


### Remove People

DELETE /people/peopleId, Authorization: true.
