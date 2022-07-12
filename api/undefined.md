# 메시지 발송

### Parameter Description

| **설명**  | <ul><li>메시지 발송을 요청하는 기능입니다.</li></ul>    |
| :-----: | ---------------------------------------- |
| **URL** | **\[POST]** api.bizppurio.com/v3/message |

### Request

**Header**&#x20;

![](<../.gitbook/assets/image (16) (1) (1).png>)

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

![](<../.gitbook/assets/image (14) (1).png>)

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

![](<../.gitbook/assets/image (10) (1) (1).png>)

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

![](<../.gitbook/assets/image (2) (1) (1).png>)

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

![](<../.gitbook/assets/image (12) (1).png>)

**file**

![](<../.gitbook/assets/image (25) (1) (1) (1).png>)

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

![](<../.gitbook/assets/image (24) (1) (1) (1) (1) (1).png>)

### BUTTON

![](<../.gitbook/assets/image (3) (1).png>)

**버튼 타입 별 속성 (\*type)**

![](<../.gitbook/assets/image (5) (1) (1).png>)



### ITEM

![](<../.gitbook/assets/image (18) (1).png>)

### ITEMHIGHLIGHT

![](<../.gitbook/assets/image (22) (1).png>)

### IMAGE

![](<../.gitbook/assets/image (23) (1) (1) (1).png>)

### QUICKREPLY

![](<../.gitbook/assets/image (15).png>)

**버튼 타입 별 속성 (\*type)**

![](<../.gitbook/assets/image (26) (1) (1).png>)

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

![](<../.gitbook/assets/image (16) (1).png>)

**공통 포맷(MESSAGEBASE ID)**

![](<../.gitbook/assets/image (23) (1) (1).png>)

> **\*글자수 및 라인수 정의**
>
> 글자 수 : 1줄 당 정상적으로 표현가능한 글자 수, 한글 **'**가' 기준 측정
>
> 줄(라인) 수 : expand 없이 메시지 버블 최대크기에서 표현 가능한 description 줄 수

**LMS (Standalone No media)**

**\[글자 수]**

![](<../.gitbook/assets/image (20) (1).png>)

**\[줄 수(접혀있는 경우)]**

![](<../.gitbook/assets/image (12).png>)



**MMS (Standalone Media Top – 세로형)**

**글자 수**

![](<../.gitbook/assets/image (10) (1).png>)

**\[줄 수(Media Tall인 경우, 접혀있는 경우)]**

![](<../.gitbook/assets/image (24) (1) (1) (1) (1).png>)

**\[줄 수(Media Medium인 경우, 접혀있는 경우)]**

![](<../.gitbook/assets/image (2) (1).png>)

**MMS (Carousel Medium – 슬라이드형)**

**글자 수**

![](<../.gitbook/assets/image (20).png>)

**\[줄 수 (Media 없는 경우, RCS A2P 단말 기준)]**

![](<../.gitbook/assets/image (24) (1) (1) (1).png>)

**\[줄 수 (Media Medium인 경우, RCS A2P 단말 기준)]**

![](<../.gitbook/assets/image (23) (1).png>)

**MMS (Carousel Small – 슬라이드형)**

**글자 수**

![](<../.gitbook/assets/image (9).png>)

**줄 수 (Media Short인 경우, RCS A2P 단말 기준)**

![](<../.gitbook/assets/image (6).png>)

### MESSAGE

![](<../.gitbook/assets/image (27) (1) (1).png>)



### media 종류&#x20;

**이미지**

비즈뿌리오 사이트의 \[메시지관리] – \[RCS 관리] – \[RCS 이미지 관리] 메뉴에서 이미지를 등록하여 사용합니다.

이미지는 등록일로부터 365일간 발송 가능합니다. (이후 자동 삭제)

**이미지 URL**

포맷 : **maapfile://{fileId}**

예시 : "media":"maapfile://BR.i6dOpSm8N8.20200302150000.001"



**동영상 스트리밍**

* 3가지 형태의 YouTube URL 주소 지원 \
  ****(정확한 형식을 준수해야 하며, 일부만 일치하는 경우 실패)
* 동영상 썸네일은 등록된 이미지만 사용 가능하며 YouTube URL 뒤에 콤마(,)와 함께 입력\
  (콤마(,) 외 공백을 포함하는 경우 실패)

### BUTTON

![](<../.gitbook/assets/image (7) (1).png>)



### SUGGESTIONS

![](<../.gitbook/assets/image (18).png>)



### ACTION

![](<../.gitbook/assets/image (25) (1) (1).png>)



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

![](<../.gitbook/assets/image (24) (1) (1).png>)

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

* **해외수신자에게 국제 메시지를 발송하는 서비스**



**메시지 유형별 메시지 길이 제한**

![](<../.gitbook/assets/image (23).png>)

****

Ex) 미국(1) 010-1234-1234로 전송하는 경우

**\* 수신 번호에 국가 코드를 포함하는 경우**&#x20;

![](<../.gitbook/assets/image (17).png>)

![](<../.gitbook/assets/image (3).png>)

### Response

**Headers**

```http
HTTP/1.1 200 OK
Content-type: application/json
```

**Body**

![](<../.gitbook/assets/image (26) (1).png>)

**예시)**

```json
{
  "code": 1000,
  "description": "Success",
  "refkey": "123456789012345678901234890123",
  "messagekey": "190922175225820#ft002951servj8FU67"
}
```

