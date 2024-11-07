#  Docs API

##  Endpoints

- **Swagger:**
  
      /docs

- [**User:**](./User.md)
  
         [GET] /user  
         [GET] /user/{id}  
        [POST] /user          // Os usuários são criados com os emails já validados
         [PUT] /user/{id}  
      [DELETE] /user/{id}  

- **Auth:**
  
        [POST] /auth/login  
        [POST] /auth/register  
        [POST] /auth/token/refresh  
        [POST] /auth/logout  
        [POST] /auth/forgot-password-request
         [GET] /auth/reset-password  
         [GET] /auth/confirm/{codigo_de_verificacao}  

- **Course:**  

         [GET] /course  
         [GET] /course/{id}  
        [POST] /course  
         [PUT] /course/{id}  
      [DELETE] /course/{id}  

        [POST] /course/{id}/users  

- **Post:**  

         [GET] /post  
         [GET] /post/{id}  
        [POST] /post  
         [PUT] /post/{id}  
      [DELETE] /post/{id}  

        [POST] /post/user/{idUser}  
        [POST] /post/course/{idCourse}  
        [POST] /post/question/{idQuestion}  

- **Question:**  

         [GET] /question    
         [GET] /question/{id}  
        [POST] /question  
         [PUT] /question/{id}  
      [DELETE] /question/{id}  

- **Category:**  

         [GET] /category  
         [GET] /category/{id}  
        [POST] /category  
         [PUT] /category/{id}  
      [DELETE] /category/{id} 
