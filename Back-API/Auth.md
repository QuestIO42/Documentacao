# API Autenticação

Seguir **estritamente** o padrão a seguir:


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
{
}
```

    [POST] /auth/token/refresh  

```json
//request
{
        "refresh": "JWTeyJhbGciOiJIUzI1NiIsInR5cCI6IkpX"

},
//response
{
        "access": "JWTasdasciOiJIUzI1NiIsInR5cCI6IkpX"

}
```
    [POST] /auth/logout  

```json
//além do request, no front apagar os tokens de access e refresh
//request
{
    "access": "JWTasdasciOiJIUzI1NiIsInR5cCI6IkpX"
}

//response
http status 204
{

}
```

    [POST] /auth/forgot-password-request

```json
//request
{
   "email" : "email"
}

//response
http status 200
{}
```

    [GET] /auth/reset-password  

```json
{
    "token" : "@#$@#SFDFDGGHS#$$%%^",
    "newPassword" : "secret123"
    
}
```


     [GET] /auth/confirm/{codigo_de_verificacao}  

```json
{
    
}
```
