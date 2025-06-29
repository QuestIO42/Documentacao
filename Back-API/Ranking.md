# API Ranking

## Visualizar ranking geral
    [GET] /ranking

Retorna os usuários cadastrados com maior XP.

### Request:
```json
{}
```

### Response:
```json
[
    {
        "full_name": "Fulano de tal",
        "total_xp": 1000
    },
    {
        "full_name": "Beltrano de tal",
        "total_xp": 800
    }
]
```

## Visualizar ranking do usuário autenticado
    [GET] /ranking/user

Retorna a posição e os detalhes do ranking do usuário autenticado.

### Request:
```json
{}
```

### Response:
```json
{
    "user_ranking": {
        "full_name": "Fulano de tal",
        "total_xp": 1000
    },
    "position": 1
}
```
