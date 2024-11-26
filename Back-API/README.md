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
  
         [GET] /user  
         [GET] /user/{id}  
        [POST] /user         // para importação de usuários (recebe um arquivo .csv)
         [PUT] /user/{id}  
      [DELETE] /user/{id}  

         [GET] /user/course/{idCourse}  // usuários de um curso  

- [**Course:**](./Course.md)  

         [GET] /course  
         [GET] /course/{id}  
        [POST] /course  
         [PUT] /course/{id}  
      [DELETE] /course/{id}  

         [GET] /course/user/{idUser}  // cursos de um usuário  

- [**UserCourse:**](./UserCourse.md)  

         [GET] /usercourse/{idUser}/{idCourse}  
        [POST] /usercourse  
         [PUT] /usercourse/{idUser}/{idCourse}  
      [DELETE] /usercourse/{idUser}/{idCourse}  

- [**Quiz:**](./Quiz.md)  

         [GET] /quiz/{id}  
        [POST] /quiz  
         [PUT] /quiz/{id}  
      [DELETE] /quiz/{id}  

         [GET] /quiz/course/{idCourse}  // questionários de um curso   

- [**Category:**](./Category.md)  

         [GET] /category/{id}  
        [POST] /category  
         [PUT] /category/{id}  
      [DELETE] /category/{id}

         [GET] /category/course/{idCourse}  // categorias de um curso
         [GET] /category/category/{idCategory}  // sub-categorias de uma categoria
  
- [**Question:**](./Question.md)  

         [GET] /question/{id}  
        [POST] /question  
         [PUT] /question/{id}  
      [DELETE] /question/{id}  

         [GET] /question/quiz/{idQuiz}  // questões de um questionário  
         [GET] /question/category/{idCategory}  // questões de uma categoria  

- [**Post:**](./Post.md)

         [GET] /post/{id}  
        [POST] /post  
         [PUT] /post/{id}  
      [DELETE] /post/{id}  

         [GET] /post/user/{idUser}  // posts de um usuário  
         [GET] /post/course/{idCourse}  // posts de um curso   
         [GET] /post/question/{idQuestion}  // posts de uma questão  

- [**QuizQuestion:**](./QuizQuestion.md)  

         [GET] /quizquestion/{idQuiz}/{idQuestion}  
        [POST] /quizquestion  
         [PUT] /quizquestion/{idQuiz}/{idQuestion}  
      [DELETE] /quizquestion/{idQuiz}/{idQuestion}

- [**Answer:**](./Answer.md)  

         [GET] /answer/{id}  
        [POST] /answer  
         [PUT] /answer/{id}  
      [DELETE] /answer/{id}  

         [GET] /answer/question/{idQuestion}  // respostas de uma questão  

- [**UserQuizQuestionAnswer:**](./UserQuizQuestionAnswer.md)  

         [GET] /userquizquestionanswer/{id}  
        [POST] /userquizquestionanswer  
         [PUT] /userquizquestionanswer/{id}  
      [DELETE] /userquizquestionanswer/{id}  

         [GET] /userquizquestionanswer/quiz/{idQuiz}  // respostas de um usuário em um questionário
         [GET] /userquizquestionanswer/quizquestion/{idQuiz}/{idQuestion}  // resposta de um usuário em uma questão de um questionário

