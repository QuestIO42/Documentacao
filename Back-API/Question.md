# API Questões

         [GET] /question/quiz/{idQuiz}  // questões de um questionário  

Retorna todos as questões de um questionário. 

```json
// request
{}
// response
[
    {
        "id": "1ed8b3c6-d683-4081-b369-512efe2eb573",
        "name": "Introdução", 
        "type": "CONTENT", // só leitura
        "responsible": "False",
        "content": "Isso é apenas um conteúdo introdutório, não é preciso responder nada.\n
                    # Markdown\n
                    Será possível usar Markdown aqui?",
    },
    {
        "id": "4a870aca-072c-4fbc-9f5d-20490f8fe19c",
        "name": "Máquinas de Estado Finito", 
        "type": "CHOICE", // Múltipla escolha
        "responsible": "True",
        "content": "Selecione a opção que mais lhe apetecer. Que máquina é essa?",
    },
    {
        "id": "7a870aca-072c-4fbc-9f5d-20490f8fe19d",
        "name": "Máquinas de Estado Finito", 
        "type": "OPEN", // Resposta aberta
        "responsible": "True",
        "content": "Explique o que é uma FSM",
    },
    {
        "id": "0a870aca-072c-4fbc-9f5d-20490f8fe19a",
        "name": "Máquinas de Estado Finito", 
        "type": "CODE", // Verilog
        "responsible": "True",
        "content": "Forneça o um código de uma FSM...",
    },
]
```