---
sidebar_position: 2
---
# Авторизация
Служит для авторизации пользователей через стандартную форму BearLogin, которую вы можете
изменять без изменения кода.

<pre>
  <b>GET</b> v1/authorize
</pre>


### Параметры запроса
<table>
  <thead>
    <th>Поле</th>
    <th>Описание</th>
  </thead>

  <tbody>
   <tr>
      <td>redirect_uri<font color="red">*</font></td>
      <td>URL на который произойдет редирект после успешной авторизации</td>
    </tr>
  </tbody>
</table>

### Результат ответа
После успешной авторизации вернется статус `301`, произойдет redirect на указанный вами в параметрах `redirect_uri` и будут установлены соответствующие <a href="https://en.wikipedia.org/wiki/HTTP_cookie" rel="noreferrer" target="_blank">HTTP Cookie</a>



# Кастомная форма авторизации

<pre>
<b>GET</b> v1/authorize
</pre>

Используйте данный способ авторизации в том случае, если есть необходимость внедрения авторизации в свое приложение, не используя при этом редиректы и открытие новых окон.

### Параметры запроса
<table>
  <thead>
    <th>Поле</th>
    <th>Описание</th>
  </thead>

  <tbody>
    <tr>
      <td>
        mode
        <font color="red">*</font>
      </td>
      <td>Следует указать как <code>manual</code></td>
    </tr>
    <tr>
      <td>
        formName
        <font color="red">*</font>
      </td>
      <td>Следует указать наименование формы. К примеру <code>signIn</code> или <code>signUp</code></td>
    </tr>
  </tbody>
</table>

### Результат ответа
```
{
  form: {
    name: string,
    fields: Array<{
      name: "fieldName",
      attributes?: {
        min?: number,
        max?: number,
        regExp?: "/\+/"
      }
    }>
  }
}
```

:::info
Имена вложенных полей будут описаны в следующем формате `fieldA.nestedKeyB`
:::

После получения следующих полей, следует отрисовать форму, а затем выполнить следующий шаг:

<pre>
<b>POST</b> v1/authorize
</pre>

### Тело запроса
```
{
  form: {
   name: string,
   fields: {
      "fieldName": "fieldValue"
   }
  }
}
```

### Результат ответа
После успешной авторизации вернется статус `200` и будут установлены соответствующие <a href="https://en.wikipedia.org/wiki/HTTP_cookie" rel="noreferrer" target="_blank">HTTP Cookie</a>
