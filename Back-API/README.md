#  Documentação das APIs

Seguir **estritamente** o padrão a seguir!

Todas as rotas protegidas levam no cabecalho da requisição (`Authorization`) o access token no padráo `Bearer: token`

Lista de **rotas não protegidas**:

      [POST] /auth/login  
      [POST] /auth/register  
      [POST] /auth/forgot-password-request

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
        [POST] /user       // para importação de usuários
         [PUT] /user/{id}  
      [DELETE] /user/{id}  

- [**Course:**](./Course.md)  

         [GET] /course  
         [GET] /course/{id}  
        [POST] /course  
         [PUT] /course/{id}  
      [DELETE] /course/{id}  

        [POST] /course/{id}/users  

- [**Post:**](./Post.md)

         [GET] /post  
         [GET] /post/{id}  
        [POST] /post  
         [PUT] /post/{id}  
      [DELETE] /post/{id}  

        [POST] /post/user/{idUser}  
        [POST] /post/course/{idCourse}  
        [POST] /post/question/{idQuestion}  

- [**Question:**](./Question.md)  

         [GET] /question    
         [GET] /question/{id}  
        [POST] /question  
         [PUT] /question/{id}  
      [DELETE] /question/{id}  

- [**Category:**](./Category.md)  

         [GET] /category  
         [GET] /category/{id}  
        [POST] /category  
         [PUT] /category/{id}  
      [DELETE] /category/{id} 
