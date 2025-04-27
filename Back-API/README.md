#  Documentação das APIs

1. Seguir **estritamente** o padrão a seguir! 
2. Se for implementar algo que não está descrito aqui, por favor, estabeleça o padrão e descreva aqui como implementou.
3. Se não entendeu alguma coisa, pergunte!  

Todas as rotas protegidas levam no cabecalho da requisição (`Authorization`) o access token no padráo `Bearer: token`

Lista de **rotas não protegidas**:

      [POST] /auth/login  
      [POST] /auth/register  
      [POST] /auth/forgot-password-request
       [GET] /auth/reset-password/{codigo_de_verificacao}  
       [GET] /auth/confirm-email/{codigo_de_verificacao}  

##  Endpoints

- **Swagger:**
  
      /docs

- [**Auth:**](./Auth.md)
  
      [POST] /auth/login  
      [POST] /auth/logout  
      [POST] /auth/self-register  
      [POST] /auth/forgot-password-request
      [POST] /auth/token/refresh  
       [GET] /auth/reset-password/{codigo_de_verificacao}  
       [GET] /auth/confirm-email/{codigo_de_verificacao}  

- [**User:**](./User.md)
  
         [GET] /user        // ver todos os usuarios
        [POST] /user        // para importação de usuários (recebe um arquivo .csv)
         [GET] /user/{id}   // ver informações de um usuario especifico
         [PUT] /user/{id}   // atualizar senha de um usuário
       [PATCH] /user/{id}   // atualizar informações de um usuário
      [DELETE] /user/{id}   // remover um usuario

         [GET] /user/ranking/{quantidade}  // ver rank de usuarios do site
         [GET] /user/course/{idCourse}     // usuários de um curso  

- [**Course:**](./Course.md)  

         [GET] /course       // ver todos os cursos
         [GET] /course/{id}  // ver um curso especifico
        [POST] /course       // cadastrar curso
         [PUT] /course/{id}  // atualizar informações de um curso
      [DELETE] /course/{id}  // remover um curso
  
         [GET] /course/ranking/{quantidade}  // visualizar ranking de usuarios no curso
         [GET] /course/user/{idUser}         // ver cursos de um usuário  

- [**UserCourse:**](./UserCourse.md)  

         [GET] /usercourse/{idUser}/{idCourse}  // ver informações de um usuario em um curso
        [POST] /usercourse                      // cadastrar um usuario em um curso
         [PUT] /usercourse/{idUser}/{idCourse}  // atualizar cadastro de um usuario em um curso
      [DELETE] /usercourse/{idUser}/{idCourse}  // remover usuario de um curso

- [**Quiz:**](./Quiz.md)  

         [GET] /quiz/{id}  // ver um questionario especifico
        [POST] /quiz       // cadastrar um questionario
         [PUT] /quiz/{id}  // atualizar um questionario
      [DELETE] /quiz/{id}  // remover um querionario

         [GET] /quiz/course/{idCourse}  // ver questionários de um curso   

- [**Category:**](./Category.md)  

         [GET] /category/{id}  // ver categoria pelo id
        [POST] /category       // cadastrar categoria
         [PUT] /category/{id}  // atualizar informações de uma categoria
      [DELETE] /category/{id}  // remover uma categoria

         [GET] /category/course/{idCourse}      // ver categorias de um curso
         [GET] /category/category/{idCategory}  // ver sub-categorias de uma categoria
  
- [**Question:**](./Question.md)  

         [GET] /question/{id}  // ver uma questão especifica
        [POST] /question       // cadastrar uma questão
         [PUT] /question/{id}  // atualizar uma questão
      [DELETE] /question/{id}  // remover uma questão especifica

         [GET] /question/quiz/{idQuiz}          // ver questões de um questionário  
         [GET] /question/category/{idCategory}  // ver questões de uma categoria  

- [**Post:**](./Post.md)

         [GET] /post/{id}  // ver uma postagem especifica
        [POST] /post       // enviar uma postagem
         [PUT] /post/{id}  // atualizar uma postagem
      [DELETE] /post/{id}  // remover uma postagem especifica

         [GET] /post/user/{idUser}          // posts de um usuário  
         [GET] /post/course/{idCourse}      // posts de um curso   
         [GET] /post/question/{idQuestion}  // posts de uma questão  

- [**QuizQuestion:**](./QuizQuestion.md)  

         [GET] /quizquestion/{idQuiz}/{idQuestion}  // ver informações de uma questão em um quiz
        [POST] /quizquestion                        // cadastrar uma questão em um quiz
         [PUT] /quizquestion/{idQuiz}/{idQuestion}  // atualizar informações de uma questão em um quiz
      [DELETE] /quizquestion/{idQuiz}/{idQuestion}  // remover uma questão de um quiz

- [**Answer:**](./Answer.md)  

         [GET] /answer/{id}  // ver uma resposta especifica
        [POST] /answer       // cadastrar uma resposta
         [PUT] /answer/{id}  // atualizar uma resposta
      [DELETE] /answer/{id}  // remover uma resposta especifica

         [GET] /answer/question/{idQuestion}  // ver as respostas de uma questão

- [**UserQuizQuestionAnswer:**](./UserQuizQuestionAnswer.md)  

         [GET] /userquizquestionanswer/{id}      // ver uma resposta especifica de algum usuario em alguma questão pelo id
        [POST] /userquizquestionanswer           // enviar a resposta de um usuario para uma questão
         [PUT] /userquizquestionanswer/{id}      // atualizar uma resposta especifica de algum usuario em alguma questão pelo id
      [DELETE] /userquizquestionanswer/{id}      // remover uma resposta especifica de algum usuario em alguma questão pelo id

         [GET] /userquizquestionanswer/quiz/{idQuiz}                          // ver respostas de um usuário em um questionário
         [GET] /userquizquestionanswer/quizquestion/{idQuiz}/{idQuestion}     // ver resposta de um usuário em uma questão de um questionário

##  Teste com Postman
- [**Authentication**](./Authentication.md)  
