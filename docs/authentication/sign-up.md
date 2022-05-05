---
sidebar_position: 1
---
# Регистрация

<pre>
<b>POST</b> v1/sign-up
</pre>

Служит для регистрации новых пользователей.

### Request body
| Syntax                                    | Description                                                   |
| ----------------------------------------- | ------------------------------------------------------------- |
| client_id <font color="red">*</font>      | Идентификатор клиента                                         |
| email  <font color="red">*</font>         | Почтовый адрес пользователя                                   |
| password  <font color="red">*</font>      | Пароль пользователя                                           |
| connection  <font color="red">*</font>    | Название необходимой базы данных                              |

### Response
```
{
  key: value
}
```