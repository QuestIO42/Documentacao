# API Usuáros
/api/user

## Request vázio
O request vázio a principio retorna todos os usuários cadastrados no banco de dados.

Exemplo de resposta:
```json

[
    {
        "id": 2,
        "password": "123",
        "last_login": null,
        "is_superuser": false,
        "username": "test2",
        "first_name": "asas",
        "last_name": "asas",
        "email": "asas@asdsad.com",
        "is_staff": false,
        "is_active": false,
        "date_joined": "2023-11-17T23:38:00Z",
        "full_name": "dsdsdsd",
        "college_register": "212",
        "user_role": null,
        "account_status": null,
        "xp_count": null,
        "groups": [],
        "user_permissions": []
    },
    {
        "id": 3,
        "password": "123",
        "last_login": null,
        "is_superuser": false,
        "username": "test23",
        "first_name": "asas",
        "last_name": "asas",
        "email": "asas@asdsad.com",
        "is_staff": false,
        "is_active": false,
        "date_joined": "2023-11-17T23:38:00Z",
        "full_name": "dsdsdsd",
        "college_register": "212",
        "user_role": null,
        "account_status": null,
        "xp_count": null,
        "groups": [],
        "user_permissions": []
    },
    {
        "id": 4,
        "password": "123",
        "last_login": null,
        "is_superuser": false,
        "username": "postman",
        "first_name": "asas",
        "last_name": "asas",
        "email": "asas@asdsad.com",
        "is_staff": false,
        "is_active": false,
        "date_joined": "2023-11-17T23:38:00Z",
        "full_name": "dsdsdsd",
        "college_register": "212",
        "user_role": null,
        "account_status": null,
        "xp_count": null,
        "groups": [],
        "user_permissions": []
    },
    {
        "id": 5,
        "password": "sdsdsd",
        "last_login": "2023-11-17T23:42:00Z",
        "is_superuser": false,
        "username": "topostman",
        "first_name": "sds",
        "last_name": "dsds",
        "email": "sdsd@dsds.com",
        "is_staff": false,
        "is_active": false,
        "date_joined": "2023-11-17T23:42:00Z",
        "full_name": "sdsd",
        "college_register": "3232",
        "user_role": 0,
        "account_status": 0,
        "xp_count": 0,
        "groups": [],
        "user_permissions": []
    },
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
]

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
    "email": "
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
/api/user/1
```
E o retorno esperado deve ser um json com o usuário de ID 1.

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