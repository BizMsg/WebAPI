# 인증토큰 발급

{% swagger method="post" path="/v1/token" baseUrl="검수 or 운영 도메인" summary="인증 토큰 발급 요청" %}
{% swagger-description %}
API 서비스를 이용하기 위해서 인증 토큰을 발급하기 위한 기능입니다.

인증 토큰의 유효 시간은 24시간이며, 이후에는 사용이 불가하고 재발급이 필요합니다.

Authorization 헤더에 비즈뿌리오 계정과 암호를 Base64 인코딩한 문자열을 입력합니다.&#x20;
{% endswagger-description %}

{% swagger-parameter in="header" required="true" name="Authorization" type="" %}
Basic 계정:암호(Base64 인코딩)
{% endswagger-parameter %}

{% swagger-parameter in="header" required="true" name="Content-type" %}
application/json; charset=utf-8
{% endswagger-parameter %}

{% swagger-parameter in="body" name="accesstoken" type="" required="true" %}
인증 토큰
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="type" %}
Bearer
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="expired" %}
토큰 만료 시점
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
//headers
HTTP/1.1 200 OK
Content-type: application/json; charset=utf-8

//body
{
  "accesstoken": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJ2ZwxvcGVydC5jb20iLCJleHAiOiIxNDg1
  MjcwMDAwMDAwIiwiaHR0cHM6Ly92ZwxvcGVydC5jb20vand0X2NsYWltcy9pc19hZG1pbiI6dHJ1ZswidXNlcklk
  IjoiMTEwMjgzNzM3MjcxMDIiLCJ1c2VybmFtZSI6InZlbG9wZXJ0In0.WE5fMufM0NDSVGJ8cAolXGkyB5RmYwCto1
  pQwDIqo2w",
  "type": "Bearer", 
  "expired": "20201110185520"
}
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="설명" %}
**인증 토큰 발급 요청**

API 서비스를 이용하기 위해서 인증 토큰을 발급하기 위한 기능입니다.

인증 토큰의 유효 시간은 24시간이며, 이후에는 사용이 불가하고 재발급이 필요합니다.

Authorization 헤더에 비즈뿌리오 계정과 암호를 Base64 인코딩한 문자열을 입력합니다.
{% endtab %}

{% tab title="Request" %}
**Headers**\


|       키       |   타입   |                설명               |
| :-----------: | :----: | :-----------------------------: |
| Authorization | String |     Basic 계정:암호(Base64 인코딩)     |
|  Content-type | String | application/json; charset=utf-8 |
{% endtab %}

{% tab title="Response" %}
**Response**

|      키      |   타입   |                설명               |
| :---------: | :----: | :-----------------------------: |
| accesstoken | String |     Basic 계정:암호(Base64 인코딩)     |
|     type    | String | application/json; charset=utf-8 |
|   expired   | String |             토큰 만료 시점            |
{% endtab %}
{% endtabs %}

### **Request**

**Headers**

```http
POST /v1/token HTTP/1.1
Authorization: Basic Base64(계정:암호)
Content-type: application/json; charset=utf-8
```

### **Response**

**Headers**

```http
HTTP/1.1 200 OK
Content-type: application/json; charset=utf-8
```

**Body**

```json5
{
  "accesstoken": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJ2ZwxvcGVydC5jb20iLCJleHAiOiIxNDg1
  MjcwMDAwMDAwIiwiaHR0cHM6Ly92ZwxvcGVydC5jb20vand0X2NsYWltcy9pc19hZG1pbiI6dHJ1ZswidXNlcklk
  IjoiMTEwMjgzNzM3MjcxMDIiLCJ1c2VybmFtZSI6InZlbG9wZXJ0In0.WE5fMufM0NDSVGJ8cAolXGkyB5RmYwCto1
  pQwDIqo2w",
  "type": "Bearer", 
  "expired": "20201110185520"
}
```













