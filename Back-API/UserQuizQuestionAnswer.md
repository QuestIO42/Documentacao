# API Respostas dos usuários

    [POST] /userquizquestionanswer    

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
    "feedback": "Erro de sintaxe: Linha 2: endmodula... "
},
```

