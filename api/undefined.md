# 메시지 발송

### Parameter Description

| **설명**  | <ul><li>메시지 발송을 요청하는 기능입니다.</li></ul>    |
| :-----: | ---------------------------------------- |
| **URL** | **\[POST]** api.bizppurio.com/v3/message |

### Request

**Header**&#x20;

![](<../.gitbook/assets/image (16).png>)

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

![](<../.gitbook/assets/image (14).png>)

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

## Content

### SMS

![](<../.gitbook/assets/image (10).png>)

```json
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

![](<../.gitbook/assets/image (2).png>)

```json
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

![](<../.gitbook/assets/image (12).png>)

**file**

![](<../.gitbook/assets/image (25).png>)

```json
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



### AT/AI**/FT**

![](<../.gitbook/assets/image (24).png>)

### BUTTON

![](<../.gitbook/assets/image (3).png>)

**버튼 타입 별 속성 (\*type)**

![](<../.gitbook/assets/image (5).png>)



### ITEM

![](<../.gitbook/assets/image (18).png>)

### ITEMHIGHLIGHT

![](<../.gitbook/assets/image (22).png>)

### IMAGE

![](<../.gitbook/assets/image (23).png>)

### QUICKREPLY

![](<../.gitbook/assets/image (15).png>)

**버튼 타입 별 속성 (\*type)**

![](<../.gitbook/assets/image (8).png>)

### Examples

**알림톡**

```json
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
          "url_pc": "http://www.bizppurio.com",
          "url_mobile": "http://www.bizppurio.com"
        }
      ]
    }
  }
}
```

**알림톡 아이템 리스트형**

```json
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
      "message": "알림톡 아이템리스트 + 버튼(WL)",
      "header": "헤더 (최대 16자)",
      "button": [
        {
          "name": "웹 링크 버튼",
          "type": "WL",
          "url_pc": "http://www.bizppurio.com",
          "url_mobile": "http://www.bizppurio.com"
        }
      ],
      "item": {
        "list": [
          {
            "title": "타이틀",
            "description": "디스크립션"
          },
          {
            "title": "타이틀2",
            "description": "디스크립션2"
          }
        ],
        "summary": {
          "title": "요약 타이틀",
          "description": "$100,000원"
        }
      },
      "itemhighlight": {
        "title": "타이틀",
        "description": "디스크립션"
      }
    }
  }
}
```



**친구톡**

```json
{
  "account": "test",
  "refkey": "test1234",
  "type": "ai",
  "from": "07000000000",
  "to": "01000000000",
  "content": {
    "ai": {
      "senderkey": "12345",
      "templatecode": "template",
      "message": "알림톡 이미지"
    }
  }
}
```

### **RCS**

|       키       |  타입  |  길이 | 필수여부 |                                        설명                                        |   |
| :-----------: | :--: | :-: | :--: | :------------------------------------------------------------------------------: | - |
|    message    | json |  -  |   N  |                        메시지 베이스에서 치환할 정보 **\* MESSAGE 참조**                        |   |
| messagebaseid | text |  40 |   Y  | <p>RCS 공통 포맷 (RCS SMS, LMS, MMS) <strong>* 공통 포맷 참조</strong></p><p>또는 템플릿 ID</p> |   |
|   chatbotid   | text |  40 |   Y  |                             RCS 브랜드 포탈을 통해 생성한 챗봇 ID                             |   |
|    agencyid   | text |  20 |   N  |                              대행사 ID (기본 : daoutech)                              |   |
|     header    | text |  1  |   Y  |                         메시지 상단에 식별 문구 입력 (0:Web 발신, 1:광고)                        |   |
|     footer    | text |  64 |   N  |                               메시지 하단에 수신 거부 문구를 입력                               |   |
|  copyallowed  | text |  1  |   N  |                           단말기에서 사용자에게 ‘복사/공유’ 메뉴 보기 여부                           |   |
|     button    | json |  -  |   N  |                          메시지에 삽입할 버튼 정보 **\* BUTTON 참조**                         |   |

**공통 포맷(MESSAGEBASE ID)**

|     ID     | 메시지 유형1 |        메시지 유형2       | 카드 장 수 | 카드 별 최대 버튼 수 | 본문 길이 (글자수) |
| :--------: | :-----: | :------------------: | :----: | :----------: | :---------: |
|  SS000000  |   SMS   |      Standalone      |    1   |       1      |     100     |
|  SL000000  |   LMS   |      Standalone      |    1   |       3      |     1300    |
|  SMwThT00  |   MMS   | Standalone Media Top |    1   |       2      |     1300    |
|  SMwThM00  |   MMS   | Standalone Media Top |    1   |       2      |     1300    |
| CMwMhM0300 |   MMS   |    Carousel Medium   |    3   |       2      |  1300 (총합)  |
| CMwMhM0400 |   MMS   |    Carousel Medium   |    4   |       2      |  1300 (총합)  |
| CMwMhM0500 |   MMS   |    Carousel Medium   |    5   |       2      |  1300 (총합)  |
| CMwMhM0600 |   MMS   |    Carousel Medium   |    6   |       2      |  1300 (총합)  |
| CMwShS0300 |   MMS   |    Carousel Small    |    3   |       2      |  1300 (총합)  |
| CMwShS0400 |   MMS   |    Carousel Small    |    4   |       2      |  1300 (총합)  |
| CMwShS0500 |   MMS   |    Carousel Small    |    5   |       2      |  1300 (총합)  |
| CMwShS0600 |   MMS   |    Carousel Small    |    6   |       2      |  1300 (총합)  |

> **\*글자수 및 라인수 정의**
>
> 글자 수 : 1줄 당 정상적으로 표현가능한 글자 수, 한글 **'**가' 기준 측정
>
> 줄(라인) 수 : expand 없이 메시지 버블 최대크기에서 표현 가능한 description 줄 수

**\[글자 수]**

| 타이틀 | 디스크립션 | 버튼명 |
| :-: | :---: | :-: |
|  16 |   18  |  17 |

**\[줄 수(접혀있는 경우)]**

|                | 버튼 0개 | 버튼 1개 | 버튼 2개 | 버튼 3개 |
| :------------: | :---: | :---: | :---: | :---: |
|   디스크립션 only   |   28  |   26  |   24  |   22  |
| 타이틀 1줄 + 디스크립션 |   27  |   25  |   23  |   20  |
| 타이틀 2줄 + 디스크립션 |   26  |   23  |   21  |   19  |



**MMS (Standalone Media Top – 세로형)**

**글자 수**

| 타이틀 | 디스크립션 | 버튼명 |
| :-: | :---: | :-: |
|  16 |   18  |  17 |

**\[줄 수(Media Tall인 경우, 접혀있는 경우)]**

|                | 버튼 0개 | 버튼 1개 | 버튼 2개 |
| :------------: | :---: | :---: | :---: |
|   디스크립션 only   |   9   |   8   |   6   |
| 타이틀 1줄 + 디스크립션 |   8   |   6   |   4   |
| 타이틀 2줄 + 디스크립션 |   7   |   5   |   3   |

**\[줄 수(Media Medium인 경우, 접혀있는 경우)]**

|                | 버튼 0개 | 버튼 1개 | 버튼 2개 |
| :------------: | :---: | :---: | :---: |
|   디스크립션 only   |   15  |   13  |   11  |
| 타이틀 1줄 + 디스크립션 |   14  |   12  |   10  |
| 타이틀 2줄 + 디스크립션 |   13  |   11  |   9   |

**MMS (Carousel Medium – 슬라이드형)**

**글자 수**

| 타이틀 | 디스크립션 | 버튼명 |
| :-: | :---: | :-: |
|  13 |   14  |  13 |

**\[줄 수 (Media 없는 경우, RCS A2P 단말 기준)]**

|                | 버튼 0개 | 버튼 1개 | 버튼 2개 |
| :------------: | :---: | :---: | :---: |
|   디스크립션 only   |   28  |   26  |   23  |
| 타이틀 1줄 + 디스크립션 |   27  |   25  |   23  |
| 타이틀 2줄 + 디스크립션 |   26  |   23  |   21  |
| 타이틀 3줄 + 디스크립션 |   24  |   22  |   20  |

**\[줄 수 (Media Medium인 경우, RCS A2P 단말 기준)]**

|                | 버튼 0개 | 버튼 1개 | 버튼 2개 |
| -------------- | :---: | :---: | :---: |
| 디스크립션 only     |   17  |   15  |   13  |
| 타이틀 1줄 + 디스크립션 |   16  |   14  |   12  |
| 타이틀 2줄 + 디스크립션 |   15  |   13  |   11  |
| 타이틀 3줄 + 디스크립션 |   14  |   12  |   10  |

**MMS (Carousel Small – 슬라이드형)**

**글자 수**

| 타이틀 | 디스크립션 | 버튼명 |
| :-: | :---: | :-: |
|  5  |   6   |  5  |

**줄 수 (Media Short인 경우, RCS A2P 단말 기준)**

|                | 버튼 0개 | 버튼 1개 | 버튼 2개 |
| :------------: | :---: | :---: | :---: |
|   디스크립션 only   |   20  |   18  |   16  |
| 타이틀 1줄 + 디스크립션 |   19  |   17  |   15  |
| 타이틀 2줄 + 디스크립션 |   18  |   16  |   14  |
| 타이틀 3줄 + 디스크립션 |   17  |   15  |   13  |
| 타이틀 4줄 + 디스크립션 |   16  |   14  |   12  |
| 타이틀 5줄 + 디스크립션 |   15  |   13  |   11  |



### MESSAGE

|      키      |  타입  |  길이 |  필수 |  설명  |
| :---------: | :--: | :-: | :-: | :--: |
|    title    | text |  -  |  N  |  제목  |
|    media    | text |  -  |  N  | 첨부파일 |
| description | text |  -  |  N  |  내용  |



### media 종류&#x20;

**이미지**

비즈뿌리오 사이트의 \[메시지관리] – \[RCS 관리] – \[RCS 이미지 관리] 메뉴에서 이미지를 등록하여 사용합니다.

이미지는 등록일로부터 365일간 발송 가능합니다. (이후 자동 삭제)

### BUTTON

| 키           | 타입                     | 설명                    |
| ----------- | ---------------------- | --------------------- |
| suggestions | array of 'suggestions' | **\* SUGGESTIONS 참조** |



### SUGGESTIONS

| 키      | 타입   | 설명               |
| ------ | ---- | ---------------- |
| Action | json | **\* ACTION 참조** |



### ACTION

| 키                       |  타입  |       설명       |
| ----------------------- | :--: | :------------: |
| **displayText**         | text |                |
| **urlAction**           | json |  **URL 연결하기**  |
|     openUrl             |      |                |
|         url             |      |                |
| **dialerAction**        | json |   **전화 연결하기**  |
|     dialPhoneNumber     |      |                |
|         phoneNumber     |      |                |
| **mapAction**           | json |   **지도 보여주기**  |
|     showLocation        |      |                |
|         location        |      |                |
|             latitude    |      |       위도       |
|             longitude   |      |       경도       |
|             label       |      |       표식       |
|         fallbackUrl     |      |     대체 URL     |
| **mapAction**           | json | **현재 위치 공유하기** |
|     requestLocationPush |      |                |
| **clipboardAction**     | json |    **복사 하기**   |
|     copyToClipboard     |      |                |
|         text            |      |  버튼 명 / 복사할 값  |
| **composeAction**       | json |   **메시지 전송**   |
|     composeTextMessage  |      |                |
|         phoneNumber     |      |      수신 번호     |
|         text            |      |       메시지      |
| **calendarAction**      | json |   **캘린더 등록**   |
|     createCalendarEvent |      |                |
|         startTime       |      |      시작 시간     |
|         endTime         |      |      종료 시간     |
|         title           |      |       제목       |
|         description     |      |       설명       |



### RCS Examples

RCS : 공통 포맷 SMwThT00 (**MMS Standalone Tall**) 사용 **첨부파일 1개, 버튼 1개**

```json
{
  "account": "test",
  "refkey": "test1234",
  "type": "rcs",
  "from": "07000000000",
  "to": "01000000000",
  "content": {
    "rcs": {
      "messagebaseid": "SMwThT00",
      "chatbotid": "15880000",
      "header": "1",
      "footer": "무료 수신 거부 080-1234-5678",
      "copyallowed": "Y",
      "message": {
        "description": "안녕하세요! MMS-StandaloneTall(SMwThT00)",
        "media": " maapfile://BR.05NGK0A6dA.20200326140000.001"
      },
      "button": [
        {
          "suggestions": [
            {
              "action": {
                "urlAction": {
                  "openUrl": {
                    "url": "https://www.google.com"
                  }
                },
                "displayText": "구글로 이동"
              }
            }
          ]
        }
      ]
    }
  }
}

