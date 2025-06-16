# API Respostas dos Usuários

## Criar Respostas para um Questionário
    [POST] /userquizquestionanswer

Cria as respostas de um questionário para um usuário. Se houver um questionário não enviado, retorna um erro indicando a tentativa atual aberta.

### Request:
```json
{
    "id_user": "321372b4-8631-4fef-9fc0-c961952239f1",
    "id_quiz": "7ab20845-69ee-45ae-a768-3339890f6a9b"
}
```

### Responses:
```json
// Sucesso
[
    {
        "id": "7617ee90-3def-46bc-99a5-745778fe38f2",
        "id_user": "321372b4-8631-4fef-9fc0-c961952239f1",
        "id_quiz": "7ab20845-69ee-45ae-a768-3339890f6a9b",
        "id_question": "7a7796c0-978b-4871-805a-1d9e622bbc23",
        "current_try": 1
    },
    {
        "id": "e8c2db85-a2e4-4e08-bf71-8563736b3640",
        "id_user": "321372b4-8631-4fef-9fc0-c961952239f1",
        "id_quiz": "7ab20845-69ee-45ae-a768-3339890f6a9b",
        "id_question": "5650afed-f0b3-4ff8-a774-392f72e6e6e5",
        "current_try": 1
    },
    ...
] Response Code 201

// Erro: Questionário em andamento
{
    "feedback": "O usuário ainda está com o quiz em andamento",
    "current_try": 1
} Response Code 400
```

## Obter Respostas de um Questionário
    [GET] /userquizquestionanswer/quiz/{id_quiz}

Retorna os objetos de resposta do questionário do usuário em uma tentativa.

### Request:
```json
{
    "id_user": "321372b4-8631-4fef-9fc0-c961952239f1",
    "current_try": 1
}
```

### Response:
```json
[
    {
        "id": "30bbec4d-b8c3-4ace-b4c6-b1f15a1898ac",
        "text_answer": null,
        "entry_date": "2025-05-25T15:27:51.247976-03:00",
        "score": 0,
        "current_try": 1,
        "delivered": false,
        "id_user": "321372b4-8631-4fef-9fc0-c961952239f1",
        "id_quiz": "7ab20845-69ee-45ae-a768-3339890f6a9b",
        "id_question": "7a7796c0-978b-4871-805a-1d9e622bbc23",
        "id_answer": null
    },
    ...
] Response Code 200
```

## Responder Questão
    [PUT] /userquizquestionanswer/<uuid:pk>

Altera o objeto de resposta do questionário do usuário. Deve ser usado para alterar as respostas de uma questão. Os campos são opcionais.

Essa rota não corrige as respostas, apenas altera o objeto de resposta. Para corrigir as respostas, use a rota de enviar questionário.

### Request:
```json
{
    "text_answer": "Resposta do usuario", // resposta discursiva e de verilog
    "id_answer": "7a7796c0-978b-4871-805a-1d9e622bbc23" // resposta multipla escolha
}
```

### Response:
```json
{
    "id": "b9474673-55ef-4ef1-b9a4-719143bff3d4",
    "text_answer": "Resposta do usuario",
    "entry_date": "2025-05-25T15:27:51.249805-03:00",
    "score": 0,
    "current_try": 1,
    "delivered": false,
    "id_user": "321372b4-8631-4fef-9fc0-c961952239f1",
    "id_quiz": "7ab20845-69ee-45ae-a768-3339890f6a9b",
    "id_question": "5650afed-f0b3-4ff8-a774-392f72e6e6e5",
    "id_answer": "7a7796c0-978b-4871-805a-1d9e622bbc23"
} Response Code 200
```

## Enviar Questionário
    [POST] /userquizquestionanswer/send

Envia e salva as respostas de um usuário em um quiz. Responde uma lista com os resultados de cada questão. Retorna um erro caso o usuário não tenha um quiz aberto.

### Request:
```json
{
    "id_user": "321372b4-8631-4fef-9fc0-c961952239f1",
    "id_quiz": "7ab20845-69ee-45ae-a768-3339890f6a9b"
}
```

