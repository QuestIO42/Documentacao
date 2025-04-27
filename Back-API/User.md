# API Usuários

         [GET] /user  

Retorna todos os usuários cadastrados no portal.

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
        "role": "STUDENT", // STUDENT, MENTOR, TEACHER, ADMIN
        "xp_count": "0",
    },
    {
        "id": "4a870aca-072c-4fbc-9f5d-20490f8fe19c",
        "username": "567890", // RA do aluno
        "full_name": "Beltrano de tal",
        "email": "beltrano@estudante.ufscar.br",
        "user_role": "MENTOR",
        "xp_count": "0",
    },
]
```

## Request com parâmetros (GET|URL) | Busca de usuário

         [GET] /user/{id}  

O request com parâmetros na URL remente a busca de um usuário no banco de dados. 

E o retorno esperado deve ser um json com o usuário de ID especificado.

```json
// response
{
    "id": "4a870aca-072c-4fbc-9f5d-20490f8fe19c",
    "username": "567890", // RA do aluno
    "full_name": "Beltrano de tal",
    "email": "beltrano@estudante.ufscar.br",
    "user_role": "MENTOR",
    "xp_count": "0",
}
```

## Request com parâmetros (PUT|URL) | Alteração de senha
         [PUT] /user/{id}  
Deve ser usado para alterar a senha do usuario apos verificar o pedido de alteração de senha em `[GET] /auth/reset-password/{uuid4}` 
```json
// request
{
    "password": "secret123"
}
// response
{
    "id": "4a870aca-072c-4fbc-9f5d-20490f8fe19c",
    "username": "567890", // RA do aluno
    "full_name": "Beltrano de tal",
    "email": "beltrano@estudante.ufscar.br",
    "user_role": "MENTOR",
    "xp_count": "0",
    "password": "JWTeyJhbGciOiJIUzI1NiIsInR5cCI6IkpX"
}
```
## Request com parâmetros (PUT|URL) | Alteração de senha
         [PATCH] /user/{id}  
Deve ser usado para alterar as informações de um usuário
```json
// request
{
    "username": "567890",                         //opcional
    "full_name": "Beltrano de tal",               //opcional
    "email": "beltrano@estudante.ufscar.br",      //opcional
}
// response
{
    "username": "567890", // RA do aluno
    "full_name": "Beltrano de tal",
    "email": "beltrano@estudante.ufscar.br",
}
```
# Importação/exportação de dados

## Importação de alunos em um curso

         [POST] /user       // para importação de usuário

```json
// request
{
    "course_id": "4a870aca-072c-4fbc-9f5d-20490f8fe19c",
    "file": "import_users.csv" // especificar como será o envio do arquivo (ver formato a seguir)
} 
// response
[
    {
        "id": "1ed8b3c6-d683-4081-b369-512efe2eb573",
        "full_name": "Fulano de tal",
        "status": "created", // Novo aluno cadastrado e inscrito
    },
    {
        "id": "4a870aca-072c-4fbc-9f5d-20490f8fe19c",
        "full_name": "Beltrano de tal",
        "status": "subscribed", // Aluno existente, apenas foi inscrito
    },
    {
        "id": "7a870aca-072c-4fbc-9f5d-20490f8ff19c",
        "full_name": "Cicrano de tal",
        "status": "none", // Aluno existente, ja estava inscrito no curso
    },
]
```

- Importação de usuários de uma turma do AVA2 [[formato](import_users.csv)]
- Exportacão de notas para uma turma do AVA2 [[formato](export_grades.csv)]