```

RCS : 공통 포맷 : CMwMhM0300 (**MMS Carousel Medium 3장**) 사용 **첨부파일 3개, 버튼 카드 별 2개**

```json
{
  "account": "test",
  "refkey": "test1234",
  "type": "rcs",
  "from": "07000000000",
  "to": "01000000000",
  "content": {
    "rcs": {
      "messagebaseid": "CMwMhM0300",
      "chatbotid": "15880000",
      "header": "0",
      "copyallowed": "Y",
      "message": {
        "title1": "첫번째",
        "description1": "1번",
        "media1": "maapfile://BR.05NGK0A6dA.20200326140000.001",
        "title2": "두번째",
        "description2": "2번",
        "media2": "maapfile://BR.05NGK0A6dA.20200326140000.002",
        "title3": "세번째",
        "description3": "3번",
        "media3": "maapfile://BR.05NGK0A6dA.20200326140000.003"
      },
      "button": [
        {
          "suggestions": [
            {
              "action": {
                "urlAction": {
                  "openUrl": {
                    "url": "https://www.google.com"
                  }
                },
                "displayText": "URL 연결하기"
              }
            },
            {
              "action": {
                "dialerAction": {
                  "dialPhoneNumber": {
                    "phoneNumber": "+1650253000"
                  }
                },
                "displayText": "전화 걸기"
              }
            }
          ]
        },
        {
          "suggestions": [
            {
              "action": {
                "composeAction": {
                  "composeTextMessage": {
                    "phoneNumber": "+1650253000",
                    "text": "Draft to go into the send message text field."
                  }
                },
                "displayText": "메시지 전송"
              }
            },
            {
              "action": {
                "clipboardAction": {
                  "copyToClipboard": {
                    "text": "COUPONE-1234-1234"
                  }
                },
                "displayText": "복사하기"
              }
            }
          ]
        },
        {
          "suggestions": [
            {
              "action": {
                "calendarAction": {
                  "createCalendarEvent": {
                    "startTime": "2017-03-16T17:40:00.214+09:00",
                    "endTime": "2017-03-18T17:40:00.216+09:00",
                    "title": "Meeting",
                    "description": "GSG review meeting"
                  }
                },
                "displayText": "캘린더 등록"
              }
            },
            {
              "action": {
                "mapAction": {
                  "showLocation": {
                    "location": {
                      "latitude": 37.4220041,
                      "longitude": -122.0862515,
                      "label": "Googleplex"
                    },
                    "fallbackUrl": "https://www.google.com/maps/@37.4219162,-22.078063,15z"
                  }
                },
                "displayText": "지도 보여주기"
              }
            }
          ]
        }
      ]
    }
  }
}

