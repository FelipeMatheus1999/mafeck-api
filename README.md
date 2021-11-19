## MAFECK-HAKI API (SAMUEL GRUPO 2) ##
Base URL: https://mafeck-api.herokuapp.com/

## Endpoints

Existem 3 endpoints que podem ser utilizados para cadastro, 2 endpoints que podem ser usados para login, 1 para criar uma pessoa, 1 para criar os comentários e 1 para atualizar.

## ROTAS QUE NÃO PRECISAM DE AUTENTICAÇÃO ##

### Cadastro

POST /register <br/>
POST /signup <br/>
POST /users

Qualquer um desses 3 endpoints irá cadastrar o usuário na lista de "Users", sendo que os campos obrigatórios são os de email e password.
Você pode ficar a vontade para adicionar qualquer outra propriedade no corpo do cadastro dos usuários.

body: {<br/>
	"username": "teste",<br/>
	"email": "teste@gmail.com",<br/>
	"password": "123456Aa@",<br/>
	"phone": "990991234",<br/>
	"oab": "451267",<br/>
	"state": "CE"<br/>
       }

response: {<br/>
              "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InRlc3RlQGdtYWlsLmNvbSIsImlhdCI6MTYzNjU1MjUwNywiZXhwIjoxNjM2NTU2MTA3LCJzdWIiOiIyIn0.pG3YWQF3h4uxGor-HKG3wN36WZKLtGMeNTNAA4kaAEg",<br/>
              "user": {
                "email": "teste@gmail.com",<br/>
                "username": "teste",<br/>
		"phone": "990991234",<br/>
	        "oab": "451267",<br/>
	        "state": "CE",<br/>
                "id": 1<br/>
              }<br/>
            }

### Login

POST /login <br/>
POST /signin

Qualquer um desses 2 endpoints pode ser usado para realizar login com um dos usuários cadastrados na lista de "Users"

body: {<br/>
        "email": "teste@gmail.com",<br/>
        "password": "123456Aa@"<br/>
        }

response: {<br/>
              "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InRlc3RlQGdtYWlsLmNvbSIsImlhdCI6MTYzNjU1MjUwNywiZXhwIjoxNjM2NTU2MTA3LCJzdWIiOiIyIn0.pG3YWQF3h4uxGor-HKG3wN36WZKLtGMeNTNAA4kaAEg",<br/>
              "user": {
                "email": "teste@gmail.com",<br/>
                "username": "teste",<br/>
                "id": 2<br/>
              }<br/>
            }


## ROTAS QUE PRECISAM DE AUTENTICAÇÃO ##

Rotas que necessitam de autorização deve ser informado no cabeçalho da requisição o campo "Authorization", dessa forma:

Authorization: Bearer {token}


# Create People #

Nesse endpoint você pode criar uma pessoa. 

POST /users/userId/people - FORMATO DA REQUISIÇÃO

body: {<br/>
      "name": "teste1",<br/>
      "cpf": "055.321.435.80",<br/>
      "genre": "masculíno",<br/>
      "naturalness": "Cearense",<br/>
      "nationality": "Brasileiro",<br/>
      "fatherName": "Pedro Arruda da silva",<br/>
      "motherName": "Maria Ericka da silva",<br/>
      "qualification": "",<br/>
      "company": "Kenzie",<br/>
      "phone": "9-9423.4566",<br/>
      "type": "PF",<br/>
      "maritalStatus": "Casado",<br/>
      "address": {
        "road": "Cágado",<br/>
        "zipCode": "355399.10",<br/>
        "district": "Ben fica",<br/>
        "houseNumber": "456"<br/>
      },<br/>
      "comments": [],<br/>
    }

FORMATO DA RESPOSTA

