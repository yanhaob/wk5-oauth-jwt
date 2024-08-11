# wk5-oauth-jwt
- https://github.com/lenve/oauth2-samples
- https://www.javaboy.org/2020/0424/github-oauth2.html
- https://www.javaboy.org/2020/0421/oauth2-jwt.html

Task1 is to setup OAuth authorization for Github and use Github's token as the user's basic identifier. Task2 is to setup JWT authentication: the front-end first carries a token in the header of each HTTP request, then the back-end verifies the validity period and legitimacy of the jwt token.

## OAuth

**Step1**, register a new OAuth application on Github ([Register Here](https://github.com/settings/applications/new)), configure as in the Fig.1 below.

<div style="text-align: center;">
    <img src="./img/github.png" alt="github" width="50%">
    <p style="margin: 0;">Fig.1 Oauth Setup</p>
</div>

**Step2**, cd github\_login to input your client\_id and client\_secret from above to the file IndexController.java, and run GithubLoginApplication.java, as followed by the Fig.2 below.

<div style="text-align: center;">
    <img src="./img/oauth.png" alt="oauth" width="100%">
    <p style="margin: 0;">Fig.2 OAuth Running</p>
</div>

**Step3**, save the token "gho\_4Oq7GdSAxwm7Z8ZZdz2tLKFK7peTcB3H2qdr" from above to enter it on [Postman](https://web.postman.co/workspace/My-Workspace~17dec501-2190-4fb7-8a43-d6953248e8f0/request/create?requestId=9d501966-0a07-471c-ae0f-5ca786e0ff62), and configure as in the Fig.3 below. Click "Send".
<div style="text-align: center;">
    <img src="./img/oauth-res.png" alt="oauth-res" width="100%">
    <p style="margin: 0;">Fig.3 OAuth Result</p>
</div>

## JWT
**Step1**, POST  on [Postman](https://web.postman.co/workspace/My-Workspace~17dec501-2190-4fb7-8a43-d6953248e8f0/request/create?requestId=9d501966-0a07-471c-ae0f-5ca786e0ff62) by the following command:
```sh
http://localhost:8080/oauth/token?client_id=yanhaob&client_secret=yanhaob&username=yanhaob&password=yanhaob&grant_type=password
```
then we have the encoded jwt token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOlsicmVzMSJdLCJ1c2VyX25hbWUiOiJ5YW5oYW9iIiwic2NvcGUiOlsiYWxsIl0sImFjdGl2ZSI6dHJ1ZSwiZXhwIjoxMDUyNzA2NjAyLCJhdXRob3JpdGllcyI6WyJST0xFX3VzZXIiXSwianRpIjoiYmMyMzFkODktZjMwNC00M2JiLTlkZjItNTAyYTMxZWRkMjVhIiwiY2xpZW50X2lkIjoieWFuaGFvYiJ9.JF-uCMz5owNw9x9MxanA7jSniFgiARBBVSDQ\_GzWU6E

**Step2**, decode by [JWT](https://jwt.io/) then we have the decoded jwt token: 
```sh
{
  "aud": [
      "res1"
  ],
  "user_name": "yanhaob",
  "scope": [
      "all"
  ],
  "active": true,
  "exp": 1052706602,
  "authorities": [
      "ROLE_user"
  ],
  "jti": "bc231d89-f304-43bb-9df2-502a31edd25a",
  "client_id": "yanhaob"
}
```

**Step3**, GET on [Postman](https://web.postman.co/workspace/My-Workspace~17dec501-2190-4fb7-8a43-d6953248e8f0/request/create?requestId=9d501966-0a07-471c-ae0f-5ca786e0ff62) by the following command:
```sh
http://localhost:8081/hello
```
and configure as in the Fig.4 below. Click "Send".
<div style="text-align: center;">
    <img src="./img/jwt-res.png" alt="jwt-res" width="100%">
    <p style="margin: 0;">Fig.4 JWT Result</p>
</div>

