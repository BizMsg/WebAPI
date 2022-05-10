# WebAPI

## API 요청

**인증 토큰 발급**

{% swagger method="post" path="/v1/token" baseUrl="검수 or 운영 도메인" summary="인증 토큰 발급 요청" %}
{% swagger-description %}
API 서비스를 이용하기 위해서 인증 토큰을 발급하기 위한 기능입니다.

인증 토큰의 유효 시간은 24시간이며, 이후에는 사용이 불가하고 재발급이 필요합니다.

Authorization 헤더에 비즈뿌리오 계정과 암호를 Base64 인코딩한 문자열을 입력합니다.
{% endswagger-description %}

{% swagger-parameter in="header" required="true" name="Authorization" type="" %}
Basic 계정:암호(Base64 인코딩)
{% endswagger-parameter %}

{% swagger-parameter in="header" required="true" name="Content-type" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="accesstoken" type="" required="true" %}
인증 토
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="type" %}
Bearer
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="expired" %}
토큰 만료 시
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}
{% endswagger %}

### **Request**

**Headers**

```http
POST /v1/token HTTP/1.1
Authorization: Basic Base64(계정:암호)
Content-type: application/json; charset=utf-8
```

****

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



## 메시지 전송

{% swagger method="post" path="/v3/message" baseUrl="검수 or 운영 도메인" summary="메시지 전송을 요청하는 기능입니다." %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Content-type" %}
application/json; charset=utf-8
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" %}
**인증 토큰 발급을 통해 받은 {type} + " " + {accesstoken}**
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}
{% endswagger %}

### Request

**Headers**

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

|      Key     | Type |  길이 | 필수여부 |                     설명                    |
| :----------: | :--: | :-: | :--: | :---------------------------------------: |
|    account   | text |  20 |   Y  |                  비즈뿌리오 계정                 |
|     type     | text |  3  |   Y  | 메시지 데이터 **\* SMS, LMS, MMS, AT, FT, RCS** |
|     from     | text |  16 |   Y  |                   발신 번호                   |
|      to      | text |  16 |   Y  |                   수신 번호                   |
|    country   | text |  3  |   N  |        국가 코드 \* **● 국제 메시지 발송 참조**        |
|    content   | json |  -  |   Y  |        메시지 데이터 \* **● CONTENT 참조**        |
|    refkey    | text |  32 |   Y  |                고객사에서 부여한 키                |
|   userinfo   | text |  50 |   N  |                 정산용 부서 코드                 |
|    resend    | json |  3  |   N  |      대체 전송 메시지 유형 \* **● RESEND 참조**      |
|   recontent  | json |  -  |   N  |     대체 전송 메시지 데이터 \* **● CONTENT 참조**     |
| resellercode | text |  10 |   N  |                특부가사업자 식별코드                |

```json5
{
  "account": {},
  /*text(20)*//*비즈뿌리오 계정*/
  "type": {},
  /*text(3)*//*메시지 타입*/
  "from": {},
  /*text(20)*//*발신 번호*/
  "to": {},
  /*text(20)*//*수신 번호*/
  "country": {},
  /*text(20)*//*국가 코드*/
  "content": {
  /*text(20)*//*메시지 데이터*/
  "refkey": {},
  /*text(20)*//*고객사에서 부여한 키*/
  "userinfo": {},
  /*text(20)*//*정산용 부서 코드*/
  "resend": {},
  /*text(20)*//*대체 전송 메시지 유형*/
  "recontent": {},
  /*text(20)*//*대체 전송 메시지 데이터*/
  "resellercode": {}
  /*text(20)*//*특부가 사업자 식별코드*/
}
```

### SMS

|   Key   | Type |  길이 | 필수여부 |            설명            |
| :-----: | :--: | :-: | :--: | :----------------------: |
| message | text |  -  |   Y  | 내용 (EUC-KR 기준, 최대 90바이트) |

```json5
{
  "account": {},
  "type": {},
  "from": {},
  "to": {},
  "country": {},
  "content": {
    "sms": {
      "message": {}
    }
  },
  "refkey": {},
  "userinfo": {},
  "resend": {},
  "recontent": {},
  "resellercode": {}
}
```



### LMS

|   Key   | Type |  길이 | 필수여부 |            설명            |
| :-----: | :--: | :-: | :--: | :----------------------: |
| message | text |  -  |   Y  | 내용 (EUC-KR 기준, 최대 90바이트) |
| subject | text |  64 |   N  | 제목 (EUC-KR 기준, 최대 64바이트) |

```json5
{
  "account": {},
  "type": {},
  "from": {},
  "to": {},
  "country": {},
  "content": {
    "lms": {
      "message": {},
      "subject": {}
    }
  },
  "refkey": {},
  "userinfo": {},
  "resend": {},
  "recontent": {},
  "resellercode": {}
}
```



### MMS



|     Key    | Type |  길이 | 필수여부 |              설명              |
| :--------: | :--: | :-: | :--: | :--------------------------: |
|   message  | text |  -  |   Y  |   내용 (EUC-KR 기준, 최대 90바이트)   |
| **\*file** | json |  -  |   Y  | 첨부파일 (최대 3개)  **\* FILE 참조** |
|   subject  | text |  64 |   N  |   제목 (EUC-KR 기준, 최대 64바이트)   |

**file**

|  Key | Type |  길이 | 필수여부 |      설명     |
| :--: | :--: | :-: | :--: | :---------: |
| type | text |  3  |   Y  | 파일 유형 (IMG) |
|  key | text |  40 |   Y  |     파일      |

```json5
{
  "account": "",
  "type": "",
  "from": "",
  "to": "",
  "country": "",
  "content": {
    "mms": {
      "message": {},
      "subject": {},
      "file": [
        {
          "type": "",
          "key": ""
        }
      ]
    }
  },
  "refkey": "",
  "userinfo": "",
  "resend": "",
  "recontent": "",
  "resellercode": ""
}
```

















