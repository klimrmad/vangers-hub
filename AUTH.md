# Регистрация и авторизация

Для регистрации используйте `API_KEY` hub-а: `AIzaSyCBIQuVs-kSfn_zntT4rfpjdyXmr5_nzL4`.

---

## Анонимная учетная запись

[API docs](https://firebase.google.com/docs/reference/rest/auth#section-sign-in-anonymously)

    wget --no-check-certificate --method POST \
      --header 'Content-Type: application/json' \
      --body-data '{"returnSecureToken":true}' \
       'https://identitytoolkit.googleapis.com/v1/accounts:signUp?key={API_KEY}'

Ответ будет содержать следующие поля:

 - `localId`— UID созданного пользователя. Это и будет UID сервера.
 - `idToken` — Auth ID token. Используется для выполнения запросов (таймаут 3600 секунд).
 - `refreshToken` — Auth refresh token. Используется для обновления Auth ID token.

Залогиниться повторно в такую учетную запись нельзя. 
Вам нужно будет сохранять `refreshToken` и использовать его для получения свежего `idToken`.
  
## Персонализированная учетная запись

[API docs](https://firebase.google.com/docs/reference/rest/auth#section-create-email-password)

    wget --no-check-certificate --method POST \
      --header 'Content-Type: application/json' \
      --body-data '{"email":"{EMAIL}","password":"{PASSWORD}","returnSecureToken":true}' \
       'https://identitytoolkit.googleapis.com/v1/accounts:signUp?key={API_KEY}'

Ответ аналогичен анонимной регистрации.

В такую учетную запись можно залогиниться с учетными данными, указанными при регистрации. 
Также можно сохранять `refreshToken` и использовать его для получения свежего `idToken`. 

## Авторизация с email и password

[API docs](https://firebase.google.com/docs/reference/rest/auth#section-sign-in-email-password)

    wget --no-check-certificate --method POST \
      --header 'Content-Type: application/json' \
      --body-data '{"email":"{EMAIL}","password":"{PASSWORD}","returnSecureToken":true}' \
       'https://identitytoolkit.googleapis.com/v1/accounts:signInWithPassword?key={API_KEY}'

Ответ аналогичен запросам на регистрацию.
