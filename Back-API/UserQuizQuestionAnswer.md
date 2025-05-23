# API Respostas dos usuários

    [POST] /userquizquestionanswer    

Usuario envia resposta sem ter mais tentativas a se realizar.

```json
// request
{
    "id_user": "1ed8b3c6-d683-4081-b369-512efe2eb573",
    "id_quiz": "2ed8b3c6-d683-4081-b369-512efe2eb573",
    "id_question": "3ed8b3c6-d683-4081-b369-512efe2eb573",
    "id_answer": "", // empty or omit 
    "text_answer": "Pedro Álvares Cabral",
}
// response
{
    "feedback": "Sem tentativas possíveis, já foram realizadas 3/3 tentativas",
    "current_try": 4,
    "quiz_tries": 3,
},
```

Envia e salva a resposta de um usuário a uma questão aberta. Recebe o retorno para exibição assíncrona ao usuário.

```json
// request
{
    "id_user": "1ed8b3c6-d683-4081-b369-512efe2eb573",
    "id_quiz": "2ed8b3c6-d683-4081-b369-512efe2eb573",
    "id_question": "3ed8b3c6-d683-4081-b369-512efe2eb573",
    "id_answer": "", // empty or omit 
    "text_answer": "Pedro Álvares Cabral",
}
// response
{
    "id": "1ed8b3c6-d683-4081-b369-512efe2eb573",
    "score": "100"
    "result": "right" // "right" | "wrong" | "partial"
    "feedback": "Well done!" // this is optional 
},
```
Envia e salva a resposta de um usuário a uma questão de múltipa escolha. Recebe o retorno para exibição assíncrona ao usuário.

```json
// request
{
    "id_user": "4ed8b3c6-d683-4081-b369-512efe2eb573",
    "id_quiz": "5ed8b3c6-d683-4081-b369-512efe2eb573",
    "id_question": "6ed8b3c6-d683-4081-b369-512efe2eb573",
    "id_answer": "7ed8b3c6-d683-4081-b369-512efe2eb573",  
    "text_answer": "", // empty or omit 
}
// response
{
    "id": "1ed8b3c6-d683-4081-b369-512efe2eb573",
    "score": "100"
    "result": "right" // "right" | "wrong" | "partial"
},
```
Envia e salva a resposta de um usuário a uma questão de Verilog. Recebe o retorno para exibição assíncrona ao usuário.

### Erro de sintaxe

```json
// request
{
    "id_user": "4ed8b3c6-d683-4081-b369-512efe2eb573",
    "id_quiz": "5ed8b3c6-d683-4081-b369-512efe2eb573",
    "id_question": "6ed8b3c6-d683-4081-b369-512efe2eb573",
    "id_answer": "", // empty or omit 
    "text_answer": "module top()\n endmodula;", 
}
// response
{
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
```

### Código compila, não passa em nenhum teste

```json
// request
{
    "id_user": "4ed8b3c6-d683-4081-b369-512efe2eb573",
    "id_quiz": "5ed8b3c6-d683-4081-b369-512efe2eb573",
    "id_question": "6ed8b3c6-d683-4081-b369-512efe2eb573",
    "id_answer": "", // empty or omit 
    "text_answer": "module top()\n endmodule;", 
}
// response
{
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
    }},
```

### Código compila, passa em apenas um teste

```json
// request
{
    "id_user": "4ed8b3c6-d683-4081-b369-512efe2eb573",
    "id_quiz": "5ed8b3c6-d683-4081-b369-512efe2eb573",
    "id_question": "6ed8b3c6-d683-4081-b369-512efe2eb573",
    "id_answer": "", // empty or omit 
    "text_answer": "module top(input x, y, cin, output sum)\n assign sum = x ^ y ^ cin;\n endmodule;", 
}
// response
{
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
```

### Código compila, passa em todos os testes

```json
// request
{
    "id_user": "4ed8b3c6-d683-4081-b369-512efe2eb573",
    "id_quiz": "5ed8b3c6-d683-4081-b369-512efe2eb573",
    "id_question": "6ed8b3c6-d683-4081-b369-512efe2eb573",
    "id_answer": "", // empty or omit 
    "text_answer": "module top(input x, y, cin, output sum, cout)\n assign sum = x ^ y ^ cin;\n assign cout = x&y|x&cin|y&cin;\n endmodule;", 
}
// response
{
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
```

