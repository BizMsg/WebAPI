# PUSH 방식

{% hint style="info" %}
비즈뿌리오 리포트 수신 URL을 설정하였다면 발송 결과가 발생함과 동시에 PUSH 방식으로 전달됩니다.\
(결과 요청 할 필요 없음)
{% endhint %}



## 발송 결과 전달

발송 결과는 고객사에서 사전에 등록 요청한 URL로 PUSH 방식으로 전달됩니다.

### Request

**Header**

```http
POST {고객사에서 등록 요청한 URL} HTTP/1.1
Content-type: application/json
```



**Body**

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

**예시)**

```json
{
  "DEVICE": "SMS",
  "CMSGID": "201027134355944sms027420servqer0",
  "MSGID": "1027se_SL4676027383600490148",
  "PHONE": "01000000000",
  "MEDIA": "SMS",
  "UNIXTIME": "1603773837",
  "RESULT": "4100",
  "USERDATA": "daoutech",
  "WAPINFO": "SKT",
  "REFKEY" : "smstest00001"
}
```



**MEDIA 유형**

<table data-header-hidden><thead><tr><th width="195" align="center"></th><th align="center"></th></tr></thead><tbody><tr><td align="center">분류</td><td align="center">설명</td></tr><tr><td align="center">SMS</td><td align="center">국내 SMS 발송</td></tr><tr><td align="center">ISM</td><td align="center">국제 SMS 발송</td></tr><tr><td align="center">VDO</td><td align="center">비디오 발송</td></tr><tr><td align="center">MMS</td><td align="center">이미지 발송</td></tr><tr><td align="center">LMS</td><td align="center">국내 LMS 발송</td></tr><tr><td align="center">ILM</td><td align="center">국제 LMS 발송</td></tr><tr><td align="center">FSI</td><td align="center">국제 FAX 발송</td></tr><tr><td align="center">FSD</td><td align="center">국내 FAX 발송</td></tr><tr><td align="center">VMC</td><td align="center">유선 PHONE 발송</td></tr><tr><td align="center">VMW</td><td align="center">무선 PHONE 발송</td></tr><tr><td align="center">WAP</td><td align="center">WAP 발송</td></tr><tr><td align="center">KAT</td><td align="center">알림톡 발송</td></tr><tr><td align="center">KFT</td><td align="center">친구톡 텍스트 발송</td></tr><tr><td align="center">KFP</td><td align="center">친구톡 이미지 발송</td></tr><tr><td align="center">KFW</td><td align="center">친구톡 와이드 이미지 발송</td></tr><tr><td align="center">RSS</td><td align="center">RCS SMS 발송</td></tr><tr><td align="center">RLS</td><td align="center">RCS LMS 발송</td></tr><tr><td align="center">RMS</td><td align="center">RCS MMS 발송</td></tr><tr><td align="center">RTS</td><td align="center">RCS TEMPLATE 발송</td></tr></tbody></table>





## 발송 결과 재 요청

<table data-header-hidden><thead><tr><th width="150" align="center"></th><th width="570.3333333333333"></th></tr></thead><tbody><tr><td align="center"><strong>설명</strong> </td><td><ul><li>발송 결과를 재요청하는 기능입니다.</li></ul></td></tr><tr><td align="center"><strong>URL</strong></td><td><strong>[POST] api.bizppurio.com/v2/report</strong></td></tr></tbody></table>

### **Request**

**Header**

```http
POST /v2/report HTTP/1.1
Content-type: application/json
Authorization: Bearer {accesstoken}
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
