# 발송 결과 요청 및 완료 처리 (POLLING 방식)

* **Polling 방식을 사용하기 위해서는 별도로 사용 요청이 필요합니다.**
* Polling 방식으로 발송 요청한 메시지들에 대해 일정 시간 후 발송 결과를 확인하는 방식입니다.
* 발송 결과 조회 후 발송 결과 **완료 처리**를 해야 합니다. 발송 결과 완료 처리를 하지 않으면, 동일한 발송 결과를 응답합니다.
* 지정된 기간(3일)동안 발송 결과 조회 혹은 발송 결과 완료 처리를 하지 않으면, 발송 결과 데이터는 제거됩니다.
* 1회 호출 시 최대 1,000개의 발송 결과를 응답합니다.
* 빈번한 발송 결과 요청은 정책에 따라 차단될 수 있습니다.

## Parameter Description

### **Request**

| **설명**  | <ul><li>발송 결과를 Polling 방식으로 요청하는 기능입니다.</li></ul> |
| :-----: | ------------------------------------------------- |
| **URL** | **api.bizppurio.com/v1/result/request**           |

**Headers**

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

****

**Body**

<figure><img src="../../.gitbook/assets/image (6) (3).png" alt=""><figcaption></figcaption></figure>

****

### Response

**Headers**

<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

**Body**

<figure><img src="../../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

**ex)**

```json5
{
  "code": "1000",
  "description": "success",
  "report": [
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
    },
    {
      "DEVICE": "SMS",
      "CMSGID": "201027134355944sms027420servqer1",
      "MSGID": "1027se_SL4676027383600490148",
      "PHONE": "01000000000",
      "MEDIA": "SMS",
      "UNIXTIME": "1603773837",
      "RESULT": "4100",
      "USERDATA": "daoutech",
      "WAPINFO": "SKT"
    }
  ]
}
```
