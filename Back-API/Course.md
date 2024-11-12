# API Cursos

         [GET] /course  

Retorna todos os cursos cadastrados no portal (por exemplo, para o usuário se inscrever em cursos abertos).

```json
// request
{}
// response
[
    {
        "id": "1ed8b3c6-d683-4081-b369-512efe2eb573",
        "name": "LD2024S2", 
        "description": "Lógica Digital (2024S2)",
    },
    {
        "id": "4a870aca-072c-4fbc-9f5d-20490f8fe19c",
        "name": "LD2024S1", 
        "description": "Lógica Digital (2024S1)",
    },
]
```

         [GET] /course/user/{idUser}  // cursos de um usuário  

Retorna os cursos em que um usuário está inscrito. 

```json
// request
{
    "idUser": "1ed8b3c6-d683-4081-b369-512efe2eb573",
}
// response
[
    {
        "id": "1ed8b3c6-d683-4081-b369-512efe2eb573",
        "name": "LD2024S2", 
        "description": "Lógica Digital (2024S2)",
    },
]
```