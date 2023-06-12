# POLLING 방식



* **Polling 방식을 사용하기 위해서는 별도로 사용 요청이 필요합니다.**
* Polling 방식으로 발송 요청한 메시지들에 대해 일정 시간 후 발송 결과를 확인하는 방식입니다.
* 발송 결과 조회 후 발송 결과 **완료 처리**를 해야 합니다. 발송 결과 완료 처리를 하지 않으면, 동일한 발송 결과를 응답합니다.
* 지정된 기간(3일)동안 발송 결과 조회 혹은 발송 결과 완료 처리를 하지 않으면, 발송 결과 데이터는 제거됩니다.
* 1회 호출 시 최대 1,000개의 발송 결과를 응답합니다.
* 빈번한 발송 결과 요청은 정책에 따라 차단될 수 있습니다.



## 발송 결과 요청

```http
POST /v1/result/request HTTP/1.1
Content-type: application/json; charset=utf-8
Authorization: Bearer {accesstoken}
```

### **Request**

<table data-header-hidden><thead><tr><th width="150" align="center"></th><th width="570.3333333333333"></th></tr></thead><tbody><tr><td align="center"><strong>설명</strong> </td><td><ul><li>발송 결과를 Polling 방식으로 요청하는 기능입니다.</li></ul></td></tr><tr><td align="center"><strong>URL</strong></td><td><strong>[POST] api.bizppurio.com/v1/result/request</strong></td></tr></tbody></table>

**Headers**

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>



**Body**

<figure><img src="../.gitbook/assets/image (6) (3).png" alt=""><figcaption></figcaption></figure>



### Response

**Headers**

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

**Body**

<figure><img src="../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

**ex)**

```json5
{
  "code": "1000",
  "description": "success",
  "report": [
    {
      "device": "SMS",
      "cmsgid": "201027134355944sms027420servqer0",
      "msgid": "1027se_SL4676027383600490148",
      "phone": "01000000000",
      "media": "SMS",
      "unixtime": "1603773837",
      "result": "4100",
      "userdata": "daoutech",
      "wapinfo": "SKT",
      "refkey": "test1234"
    },
    {
      "device": "SMS",
      "cmsgid": "201027134355944sms027420servqer0",
      "msgid": "1027se_SL4676027383600490148",
      "phone": "01000000000",
      "media": "SMS",
      "unixtime": "1603773837",
      "result": "4100",
      "userdata": "daoutech",
      "wapinfo": "SKT",
      "refkey": "test1234"
    }
  ]
}
```





### Request

**Headers**

```http
POST /v1/result/confirm HTTP/1.1
Content-type: application/json
Authorization: Bearer {인증 토큰 발급을 통해 받은 type + " " + accesstoken}
```

**Body**

<figure><img src="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2Fp24PXjwQmS4twkdG8tKP%2Fuploads%2FX4QqXu4lZ913VnQEy7Yg%2Fimage.png?alt=media&#x26;token=4ea5d84b-1760-443f-9975-4ec470e1e9a9" alt=""><figcaption></figcaption></figure>

**ex)**

```json5
{
  "account": "test",
  "msgid": [
    {
      "msgid": "1027se_SL4676027383600490148"
    },
    {
      "msgid": "1027se_SL4676027383600490149"
    }
  ]
}
```



## 발송 결과 완료 처리

### Response

**Headers**

```http
HTTP/1.1 200 OK
Content-type: application/json
```

<figure><img src="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2Fp24PXjwQmS4twkdG8tKP%2Fuploads%2FBW7nksxWEmLP5LpzmeXd%2Fimage.png?alt=media&#x26;token=158c5455-977f-4ea5-b0b8-d3355db0c05c" alt=""><figcaption></figcaption></figure>

**ex)**

```json5
{
  "code": 1000,
  "description": "Success"
}
```
