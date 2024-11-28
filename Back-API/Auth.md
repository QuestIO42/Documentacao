# API Autenticação

    [POST] /auth/login

```json
// request
{
    "login": "username ou email",
    "password": "secret123"
}
// response
{
    "access": "JWTeyJhbGciOiJIUzI1NiIsInR5cCI6IkpX",
    /* token content

    "sub": "1ed8b3c6-d683-4081-b369-512efe2eb573", // id
    "user_role": "STUDENT",
    "iat": 1516239022
    "exp": 5162390221 // 1 minuto
    "type": "access"
    */
    "refresh": "JWTeyJhbGciOiJIUzI1NiIsInR5cCI6IkpX",
    /* token content

    "sub": "1ed8b3c6-d683-4081-b369-512efe2eb573", // id
    "user_role": "STUDENT",
    "iat": 1516239022
    "exp": 5162390221 // 7 dias
    "type": "refresh"
    */
}
```

    [POST] /auth/logout  

```json
//além do request, o front deve apagar os tokens de access e refresh

// request
{}

// response
http status 204
{}
```


    [POST] /auth/self-register  


```json
// request
{
    "full_name" : "Joao da Silva",
    "username" : "123321",
    "email" : "asd@asd.com",
    "password" : "secret123"
}

// response
http status code 201
{}
```

    [POST] /auth/token/refresh  

```json
// request
{
        "refresh": "JWTeyJhbGciOiJIUzI1NiIsInR5cCI6IkpX"

},
// response
{
        "access": "JWTasdasciOiJIUzI1NiIsInR5cCI6IkpX"

}
```


    [POST] /auth/forgot-password-request

Esta rota não deve fornecer a informação sobre a existência do cadastro do usuário e não deve alterar sua senha no banco, apenas o campo `verificationCode` na tabela do usuário. Deve responder apenas: **Se este e-mail estiver cadastrado no sistema, você receberá uma mensagem com instruções para configurar uma nova senha**.

```json
// request
{
   "email" : "email"
}

// response
http status code 200
{}
```

    [GET] /auth/reset-password/{codigo_de_verificacao}    

Esta rota confere se o código de verificação do usuário existe e retorna os tokens (mesmo padrão de login). O front obtem seu ID do token e redireciona para a página de configurar uma nova senha (`change-password`), que por sua vez apontará para `[PUT] /user/{id}`.

```json
// response
http status code 200
{
    "token" : "@#$@#SFDFDGGHS#$$%%^"
}
```


     [GET] /auth/confirm-email/{codigo_de_verificacao}  

```json
// response
http status code 200
{}
```