```

* RESEND

메시지 전송이 실패한 경우, 대체 전송 설정

|    키   |  타입  |  필수 | 설명                                                    |
| :----: | :--: | :-: | ----------------------------------------------------- |
|  first | text |  N  | 1차 대체 전송 메시지 유형 **\* SMS, LMS, MMS, AT, AI, FT, RCS** |
| second | text |  N  | 2차 대체 전송 메시지 유형 **\* SMS, LMS, MMS**                  |

**1차 대체 전송**

**예시** (AT 전송 실패하는 경우, SMS (1차) 대체 전송)

```json
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

**2차 대체 전**

**예시** (RCS 전송 실패하는 경우, AT (1차) 대체 전송, AT (1차) 대체 전송 실패하는 경우, SMS (2차) 대체 전송.

```json
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



### 국제 메시지 발송

**해외수신자에게 국제 메시지를 발송하는 서비스**



**메시지 유형별 메시지 길이 제한**

| 메시지 유형 |           설명           |
| :----: | :--------------------: |
|   sms  |  본문 최대 한글 50자, 영문 150자 |
|   lms  | 본문 최대 한글 150자, 영문 450자 |
|   at   |       한글/영문 1000자      |
|   ft   |       한글/영문 1000자      |

Ex) 미국(1) 010-1234-1234로 전송하는 경우

**\* 수신 번호에 국가 코드를 포함하는 경우**&#x20;

| 지원 메시지 유형 |          주요 파라미터 예시         |
| :-------: | :-------------------------: |
|    sms    | **"**to" : "00211012341234" |
|    lms    | **"**to" : "00211012341234" |

| 메시지 유형 | 대체 전송 메시지 유형 |                    주요 파라미터 예시                   |
| :----: | :----------: | :---------------------------------------------: |
|   sms  |       -      | <p>"country" : "1",<br>"to" : "01012341234"</p> |
|   lms  |       -      |                                                 |
|  at/ai |       -      |                                                 |
|        |      sms     |                                                 |
|        |      lms     |                                                 |
|   ft   |       -      |                                                 |
|        |      sms     |                                                 |
|        |      lms     |                                                 |



### Response

**Headers**

```http
HTTP/1.1 200 OK
Content-type: application/json
```

**Body**

|      키      |  타입  |  길이 |  필수 | 설명                                   |
| :---------: | :--: | :-: | :-: | ------------------------------------ |
|     code    | text |  5  |  Y  | 결과 코드 **\* 8. API 응답 상태 및 결과 코드 참조** |
| description | text |  32 |  Y  | 결과 메시지                               |
|  messagekey | text |  32 |  Y  | 메시지 키 **\* 고객 문의 및 리포트 재 요청 기준 키**   |
|    refkey   | Text |  32 |  Y  | 고객사에서 부여한 키                          |

**예시)**

```json
{
  "code": 1000,
  "description": "Success",
  "refkey": "123456789012345678901234890123",
  "messagekey": "190922175225820#ft002951servj8FU67"
}
```







