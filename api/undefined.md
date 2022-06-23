# 인증토큰 발급

### Parameter Description

| **설명**  | <ul><li>API 서비스를 이용하기 위해서 인증 토큰을 발급하기 위한 기능입니다.</li></ul><ul><li>인증 토큰의 유효 시간은 24시간이며, 이후에는 재발급이 필요합니다.</li></ul><ul><li>Authorization 헤더에 비즈뿌리오 계정과 암호를 Base64 인코딩한 문자열을 입력합니다.</li></ul> |
| :-----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **URL** | **\[POST]** api.bizppurio.com/v1/token                                                                                                                                                     |

**Request**

|       키       |   타입   |                설명               |
| :-----------: | :----: | :-----------------------------: |
| Authorization | String |     Basic 계정:암호(Base64 인코딩)     |
|  Content-type | String | application/json; charset=utf-8 |

**Response**

|      키      |   타입   |                설명               |
| :---------: | :----: | :-----------------------------: |
| accesstoken | String |     Basic 계정:암호(Base64 인코딩)     |
|     type    | String | application/json; charset=utf-8 |
|   expired   | String |             토큰 만료 시점            |

****

### **Examples**

**Response**

**Headers**

```http
POST /v1/token HTTP/1.1
Authorization: Basic Base64(계정:암호)
Content-type: application/json; charset=utf-8
```

**Request**

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













