# Autenticação no Postman

## 1. Criar uma Collection

1. Abra o Postman e crie uma **Collection**.
2. Na aba **"Pre-request Script"** da collection, cole o seguinte código:

```javascript
let host = pm.collectionVariables.get("host");
let username = pm.collectionVariables.get("username");
let password = pm.collectionVariables.get("password");

let body = JSON.stringify({
    "login": username,
    "password": password
})

const postRequest = {
    url: host + 'auth/login',
    method: 'POST',
    timeout: 0,
    header: {
    "Content-Type": "application/json",
    "Accept": "*/*"
    },
    body: body
};
pm.sendRequest(postRequest, function (err, res) {
    console.log("Login Response: ", res.json());
    if (err) console.log("Error: ", err)

    let authorization = res.json()["access"];

    pm.collectionVariables.set('authorization_token', authorization);
});
```

---

## 2. Definir Variáveis na Collection

Crie as seguintes variáveis na sua Collection (em "Variables"):

| Nome                  | Initial Value                       |
|-----------------------|-------------------------------------|
| `host`                | `https://django.vlab.dc.ufscar.br/` |
| `username`            | `seu_usuario`                       |
| `password`            | `sua_senha`                         |
| `authorization_token` | _Deixe vazio_                       |

---

## 3. Configurar Autorização

1. Ainda na sua Collection, vá até a aba **Authorization**.
2. Em **Type**, selecione **Bearer Token**.
3. No campo **Token**, insira a variável:  `{{authorization_token}}`
   

---

## ✅ Pronto!

Agora, todas as requisições feitas dentro da sua Collection já estarão autenticadas automaticamente. O token de acesso será incluído no header `Authorization` como um Bearer Token.
