# API Respostas dos usuários

# Criar Questionario
    [POST] /userquizquestionanswer    

Cria as questoes de um questionario para um usuário.
Se houver um questionario não enviado, respondera com um erro dizendo a tentativa atual aberta.
```json
// request
{
    "id_user": "321372b4-8631-4fef-9fc0-c961952239f1",
    "id_quiz": "7ab20845-69ee-45ae-a768-3339890f6a9b",
}

// responses
[   //cria as perguntas do questionario
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
--------------------------------------------------------------------
{   //quando o usuario ja tem um questionario aberto
    "feedback": "O usuário ainda está com o quiz em andamento",
    "current_try": 1
} Response Code 400
```
# Get Questionario
    [GET] /userquizquestionanswer/quiz/{id_quiz}

Retorna os objetos de resposta do questionario do usuario em uma tentativa.
```json
// request
{
    "id_user": "321372b4-8631-4fef-9fc0-c961952239f1",
    "current_try": 1
}
// response
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

# Responder Questão

    [PUT] /userquizquestionanswer/<uuid:pk>

Altera o objeto de resposta do questionario do usuario. Deve ser usado para alterar as respostas de uma questão. Os campos são opcionais.

Essa rota não corrige as respostas, apenas altera o objeto de resposta. Para corrigir as respostas, use a rota de enviar questionario.
```json 
{
    "text_answer": "Resposta do usuario", // resposta discursiva e de verilog
    "id_answer": "7a7796c0-978b-4871-805a-1d9e622bbc23" // resposta multipla escolha
}
// response
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

# Enviar Questionario

    [POST] /userquizquestionanswer/send   
Envia e salva as respostas de um usuário em um quiz. Responde uma lista com os resultados de cada questão. Retorna um erro caso o usuário não tenha um quiz aberto.

```json
// request
{
    "id_user": "321372b4-8631-4fef-9fc0-c961952239f1",
    "id_quiz": "7ab20845-69ee-45ae-a768-3339890f6a9b",
}
// response

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
        "score": "0"
        "result": "wrong" // "right" | "wrong" | "partial"
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
            "dump": "{
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
        "score": "50"
        "result": "partial" // "right" | "wrong" | "partial"
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
        "score": "100"
        "result": "right" // "right" | "wrong" | "partial"
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
    },
] Response Code 200
-----------------------------------------------------------------------------------------------
{   // Quando o usuario não tem um quiz aberto
    "feedback": "Usuario não tem nenhuma tentativa aberta"
} Response Code 400
```

