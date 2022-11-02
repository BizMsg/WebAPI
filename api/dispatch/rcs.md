# RCS



![](<../../.gitbook/assets/image (16) (1).png>)

**공통 포맷(MESSAGEBASE ID)**

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

> **RCS MMS 슬라이드형(Carousel Medium, Small)은 1,300자까지 발송 가능하나 실제 단말에서 수신 가능한 글자 수가 적어 메시지 내용이 잘려 발송될 수 있습니다.**
>
> **아래 글자/라인수 정의 확인하시어 발송하시기 바랍니다.**&#x20;

> **RCS MMS 슬라이드형 글자/ 라인수 정의**&#x20;
>
> 글자 수 : 1줄 당 정상적으로 표현가능한 글자 수, 한글 **'**가' 기준 측정
>
> 라인 수 : 수신 가능한 디스크립션(본문) 줄 수

**Carousel Medium**

![](<../../.gitbook/assets/image (28).png>)

![](<../../.gitbook/assets/image (10).png>)

**Carousel Small**

![](<../../.gitbook/assets/image (14).png>)

![](<../../.gitbook/assets/image (27).png>)

### MESSAGE

![](<../../.gitbook/assets/image (27) (1) (1) (1).png>)



**신규 RCS 포맷**

```json5
"body": {
    "title1": "제목",
    "description1": "본문 텍스트",
    "media1": "maapfile://{fileId_1}",
    "title2": "제목 2번째 카드",
    "description2": "본문 텍스트",
    "media2": "maapfile://{fileId_2}",
    "title3": "제목 3번째 카드",
    "description3": "본문 텍스트",
    "media3": "maapfile://{fileId_3}",
    "media": "maapfile://{fileId_main}      > (신규포맷 mms 전용) 상단 main 이미지",
    "title": "제목 텍스트                   > (신규포맷 mms 전용) 상단 main 제목",
    "description": "본문 텍스트             > (신규포맷 mms 전용) 상단 main 본문",
    "subMedia1": "maapfile://{fileId_sub1}  > (신규포맷 mms 전용) 선택 옵션 서브 이미지 1",
    "subMediaUrl1": "URL                    > (신규포맷 mms 전용) 선택 옵션 서브 이미지 1 클릭 시 랜딩 URL",
    "subTitle1": "제목 텍스트               > (신규포맷 mms 전용) 선택 옵션 소제목 1",
    "subDesc1": "본문 텍스트                > (신규포맷 mms 전용) 선택 옵션 소본문 1",
    "subMedia2": "maapfile://{fileId_sub2}  > (신규포맷 mms 전용) 선택 옵션 서브 이미지 2",
    "subMediaUrl2": "URL                    > (신규포맷 mms 전용) 선택 옵션 서브 이미지 2 클릭 시 랜딩 URL",
    "subTitle2": "제목 텍스트               > (신규포맷 mms 전용) 선택 옵션 소제목 2",
    "subDesc2": "본문 텍스트                > (신규포맷 mms 전용) 선택 옵션 소본문 2",
    "subMedia3": "maapfile://{fileId_sub3}  > (신규포맷 mms 전용) 선택 옵션 서브 이미지 3",
    "subMediaUrl3": "URL                    > (신규포맷 mms 전용) 선택 옵션 서브 이미지 3 클릭 시 랜딩 URL",
    "subTitle3": "제목 텍스트               > (신규포맷 mms 전용) 선택 옵션 소제목 3",
    "subDesc3": "본문 텍스트                > (신규포맷 mms 전용) 선택 옵션 소본문 3"
 }
```



### Media 종류&#x20;

**이미지**

비즈뿌리오 사이트의 \[메시지관리] – \[RCS 관리] – \[RCS 이미지 관리] 메뉴에서 이미지를 등록하여 사용합니다.

이미지는 등록일로부터 365일간 발송 가능합니다. (이후 자동 삭제)

> **이미지 URL**
>
> **포맷**&#x20;
>
> maapfile://{fileId}
>
> &#x20;****&#x20;
>
> **예시**&#x20;
>
> "media" : "maapfile://BR.i6dOpSm8N8.20200302150000.001"

**동영상 스트리밍**

* 3가지 형태의 YouTube URL 주소 지원 \
  ****(정확한 형식을 준수해야 하며, 일부만 일치하는 경우 실패)
* 동영상 썸네일은 등록된 이미지만 사용 가능하며 YouTube URL 뒤에 콤마(,)와 함께 입력\
  (콤마(,) 외 공백을 포함하는 경우 실패)

