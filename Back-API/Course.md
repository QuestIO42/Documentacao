# API Cursos

## Visualizar todos os cursos
    [GET] /course

Retorna todos os cursos cadastrados no portal (por exemplo, para o usuário se inscrever em cursos abertos).

### Request:
```json
{}
```

### Response:
```json
[
    {
        "id": "1ed8b3c6-d683-4081-b369-512efe2eb573",
        "name": "LD2024S2", 
        "description": "Lógica Digital (2024S2)"
    },
    {
        "id": "4a870aca-072c-4fbc-9f5d-20490f8fe19c",
        "name": "LD2024S1", 
        "description": "Lógica Digital (2024S1)"
    }
]
```

## Visualizar cursos de um usuário
    [GET] /course/user/{idUser}

Retorna os cursos em que um usuário está inscrito.

### Request:
```json
{
    "idUser": "1ed8b3c6-d683-4081-b369-512efe2eb573"
}
```

### Response:
```json
[
    {
        "id": "1ed8b3c6-d683-4081-b369-512efe2eb573",
        "name": "LD2024S2", 
        "description": "Lógica Digital (2024S2)"
    }
]
```

## Exportar notas de um curso
    [GET] /course/exportgrade/{idCourse}

Exporta as notas dos alunos de um curso específico em formato CSV.

### Request:
```json
{}
```

### Response:
Arquivo CSV com as notas dos alunos.

## Importar dados de um curso
    [POST] /course/import

Importa os dados de um curso a partir de um arquivo JSON.

### Request:
```json
{
    "name": "Curso Exemplo",
    "description": "Descrição do curso",
    "open": true,
    "quizzes": [],
    "questions": [],
    "categories": []
}
```

Para mais detalhes sobre o formato do arquivo JSON, consulte o exemplo em [curso_export_example.json](../curso_export_example.json).

### Response:
```json
{
    "message": "Curso importado com sucesso."
}
```

## Exportar curso em formato JSON
    [GET] /course/export/{idCourse}

Exporta os dados de um curso específico em formato JSON.

### Request:
```json
{}
```

### Response:
Arquivo [JSON](../curso_export_example.json) com os dados do curso.

## Duplicar um curso
    [POST] /course/duplicate/{idCourse}

Duplica um curso existente, criando uma cópia com um novo nome.

### Request:
```json
{}
```

### Response:
```json
{
    "message": "Curso duplicado com sucesso."
}
```