response: {<br/>
          "name": "teste1",<br/>
          "cpf": "055.321.435.80",<br/>
          "genre": "masculíno",<br/>
          "naturalness": "Cearense",<br/>
          "nationality": "Brasileiro",<br/>
          "fatherName": "Pedro Arruda da silva",<br/>
          "motherName": "Maria Ericka da silva",<br/>
          "qualification": "",<br/>
          "company": "Kenzie",<br/>
          "phone": "9-9423.4566",<br/>
          "type": "PF",<br/>
          "maritalStatus": "Casado",<br/>
          "address": {
            "road": "Cágado",<br/>
            "zipCode": "355399.10",<br/>
            "district": "Ben fica",<br/>
            "houseNumber": "456"<br/>
          },
          "comments": [],<br/>
          "userId": "2",<br/>
          "id": 3<br/>
        }

# Patch People #

Esse endpoint atualiza o usuário e o array de comentários. É preciso está logado para atualizar.

Atualizar pessoa
PATCH /people/peopleId - FORMATO DA REQUISIÇÃO

body :{<br/>
        "name": "teste",<br/>
        "cpf": "055.321.435.80",<br/>
        "genre": "masculíno",<br/>
        "naturalness": "Cearense",<br/>
        "nationality": "Brasileiro",<br/>
        "fatherName": "Pedro Arruda da silva",<br/>
        "motherName": "Maria Ericka da silva",<br/>
        "qualification": "",<br/>
        "company": "Kenzie",<br/>
        "phone": "9-9423.4566",<br/>
        "type": "PF",<br/>
        "maritalStatus": "Casado",<br/>
        "address": {
            "road": "Cágado",<br/>
            "zipCode": "355399.10",<br/>
            "district": "Ben fica",<br/>
            "houseNumber": "456"<br/>
        }<br/>
    }
    

  FORMATO DA RESPOSTA 

response: {<br/>
          "name": "teste",<br/>
          "cpf": "055.321.435.80",<br/>
          "genre": "masculíno",<br/>
          "naturalness": "Cearense",<br/>
          "nationality": "Brasileiro",<br/>
          "fatherName": "Pedro Arruda da silva",<br/>
          "motherName": "Maria Ericka da silva",<br/>
          "qualification": "",<br/>
          "company": "Kenzie",<br/>
          "phone": "9-9423.4566",<br/>
          "type": "PF",<br/>
          "maritalStatus": "Casado",<br/>
          "address": {
            "road": "Cágado",<br/>
            "zipCode": "355399.10",<br/>
            "district": "Ben fica",<br/>
            "houseNumber": "456"<br/>
          },<br/>
          "comments": [<br/>
            {<br/>
	      "title": "comment teste",<br/>
              "comment": "teste",<br/>
              "id": 1<br/>
            }<br/>
          ],
          "userId": "2",<br/>
          "id": 1<br/>
        } 


# Patch Comments #

Atualizar comentários
PATCH /people/peopleId - FORMATO DA REQUISIÇÃO

body: {"title": "title comment" , comment": "comment...", "id": 1}

FORMATO DA RESPOSTA

response: {<br/>
          "name": "teste",<br/>
          "cpf": "055.321.435.80",<br/>
          "genre": "masculíno",<br/>
          "naturalness": "Cearense",<br/>
          "nationality": "Brasileiro",<br/>
          "fatherName": "Pedro Arruda da silva",<br/>
          "motherName": "Maria Ericka da silva",<br/>
          "qualification": "",<br/>
          "company": "Kenzie",<br/>
          "phone": "9-9423.4566",<br/>
          "type": "PF",<br/>
          "maritalStatus": "Solteiro",<br/>
          "address": {
            "road": "Cágado",<br/>
            "zipCode": "355399.10",<br/>
            "district": "Ben fica",<br/>
            "houseNumber": "456"<br/>
          },<br/>
          "comments": [<br/>
            {<br/>
	      "title": "teste title",<br/>
              "comment": "teste",<br/>
              "id": 1<br/>
            }<br/>
          ],<br/>
          "userId": "2",<br/>
          "id": 1<br/>
        }

# Remove People #

DELETE /people/peopleId

body: null

FORMATO DA RESPOSTA

response: 200 OK: {}