### Response:
```json
[
    // resposta discursivas
    {   // correta
        "id": "1ed8b3c6-d683-4081-b369-512efe2eb573",
        "score": "100",
        "result": "right", // "right" | "wrong" | "partial"
        "feedback": "Well done!" // this is optional 
    },
    {   // não corrigida automaticamente
        "id": "1ed8b3c6-d683-4081-b369-512efe2eb573",
        "score": "0",
        "result": "partial", // "right" | "wrong" | "partial"
        "feedback": "Necessário verificação do professor!"
    },

    // respostas multipla escolha
    {   // correta
        "id": "1ed8b3c6-d683-4081-b369-512efe2eb573",
        "score": "100",
        "result": "right" // "right" | "wrong" | "partial"
    },
    {   // errada
        "id": "1ed8b3c6-d683-4081-b369-512efe2eb573",
        "score": "0",
        "result": "wrong" // "right" | "wrong" | "partial"
    },
    {   // sem resposta
        "id": "1ed8b3c6-d683-4081-b369-512efe2eb573",
        "score": 0,
        "result": "wrong",
        "feedback": "ID da resposta inválido"
    },

    // respostas de verilog
    {   // erro de sintaxe
        "id": "1ed8b3c6-d683-4081-b369-512efe2eb573",
        "score": "0"
        "result": "wrong" // "right" | "wrong" | "partial"
        "feedback": {
            "1ed8b3c6-d683-4081-b369-512efe2eb573": {
            "message": "Erro no teste sum: Erro de compilação em module top\n (input flip, output zero, one);\n assign zero = flip ? 1'b1 : 1'b0;\n assign one = flip ? 1'b0 : 1'b1;\n  endmodule\n ",
            "error": "/tmp/tmp3jqe90x3/tmponn0nngb.v:10: syntax error\n/tmp/tmp3jqe90x3/tmponn0nngb.v:10: error: malformed statement"
        }
        }
    },
    {   // Código compila, não passa em nenhum teste
        "id": "1ed8b3c6-d683-4081-b369-512efe2eb573",
        "score": "0",
        "result": "wrong", // "right" | "wrong" | "partial"
        "feedback": {
            "1ed8b3c6-d683-4081-b369-512efe2eb573": {
                "message": "Erro do teste sum: esperado x obtido y! (50)",
                    "dump": {
                    "config": {
                        "hscale": 1
                    },
                    "signal": [
                        {
                            "data": [],
                            "name": "tb_top0.zero",
                            "wave": "01"
                        },
                        {
                            "data": [],
                            "name": "tb_top0.flip",
                            "wave": "01"
                        },
                        {
                            "data": [],
                            "name": "tb_top0.dut.one",
                            "wave": "10"
                        }
                    ]
                }
            },
            "1ed8b3c6-d683-4081-b369-512efe2eb575": {
                "message": "Erro do teste cout: esperado x obtido y! (0)",
                "dump": {
                    "config": {
                        "hscale": 1
                    },
                    "signal": [
                        {
                            "data": [],
                            "name": "tb_top0.zero",
                            "wave": "01"
                        },
                        {
                            "data": [],
                            "name": "tb_top0.flip",
                            "wave": "01"
                        },
                        {
                            "data": [],
                            "name": "tb_top0.dut.one",
                            "wave": "10"
                        }
                    ]
                }
            }
        }
    },
    {   // Código compila, passa em apenas um teste
        "id": "1ed8b3c6-d683-4081-b369-512efe2eb573",
        "score": "50",
        "result": "partial", // "right" | "wrong" | "partial"
        "feedback": {
            "1ed8b3c6-d683-4081-b369-512efe2eb573": {
                "message": "Sucesso do teste sum! (50)",
                "dump": {
                    "config": {
                        "hscale": 1
                    },
                    "signal": [
                        {
                            "data": [],
                            "name": "tb_top0.zero",
                            "wave": "01"
                        },
                        {
                            "data": [],
                            "name": "tb_top0.flip",
                            "wave": "01"
                        },
                        {
                            "data": [],
                            "name": "tb_top0.dut.one",
                            "wave": "10"
                        }
                    ]
                }
            },
            "1ed8b3c6-d683-4081-b369-512efe2eb575": {
                "message": "Erro do teste cout: esperado x obtido y! (0)",
                "dump": {
                    "config": {
                        "hscale": 1
                    },
                    "signal": [
                        {
                            "data": [],
                            "name": "tb_top0.zero",
                            "wave": "01"
                        },
                        {
                            "data": [],
                            "name": "tb_top0.flip",
                            "wave": "01"
                        },
                        {
                            "data": [],
                            "name": "tb_top0.dut.one",
                            "wave": "10"
                        }
                    ]
                }
            }
        }
    },
    {   // Código compila, passa em todos os testes
        "id": "1ed8b3c6-d683-4081-b369-512efe2eb573",
        "score": "100",
        "result": "right", // "right" | "wrong" | "partial"
        "feedback": {
            "1ed8b3c6-d683-4081-b369-512efe2eb573": {
                "message": "Sucesso do teste sum! (50)",
                "dump": {
                    "config": {
                        "hscale": 1
                    },
                    "signal": [
                        {
                            "data": [],
                            "name": "tb_top0.zero",
                            "wave": "01"
                        },
                        {
                            "data": [],
                            "name": "tb_top0.flip",
                            "wave": "01"
                        },
                        {
                            "data": [],
                            "name": "tb_top0.dut.one",
                            "wave": "10"
                        }
                    ]
                }
            },
            "1ed8b3c6-d683-4081-b369-512efe2eb575": {
                "message": "Sucesso do teste cout! (50)",
                "dump": {
                    "config": {
                        "hscale": 1
                    },
                    "signal": [
                        {
                            "data": [],
                            "name": "tb_top0.zero",
                            "wave": "01"
                        },
                        {
                            "data": [],
                            "name": "tb_top0.flip",
                            "wave": "01"
                        },
                        {
                            "data": [],
                            "name": "tb_top0.dut.one",
                            "wave": "10"
                        }
                    ]
                }
            }
        }
    }
] Response Code 200

// Erro: Nenhuma tentativa aberta
{
    "feedback": "Usuario não tem nenhuma tentativa aberta"
} Response Code 400
```

