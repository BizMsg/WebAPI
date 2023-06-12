# 메시지 발송

### Parameter Description

<table data-header-hidden><thead><tr><th width="150" align="center"></th><th width="555.3333333333333"></th></tr></thead><tbody><tr><td align="center"><strong>설명</strong> </td><td><ul><li>메시지 발송을 요청하는 기능입니다.</li></ul></td></tr><tr><td align="center"><strong>URL</strong></td><td><strong>[POST]</strong> api.bizppurio.com/v3/message</td></tr></tbody></table>

### Request

**Header**&#x20;

![](<../.gitbook/assets/image (16) (1) (1).png>)

**ex)**

```http
POST /v3/message HTTP/1.1
Content-type: application/json; charset=utf-8
Authorization: Bearer + " " + {accesstoken}
```

{% hint style="info" %}
Bearer 뒤에 공백이 하나 붙음에 유의하시길 바랍니다.
{% endhint %}

**Body**

*   공통

    <figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

**ex)**

```json
{
    /*text(20)*//*비즈뿌리오 계정*/
    "account": "",
    /*text(3)*//*메시지 타입*/
    "type": "",
    /*text(16)*//*발신 번호*/
    "from": "",
    /*text(16)*//*수신 번호*/
    "to": "",
    /*text(203)*//*국가 코드*/
    "country": "",
    
    /*json*//*메시지 데이터*/
    "content": {
        /*text(32)*//*고객사에서 부여한 키*/
        "refkey": "",
        /*text(50)*//*정산용 부서 코드*/
        "userinfo": "",
        /*text(3)*//*대체 전송 메시지 유형*/
        "resend": "",
        /*json*//*대체 전송 메시지 데이터*/
        "recontent": "",
        /*text(9)*//*특부가 사업자 식별코드*/
        "resellercode": "",
        /*text(9)*//*특부가 사업자 식별코드*/
        "sendtime": ""
    }
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



{% hint style="danger" %}
[**code:1000**](https://biztech.gitbook.io/bizclient/)**의 성공 Response는 api 성공을 뜻하며 발송 결과의 성공을 뜻하지 않으므로**

**발송 결과는 비즈뿌리오 실시간 결과조회 페이지의 엑셀을 다운로드 하여 확인하거나**

**발송 결과 리포트를 받아 확인할 수 있습니다.**
{% endhint %}