> **동영상 스트리밍 URL**
>
> **포맷**&#x20;
>
> https://www.youtube.com/watch?v=\[videoId],maapfile://{썸네일용 fileId\_1}
>
> https://youtu.be/\[VideoId],maapfile://{썸네일용 fileId\_2}
>
> https://m.youtube.com/watch?v=\[videoId],maapfile://{썸네일용 fileId\_3}
>
> &#x20;
>
> **예시**&#x20;
>
> "media1" : "https://www.youtube.com/watch?v=KCbtF9I0qvI,maapfile://BR.i6dOpSm8N8.20200302150000.001"



### BUTTON

![](<../../.gitbook/assets/image (7) (1).png>)

### SUGGESTIONS

![](<../../.gitbook/assets/image (18).png>)

### ACTION

![](<../../.gitbook/assets/image (25) (1) (1).png>)

### RCS Examples

RCS : 공통 포맷 SMwThT00 (**MMS Standalone Tall**) 사용 **첨부파일 1개, 버튼 1개**

```json5
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

```json5
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

**New RCS examples**

Highlighted image n title (이미지 & 타이틀 강조형)

```json5
{
  "body": {
    "media": "maapfile://fileId123", (필수)
    "title": "제목",
    "subTitle1": "소제목1",(필수)
    "subDesc1": "소본문1",(필수)
    "subTitle2": "소제목2",
    "subDesc2": "소본문2"
  },
  "buttons": [
    {
      "suggestions": [
        {
          "action": {
            "urlAction": {
              "openUrl": {
                "url": "https://www.google.com"
              }
            },
            "displayText": "구글"
          }
        },
        {
          "action": {
            "urlAction": {
              "openUrl": {
                "url": "https://www.naver.com"
              }
            },
            "displayText": "네이버"
          }
        }
      ]
    }
  ]
}
```

이미지 강조형, SNS형

```json5
{
  "body": {
    "media": "maapfile://fileId123",(필수)
    "title": "제목",
    "description": "본문"(필수)
  },
  "buttons": [
    {
      "suggestions": [
        {
          "action": {
            "urlAction": {
              "openUrl": {
                "url": "https://www.google.com"
              }
            },
            "displayText": "구글"
          }
        },
        {
          "action": {
            "urlAction": {
              "openUrl": {
                "url": "https://www.naver.com"
              }
            },
            "displayText": "네이버"
          }
        }
      ]
    }
  ]
}
```

썸네일형 (세로)

```json5
{
  "body": {
    "media": "maapfile://fileId123",(필수)
    "title": "제목",
    "description": "본문",
    "subMedia1": "maapfile://fileid456",(필수)
    "subMediaUrl1": "http://www.naver.com",
    "subDesc1": "소본문1 이미지클릭가능",(필수)
    "subMedia2": "maapfile://fileid789",(필수)
    "subDesc2": "소본문2 이미지클릭불가"(필수)
  },
  "buttons": [
    {
      "suggestions": [
        {
          "action": {
            "urlAction": {
              "openUrl": {
                "url": "https://www.google.com"
              }
            },
            "displayText": "구글"
          }
        },
        {
          "action": {
            "urlAction": {
              "openUrl": {
                "url": "https://www.naver.com"
              }
            },
            "displayText": "네이버"
          }
        }
      ]
    }
  ]
}
```

썸네일형 (가로)

```json5
{
  "body": {
    "media": "maapfile://fileId123",(필수)
    "title": "제목",
    "description": "본문",(필수)
    "subMedia1": "maapfile://fileid456",(필수)
    "subMediaUrl1": "http://www.naver.com",
    "subMedia2": "maapfile://fileid789",(필수)
    "subMedia3": "maapfile://fileid000"(필수)
  },
  "buttons": [
    {
      "suggestions": [
        {
          "action": {
            "urlAction": {
              "openUrl": {
                "url": "https://www.google.com"
              }
            },
            "displayText": "구글"
          }
        },
        {
          "action": {
            "urlAction": {
              "openUrl": {
                "url": "https://www.naver.com"
              }
            },
            "displayText": "네이버"
          }
        }
      ]
    }
  ]
}
```



### 국제 메시지 발송

* **해외수신자에게 국제 메시지를 발송하는 서비스**



**메시지 유형별 메시지 길이 제한**

![](<../../.gitbook/assets/image (23).png>)

Ex) 미국(1) 010-1234-1234로 전송하는 경우



**\* 수신 번호에 국가 코드를 포함하는 경우**&#x20;

![](<../../.gitbook/assets/image (17).png>)

![](<../../.gitbook/assets/image (3) (2).png>)



### Response

**Headers**

```http
HTTP/1.1 200 OK
Content-type: application/json
```

**Body**

![](<../../.gitbook/assets/image (26) (1) (1).png>)

**예시)**

```json5
{
  "code": 1000,
  "description": "Success",
  "refkey": "123456789012345678901234890123",
  "messagekey": "190922175225820#ft002951servj8FU67"
}
```
