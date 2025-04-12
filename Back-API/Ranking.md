# API Ranking

### Visualizar ranking do site
    [GET] /ranking  

Retorna os 10 usuários cadastrados com maior XP.

```json
// request
{}
// response
[
    {
        "id": "1ed8b3c6-d683-4081-b369-512efe2eb573",
        "username": "123456", // RA do aluno
        "full_name": "Fulano de tal",
        "email": "fulano@estudante.ufscar.br",
        "last_login": "2023-11-17T23:38:00Z",
        "user_role": "STUDENT", // STUDENT, MENTOR, TEACHER, ADMIN
        "xp_main": "0",
    },
    {
        "id": "4a870aca-072c-4fbc-9f5d-20490f8fe19c",
        "username": "567890", // RA do aluno
        "full_name": "Beltrano de tal",
        "email": "beltrano@estudante.ufscar.br",
        "last_login": "2023-11-17T23:38:00Z",
        "user_role": "MENTOR",
        "xp_main": "0",
    },
]
```

### Visualizar ranking do curso
    [GET] /ranking/{course}  

Retorna todos os usuários cadastrados no curso e sua pontuação dentro deste.

```json
// request
{}
// response
[
    {
        "id": "1ed8b3c6-d683-4081-b369-512efe2eb573",
        "username": "123456", // RA do aluno
        "full_name": "Fulano de tal",
        "email": "fulano@estudante.ufscar.br",
        "last_login": "2023-11-17T23:38:00Z",
        "user_role": "STUDENT", // STUDENT, MENTOR, TEACHER, ADMIN
        "xp_course": "0",
    },
    {
        "id": "4a870aca-072c-4fbc-9f5d-20490f8fe19c",
        "username": "567890", // RA do aluno
        "full_name": "Beltrano de tal",
        "email": "beltrano@estudante.ufscar.br",
        "last_login": "2023-11-17T23:38:00Z",
        "user_role": "MENTOR",
        "xp_course": "0",
    },
]
```
