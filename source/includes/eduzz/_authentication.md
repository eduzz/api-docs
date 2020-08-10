# Autenticação

A API da Eduzz usa Oauth2 como meio de autenticação.

Para gerar o token siga o fluxo abaixo

1. Redirecione o usuário para o endpoint de autorização, passando o seu id de aplicativo (appId) e a URL de retorno (redirectUrl).

```
https://accounts.eduzz.com/oauth/authorize?client_id={appId}&redirect_uri={redirectUrl}
```

2. Após o usuário autorizar seu aplicativo, o sistema irá redirecioná-lo para o seu site, ex:

```
{redirectUrl}?code=the_authorization_code
```

3. Para terminar o fluxo de autenticação, você precisará enviar uma requisição para a api do Eduzz accounts enviando o code, seu id de aplicativo (appId) e o seu secret (appSecret)

```
POST: https://accounts-api.eduzz.com/oauth/token

Body: {
  "client_id": "{appId}",
  "client_secret": "appSecret",
  "code": "{code}",
  "grant_type": "authorization_code"
}
```

4. Após este envio você receberá uma resposta contento um token que deverá ser armazenado em sua base de dados e utilizado para obter os dados do cliente. ex:

```
{
    "token_type": "bearer",
    "access_token": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
    "user": {
        "id": "ffffffff-ffff-ffff-ffff-e1102821d3ef",
        "eduzzId": 0,
        "nutrorId": 0,
        "name": "Fulano da Silva",
        "email": "fulano@ciclano.com"
    }
}
```