# Checar questão de verilog

    [POST] /userquizquestionanswer/check   
Faz a verificação de uma questão verilog

```json
// request
{
    "id_quiz": "1028d586-09e5-4641-af5a-05728a7928e7",
    "id_question": "8a5940ea-3ac4-4f3f-80dd-6fbe6cc17005",
    "text_answer": "module top (\n    input flip,\n    output zero, one\n);\n    // Pro mode stuff\n assign zero = flip;\n    assign one = ~flip;\nendmodule"
}

// response
[
    {
        "score": 100,
        "result": "right",
        "feedback": {
            "da35d64d-1773-4685-8c95-aea173c2f36b": {
                "message": "Sucesso no teste TB0! (50)",
                "dump": {
                    "config": {
                        "hscale": 1
                    },
                    "signal": [
                        {
                            "data": [],
                            "name": "tb_top0.zero",
                            "wave": "01"
                        },
                        {
                            "data": [],
                            "name": "tb_top0.flip",
                            "wave": "01"
                        },
                        {
                            "data": [],
                            "name": "tb_top0.dut.one",
                            "wave": "10"
                        }
                    ]
                }
            },
            "a2cbc8a0-4f1c-49d9-bf4e-edc4f458b1c4": {
                "message": "Sucesso no teste TB1! (50)",
                "dump": {
                    "config": {
                        "hscale": 1
                    },
                    "signal": [
                        {
                            "data": [],
                            "name": "tb_top1.one",
                            "wave": "10"
                        },
                        {
                            "data": [],
                            "name": "tb_top1.flip",
                            "wave": "01"
                        },
                        {
                            "data": [],
                            "name": "tb_top1.dut.zero",
                            "wave": "01"
                        }
                    ]
                }
            }
        }
    }
] Response Code 200

-----------------------------------------------------------------------------------------------
[    // Caso a requisição não enviar uma informação esperada
    "id_question": [
        "This field is required."
    ]
] Response Code 400

-----------------------------------------------------------------------------------------------
[    // Caso a questão enviada não seja uma questão de verilog
    {
        'feedback': "A questão não é do tipo Verilog"
    }
] Response Code 400
```
