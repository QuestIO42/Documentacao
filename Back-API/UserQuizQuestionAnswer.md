# API Respostas dos usuários

  [POST] /userquizquestionanswer    

Salva a resposta de um usuário a uma questão aberta.

```json
// request
{
    "id_user": "1ed8b3c6-d683-4081-b369-512efe2eb573",
    "id_quiz": "1ed8b3c6-d683-4081-b369-512efe2eb573",
    "id_question": "1ed8b3c6-d683-4081-b369-512efe2eb573",
    "id_answer": "", // empty or omit 
    "text_answer": "Pedro Álvares Cabral",
}
// response
{
    "id": "1ed8b3c6-d683-4081-b369-512efe2eb573",
    "score": "100"
    "result": "right" // "right" | "wrong" | "partial"
},
```
