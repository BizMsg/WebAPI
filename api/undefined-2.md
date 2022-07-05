# 전송 결과



### Parameter Description

| **설명**  | <ul><li>전송 결과를 재요청하는 기능입니다.</li></ul> |
| :-----: | ------------------------------------- |
| **URL** | **api.bizppurio.com/v2/report**       |

**Request**

**Header**

|       키       |   타입   |                      설명                      |
| :-----------: | :----: | :------------------------------------------: |
| Authorization | String | 인증 토큰 발급을 통해 받은 {type} + " " + {accesstoken} |
|  Content-type | String |        application/json; charset=utf-8       |

**Body**

|      키     |   타입   |    설명    |
| :--------: | :----: | :------: |
|   account  | String | 비즈뿌리오 계정 |
| messagekey | String |   메시지 키  |



## 전송 결과

### Request

**Header**

```http
POST {고객사에서 등록 요청한 URL} HTTP/1.1
Content-type: application/json
```



**Body**

|       키      |  필수 |                    설명                   |
| :----------: | :-: | :-------------------------------------: |
|    DEVICE    |  Y  |                  메시지 유형                 |
|    CMSGID    |  Y  |                  메시지 키                  |
|     MSGID    |  Y  |               비즈뿌리오 메시지 키               |
|     PHONE    |  Y  |                  수신 번호                  |
|     MEDIA    |  Y  |     실제 발송된 메시지 상세 유형 **\* MEDIA 유형**    |
|   TO\_NAME   |  N  |                  수신자 명                  |
|    UNIXTME   |  Y  |                  발송 시간                  |
|    RESULT    |  Y  | 이통사/카카오/RCS 결과 코드 **\* 9. 전송 결과 코드 참조** |
|   USERDATA   |  N  |                정산용 부서 코드                |
|    WAPINFO   |  N  |    이통사/카카오 정보 **\* SKT/KTF/LGT/KAO**    |
|    TELRES    |  N  |               이통사 대체 전송 결과              |
|    TELTIME   |  N  |               이통사 대체 전송 시간              |
|    KAORES    |  N  |               카카오 대체 전송 결과              |
|    KAOTIME   |  N  |               카카오 대체 전송 시간              |
|    RCSRES    |  N  |               RCS 대체 전송 결과              |
|    RCSTIME   |  N  |               RCS 대체 전송 시간              |
|  RETRY\_FLAG |  N  |                 대체 전송 정보                |
| RESEND\_FLAG |  N  |               대체 전송 메시지 유형              |



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



## 전송 결과 재 요청

### **Request**

****

**Header**

```http
POST /v2/report HTTP/1.1
Content-type: application/json
Authorization: Bearer {인증 토큰 발급을 통해 받은 type + " " + accesstoken}
```

**Body**

| 키          | 타입   | 길이 | 필수 | 설명       |
| ---------- | ---- | -- | -- | -------- |
| account    | text | 20 | Y  | 비즈뿌리오 계정 |
| messagekey | text | 32 | Y  | 메시지 키    |

**ex)**

```json
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

| 키           | 타입   | 필수 | 설명                       |
| ----------- | ---- | -- | ------------------------ |
| code        | text | Y  | 결과 코드 (1000 : 성공, 이외 실패) |
| description | text | Y  | 결과 메시지                   |

**ex)**

```json
{
  "code": 1000,
  "description": "Success"
}
```



## 전송 결과 전달 (URL PUSH)

전송 결과는 고객사에서 사전에 등록 요청한 URL로 PUSH 방식으로 전달됩니다.

### Request

**Header**

```http
POST {고객사에서 등록 요청한 URL} HTTP/1.1
Content-type: application/json
```

**Body**

****

|       키      |  필수 |                    설명                   |
| :----------: | :-: | :-------------------------------------: |
|    DEVICE    |  Y  |                  메시지 유형                 |
|    CMSGID    |  Y  |                  메시지 키                  |
|     MSGID    |  Y  |               비즈뿌리오 메시지 키               |
|     PHONE    |  Y  |                  수신 번호                  |
|     MEDIA    |  Y  |     실제 발송된 메시지 상세 유형 **\* MEDIA 유형**    |
|   TO\_NAME   |  N  |                  수신자 명                  |
|    UNIXTME   |  Y  |                  발송 시간                  |
|    RESULT    |  Y  | 이통사/카카오/RCS 결과 코드 **\* 9. 전송 결과 코드 참조** |
|   USERDATA   |  N  |                정산용 부서 코드                |
|    WAPINFO   |  N  |    이통사/카카오 정보 **\* SKT/KTF/LGT/KAO**    |
|    TELRES    |  N  |               이통사 대체 전송 결과              |
|    TELTIME   |  N  |               이통사 대체 전송 시간              |
|    KAORES    |  N  |               카카오 대체 전송 결과              |
|    KAOTIME   |  N  |               카카오 대체 전송 시간              |
|    RCSRES    |  N  |               RCS 대체 전송 결과              |
|    RCSTIME   |  N  |               RCS 대체 전송 시간              |
|  RETRY\_FLAG |  N  |                 대체 전송 정보                |
| RESEND\_FLAG |  N  |               대체 전송 메시지 유형              |

**MEDIA 유형**

****

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

**ex)**

```json
{
  "DEVICE" : "SMS",
  "CMSGID" : "201027134355944sms027420servqer0",
  "MSGID" : "1027se_SL4676027383600490148",
  "PHONE" : "01000000000",
  "MEDIA" : "SMS",
  "UNIXTIME" : "1603773837",
  "RESULT" : "4100",
  "USERDATA" : "daoutech",
  "WAPINFO" : "SKT"
  }

```
