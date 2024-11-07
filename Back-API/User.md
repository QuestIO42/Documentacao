# API Usuáros

    /user

## Request vázio

O request vázio a principio retorna todos os usuários cadastrados no banco de dados.

Exemplo de resposta:
```json

[
    {
        "id": "1ed8b3c6-d683-4081-b369-512efe2eb573",
        "username": "123456", // RA do aluno
        "full_name": "Fulano de tal",
        "email": "fulano@estudante.ufscar.br",
        "last_login": "2023-11-17T23:38:00Z",
        "user_role": "STUDENT", // STUDENT, MENTOR, TEACHER, ADMIN
        "xp_course": "0",
        "xp_main": "0",
    },
    {
        "id": "4a870aca-072c-4fbc-9f5d-20490f8fe19c",
        "username": "567890", // RA do aluno
        "full_name": "Beltrano de tal",
        "email": "beltrano@estudante.ufscar.br",
        "last_login": "2023-11-17T23:38:00Z",
        "user_role": "MENTOR",
        "xp_course": "0",
        "xp_main": "0",
    },
]


//atualizar TODO

```
## Request com parâmetros (POST|BODY) | Criação de usuários
O request com parâmetros no corpo da requisição remente a crição de usuários no banco de dados.

o corpo do request deve seguir o padrão:
```json
{
    "password": "",
    "last_login": ,
    "is_superuser": ,
    "username": "",
    "first_name": "",
    "last_name": "",
    "email": "",
    "is_staff": ,
    "is_active": ,
    "date_joined": "",
    "full_name": "",
    "college_register": "",
    "user_role": ,
    "account_status": ,
    "xp_count": ,
    "groups": [],
    "user_permissions": []
}
```

um exemplo de request com parâmetros é:
```json
{
    "password": "ufscarAdmin",
    "last_login": null,
    "is_superuser": false,
    "username": "Marlon",
    "first_name": "Marlon",
    "last_name": "He4rt",
    "email": "marlon@themail.com",
    "is_staff": false,
    "is_active": false,
    "date_joined": "2023-11-17T23:42:00Z",
    "full_name": "Marlon He4rt",
    "college_register": "909090",
    "user_role": 0,
    "account_status": 0,
    "xp_count": 0,
    "groups": [],
    "user_permissions": []
}
```
## Request com parâmetros (GET|URL) | Busca de usuários

O request com parâmetros na URL remente a busca de usuários no banco de dados.

Para realizar a busca via ID o request deve seguir o padrão:
```
/api/user/6
```
E o retorno esperado deve ser um json com o usuário de ID 6.

```json
{
    "id": 6,
    "password": "232323",
    "last_login": null,
    "is_superuser": false,
    "username": "dopostamn",
    "first_name": "dsds",
    "last_name": "dsdsd",
    "email": "dsds@csds.com",
    "is_staff": false,
    "is_active": false,
    "date_joined": "2023-11-17T23:42:00Z",
    "full_name": "sds",
    "college_register": "sdsdd",
    "user_role": 0,
    "account_status": 0,
    "xp_count": 0,
    "groups": [],
    "user_permissions": []
}
```

### Importação/exportação de dados

- Importação de usuários de uma turma do AVA2 [[formato](import_users.csv)]
- Exportacão de notas para uma turma do AVA2 [[formato](export_grades.csv)]