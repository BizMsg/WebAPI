# 메시지 발송

### Parameter Description

| **설명**  | <ul><li>메시지 발송을 요청하는 기능입니다.</li></ul>    |
| :-----: | ---------------------------------------- |
| **URL** | **\[POST]** api.bizppurio.com/v3/message |

### Request

**Header**&#x20;

![](<../.gitbook/assets/image (16) (1) (1).png>)

**ex)**

```http
POST /v3/message HTTP/1.1
Content-type: application/json; charset=utf-8
Authorization: 인증 토큰 발급을 통해 받은 {type} + " " + {accesstoken}

----------------------------------------------------------------------------------

예시)
POST /v3/message HTTP/1.1
Content-type: application/json; charset=utf-8
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJ2ZwxvcGVydC5jb20iLCJleHAiOiIx
NDg1MjcwMDAwMDAwIiwiaHR0cHM6Ly92ZwxvcGVydC5jb20vand0X2NsYWltcy9pc19hZG1pbiI6dHJ1ZSwidXNlcklkIjoiMTEwMjgzNzM3MjcxMDIiLCJ1c2VybmFtZSI6InZlbG9wZXJ0In0.WE5fMufM0NDSVGJ8cAolXGkyB5RmYwCto1pQwDIqo2w
```



**Body**

* 공통

![](<../.gitbook/assets/image (14) (1) (1).png>)

**ex)**

```json
{
  /*text(20)*//*비즈뿌리오 계정*/
  "account": {},
  /*text(3)*//*메시지 타입*/
  "type": {},
  /*text(20)*//*발신 번호*/
  "from": {},
  /*text(20)*//*수신 번호*/
  "to": {},
  /*text(20)*//*국가 코드*/
  "country": {},
  /*text(20)*//*메시지 데이터*/
  "content": {
  /*text(20)*//*고객사에서 부여한 키*/
  "refkey": {},
  /*text(20)*//*정산용 부서 코드*/
  "userinfo": {},
  /*text(20)*//*대체 전송 메시지 유형*/
  "resend": {},
  /*text(20)*//*대체 전송 메시지 데이터*/
  "recontent": {},
  /*text(20)*//*특부가 사업자 식별코드*/
  "resellercode": {}
}
```



### Response

**Headers**

```http
HTTP/1.1 200 OK
Content-type: application/json
```

**Body**

![](<../.gitbook/assets/image (26) (1) (1).png>)

**예시)**

```json
{
  "code": 1000,
  "description": "Success",
  "refkey": "123456789012345678901234890123",
  "messagekey": "190922175225820#ft002951servj8FU67"
}
```

