# 대체 발송

### RESEND

메시지 발송이 실패한 경우, 대체 전송 설정

<figure><img src="../../.gitbook/assets/image (1) (3).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**LMS 대체발송은 키워드가 MMS 입니다.**
{% endhint %}



**1차 대체 발송**

**예시** (AT 발송 실패하는 경우, SMS (1차) 대체 발송) &#x20;

```json5
{
  "account": "test",
  "refkey": "test1234",
  "type": "at",
  "from": "07000000000",
  "to": "01000000000",
  "content": {
    "at": {
      "senderkey": "12345",
      "templatecode": "template",
      "message": "알림톡 + 버튼(WL)",
      "button": [
        {
          "name": "웹 링크 버튼",
          "type": "WL",
          "url_mobile": "https: //www.daou.com",
          "url_pc": "https://www.daou.com"
        }
      ]
    }
  },
  "resend": {
    "first": "sms"
  },
  "recontent": {
    "sms": {
      "message": "SMS 대체 발송"
    }
  }
}
```



**2차 대체 발송**&#x20;

**예시** (RCS 발송 실패하는 경우, AT (1차) 대체 발송, AT (1차) 대체 발송 실패하는 경우, SMS (2차) 대체 발송)&#x20;

```json5
{
  "account": "test",
  "refkey": "test1234",
  "type": "rcs",
  "from": "07000000000",
  "to": "01000000000",
  "content": {
    "rcs": {
      "messagebaseid": "SL000000",
      "chatbotid": "15880000",
      "header": "0",
      "copyallowed": "Y",
      "message": {
        "title": "RCS LMS",
        "description": "RCS 전송"
      },
      "button": [
        {
          "suggestions": [
            {
              "action": {
                "mapAction": {
                  "requestLocationPush": {}
                },
                "displayText": "현재 위치 공유하기"
              }
            }
          ]
        }
      ]
    }
  },
  "resend": {
    "first": "at",
    "second": "sms"
  },
  "recontent": {
    "at": {
      "senderkey": "1234",
      "templatecode": "template",
      "message": "알림톡 전송",
      "button": [
        {
          "name": "웹 링크 버튼",
          "type": "WL",
          "url_mobile": "https://www.daou.com"
        }
      ]
    },
    "sms": {
      "message": "SMS 대체 발송"
    }
  }
}
```
