# 발송 결과 재 요청

### **Request**

**Header**

```http
POST /v2/report HTTP/1.1
Content-type: application/json
Authorization: Bearer {인증 토큰 발급을 통해 받은 type + " " + accesstoken}
```

**Body**

![](<../.gitbook/assets/image (28) (1) (1) (1).png>)

**ex)**

```json5
{
  "account": "test",
  "messagekey": "190922175225820#ft002951servj8FU67"
}
```



### Response

**Header**

```http
HTTP/1.1 200 OK   
Content-type: application/json
```

**Body**

![](<../.gitbook/assets/image (24).png>)

**ex)**

```json5
{
  "code": 1000,
  "description": "Success"
}
```
