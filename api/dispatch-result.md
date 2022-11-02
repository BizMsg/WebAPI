# 발송 결과 전달 (PUSH 방식)

{% hint style="info" %}
비즈뿌리오 리포트 수신 URL을 설정하였다면 발송 결과가 발생함과 동시에 PUSH 방식으로 전달됩니다.\
(결과 요청 할 필요 없음)
{% endhint %}



## 발송 결과 전달 (URL PUSH)

발송 결과는 고객사에서 사전에 등록 요청한 URL로 PUSH 방식으로 전달됩니다.

### Request

**Header**

```http
POST {고객사에서 등록 요청한 URL} HTTP/1.1
Content-type: application/json
```



**Body**

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

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
  "WAPINFO": "SKT"
}
```



**MEDIA 유형**

|  분류 |        설명       |
| :-: | :-------------: |
| SMS |    국내 SMS 발송    |
| ISM |    국제 SMS 발송    |
| VDO |      비디오 발송     |
| MMS |      이미지 발송     |
| LMS |    국내 LMS 발송    |
| ILM |    국제 LMS 발송    |
| FSI |    국제 FAX 발송    |
| FSD |    국내 FAX 발송    |
| VMC |   유선 PHONE 발송   |
| VMW |   무선 PHONE 발송   |
| WAP |      WAP 발송     |
| KAT |      알림톡 발송     |
| KFT |    친구톡 텍스트 발송   |
| KFP |    친구톡 이미지 발송   |
| KFW |  친구톡 와이드 이미지 발송 |
| RSS |    RCS SMS 발송   |
| RLS |    RCS LMS 발송   |
| RMS |    RCS MMS 발송   |
| RTS | RCS TEMPLATE 발송 |

