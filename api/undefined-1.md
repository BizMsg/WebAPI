# 메시지 발송

### Parameter Description

| **설명**  | <ul><li>메시지 전송을 요청하는 기능입니다.</li></ul>    |
| :-----: | ---------------------------------------- |
| **URL** | **\[POST]** api.bizppurio.com/v3/message |

### Request

**Headers**

|       키       |   타입   |                      설명                      |
| :-----------: | :----: | :------------------------------------------: |
|  Content-type | String |        application/json; charset=utf-8       |
| Authorization | String | 인증 토큰 발급을 통해 받은 {type} + " " + {accesstoken} |

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

|      Key     | Type |  길이 | 필수여부 |                                 설명                                |
| :----------: | :--: | :-: | :--: | :---------------------------------------------------------------: |
|    account   | text |  20 |   Y  |                              비즈뿌리오 계정                             |
|     type     | text |  3  |   Y  |             메시지 데이터 **\* SMS, LMS, MMS, AT, FT, RCS**             |
|     from     | text |  16 |   Y  |                               발신 번호                               |
|      to      | text |  16 |   Y  |                               수신 번호                               |
|    country   | text |  3  |   N  | 국가 코드 \* **●** [**국제 메시지 발송 참조**](undefined-1.md#undefined-2)**** |
|    content   | json |  -  |   Y  |                    메시지 데이터 \* **● CONTENT 참조**                    |
|    refkey    | text |  32 |   Y  |                            고객사에서 부여한 키                            |
|   userinfo   | text |  50 |   N  |                             정산용 부서 코드                             |
|    resend    | json |  3  |   N  |                  대체 전송 메시지 유형 \* **● RESEND 참조**                  |
|   recontent  | json |  -  |   N  |                 대체 전송 메시지 데이터 \* **● CONTENT 참조**                 |
| resellercode | text |  10 |   N  |                            특부가사업자 식별코드                            |

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

**----------------------------------------------------------------------------------------------------**

## Content

### SMS

|   Key   | Type |  길이 | 필수여부 |            설명            |
| :-----: | :--: | :-: | :--: | :----------------------: |
| message | text |  -  |   Y  | 내용 (EUC-KR 기준, 최대 90바이트) |

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

|   Key   | Type |  길이 | 필수여부 |            설명            |
| :-----: | :--: | :-: | :--: | :----------------------: |
| message | text |  -  |   Y  | 내용 (EUC-KR 기준, 최대 90바이트) |
| subject | text |  64 |   N  | 제목 (EUC-KR 기준, 최대 64바이트) |

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

|     Key    | Type |  길이 | 필수여부 |              설명              |
| :--------: | :--: | :-: | :--: | :--------------------------: |
|   message  | text |  -  |   Y  |   내용 (EUC-KR 기준, 최대 90바이트)   |
| **\*file** | json |  -  |   Y  | 첨부파일 (최대 3개)  **\* FILE 참조** |
|   subject  | text |  64 |   N  |   제목 (EUC-KR 기준, 최대 64바이트)   |

**file**

|  Key | Type |  길이 | 필수여부 |      설명     |
| :--: | :--: | :-: | :--: | :---------: |
| type | text |  3  |   Y  | 파일 유형 (IMG) |
|  key | text |  40 |   Y  |     파일      |

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



### AT/AI

|       키       |  타입  |  길이 |  필수 |                                                   설명                                                  |
| :-----------: | :--: | :-: | :-: | :---------------------------------------------------------------------------------------------------: |
|    message    | text |  -  |  Y  |                                            내용 (한글/영문 1000자)                                           |
|   senderkey   | text |  40 |  Y  |                                                발신 프로필 키                                               |
|  templatecode | text |  32 |  Y  |                                                 템플릿 코드                                                |
|     button    | json |  -  |  -  |       <p><strong>* 템플릿에 포함된 경우, 필수 입력</strong></p><p>버튼 (최대 5개) <strong>* BUTTON 참조</strong></p>      |
|   quickreply  | json |  -  |  -  | <p><strong>* 템플릿에 포함된 경우, 필수 입력</strong></p><p>바로 연결 버튼 (최대 10개) <strong>* QUICKREPLY 참조</strong></p> |
|     title     | text |  50 |  -  |                <p><strong>* 템플릿에 포함된 경우, 필수 입력</strong></p><p>템플릿 내용 중 강조 표기할 핵심 정보</p>               |
|     header    | text |  16 |  N  |                                             알림톡 아이템리스트 헤더                                             |
|      item     | json |  -  |  N  |                                    아이템리스트와 아이템 요약정보 **\* ITEM 참조**                                    |
| itemhighlight | Json |  -  |  N  |                                   아이템 하이라이트 **\* ITEMHIGHLIGHT 참조**                                   |



### FT

|     키     |  타입  |  길이 |  필수 |              설명             |
| :-------: | :--: | :-: | :-: | :-------------------------: |
|  message  | text |  -  |  Y  |        내용(한글/영문 100자)       |
| senderkey | text |  40 |  Y  |           발신 프로필 키          |
|   button  | json |  -  |  N  | 버튼 (최대 5개) **\* BUTTON 참조** |
|   image   | json |  -  |  N  | 이미지 (최대 1개) **\* IMAGE 참조** |
|  userkey  | text |  30 |  N  |           사용자 식별 키          |
|   adflag  | text |  1  |  N  |  광고성 메시지 노출 여부 (Y/N, 기본 Y)  |
|    wide   | text |  1  |  N  |  와이드 이미지 사용 여부 (Y/N, 기본 N)  |



### BUTTON

|        키        |  타입  |  길이 |  필수 |                   설명                  |
| :-------------: | :--: | :-: | :-: | :-----------------------------------: |
|       name      | text |  28 |  Y  |  버튼 제목 **\* AC 타입인 경우, ‘채널 추가’로 고정**  |
|    **\*type**   | text |  2  |  Y  |    버튼 타입 **\* 아래 버튼 타입 별 속성 표 참조**    |
|     url\_pc     | text |  -  |  N  |            PC 환경에서 이동할 URL            |
|   url\_mobile   | text |  -  |  N  |          MOBILE 환경에서 이동할 URL          |
|   scheme\_ios   | text |  -  |  N  |   iOS 환경, Application Custom Scheme   |
| scheme\_android | text |  -  |  N  | ANDROID 환경, Application Custom Scheme |

**버튼 타입 별 속성 (\*type)**

| 버튼 타입 |        속성       |  타입  | 필수여부 |                                                             설명                                                             |
| :---: | :-------------: | :--: | :--: | :------------------------------------------------------------------------------------------------------------------------: |
|   WL  |     url\_pc     | text |   N  |                                                       PC 환경에서 이동할 URL                                                      |
|       |   url\_mobile   | text |   Y  |                                                     MOBILE 환경에서 이동할 URL                                                    |
|   AL  |   scheme\_ios   | text |   -  | <p><strong>* scheme_ios, scheme_android, url_mobile 중 2가지 필수 입력</strong></p><p>클릭 시 실행할 OS 별 Application Custom Scheme</p> |
|       | scheme\_android | text |   -  |                                                                                                                            |
|       |     url\_pc     | text |   N  |                                                       PC 환경에서 이동할 URL                                                      |
|       |   url\_mobile   | text |   -  |                                                     MOBILE 환경에서 이동할 URL                                                    |
|   DS  |        -        |   -  |   -  |                                                    버튼 클릭 시 배송 조회 페이지로 이동                                                   |
|   BK  |        -        |   -  |   -  |                                                        해당 버튼 텍스트 전송                                                        |
|   MD  |        -        |   -  |   -  |                                                    해당 버튼 텍스트 + 메시지 본문 전송                                                   |
|   BC  |        -        |   -  |   -  |                                                  상담톡을 이용하는 카카오톡 채널만 이용 가능                                                  |
|       |   chat\_extra   | text |   N  |                                                      봇 전환 시 전달할 메타 정보                                                      |
|   BT  |        -        |   -  |   -  |                                            카카오 \| 오픈 빌더의 챗봇을 사용하는 카카오톡 채널만 이용 가능                                           |
|       |   chat\_extra   | text |   N  |                                                      봇 전환 시 전달할 메타 정보                                                      |
|       |   chat\_event   | text |   N  |                                                      봇 전환 시 연결할 봇 이벤트명                                                     |
|   AC  |        -        |   -  |   -  |                                                     버튼 클릭 시 카카오톡 채널 추가                                                     |



### ITEM

|    키    |      -      |   타입  |  길이 |  필수 |     설명    |
| :-----: | :---------: | :---: | :-: | :-: | :-------: |
|   list  |             | array |     |  Y  |  아이템 리스트  |
|         |    title    |  text |  6  |  Y  |    타이틀    |
|         | description |  text |  23 |  Y  |   디스크립션   |
| summary |             |  json |     |  N  | 아이템 요약 정보 |
|         |    title    |  text |  6  |  Y  |    타이틀    |
|         | description |  text |  14 |  Y  |   디스크립션   |



### ITEMHIGHLIGHT

|      키      |  타입  |  길이 |  필수 |     설명     |
| :---------: | :--: | :-: | :-: | :--------: |
|    title    | text |  30 |  Y  |     타이틀    |
| description | text |  19 |  Y  |    디스크립션   |
|   imageUrl  | text | 500 |  N  | 썸네일 이미지 주소 |



### IMAGE

|     키     |  타입  |  길이 |  필수 |        설명        |
| :-------: | :--: | :-: | :-: | :--------------: |
|  img\_url | text |  -  |  Y  |      노출할 이미지     |
| img\_link | text |  -  |  N  | 이미지 클릭 시 이동할 URL |



### QUICKREPLY

|        키        |  타입  |  길이 |  필수 |                   설명                  |
| :-------------: | :--: | :-: | :-: | :-----------------------------------: |
|       name      | text |  28 |  Y  |                바로 연결 제목               |
|       type      | text |  2  |  Y  |   버튼 연결 타입 **\* 아래 버튼 타입 별 속성 표 참조**  |
|     url\_pc     | text |  -  |  N  |            PC 환경에서 이동할 URL            |
|   url\_mobile   | text |  -  |  N  |          MOBILE 환경에서 이동할 URL          |
|   scheme\_ios   | text |  -  |  N  |   iOS 환경, Application Custom Scheme   |
| scheme\_android | text |  -  |  N  | ANDROID 환경, Application Custom Scheme |
|   chat\_extra   | text |  -  |  N  |          상담톡/봇 전환 시 전달할 메타 정보         |
|   chat\_event   | text |  -  |  N  |           봇 전환 시 연결한 봇 이벤트명           |



|  타입 |        속성       |  타입  | 필수여부 |                                                             설명                                                             |
| :-: | :-------------: | :--: | :--: | :------------------------------------------------------------------------------------------------------------------------: |
|  WL |     url\_pc     | text |   N  |                                                       PC 환경에서 이동할 URL                                                      |
|     |   url\_mobile   | text |   Y  |                                                     MOBILE 환경에서 이동할 URL                                                    |
|  AL |   scheme\_ios   | text |   -  | <p><strong>* scheme_ios, scheme_android, url_mobile 중 2가지 필수 입력</strong></p><p>클릭 시 실행할 OS 별 Application Custom Scheme</p> |
|     | scheme\_android | text |   -  |                                                                                                                            |
|     |     url\_pc     | text |   N  |                                                       PC 환경에서 이동할 URL                                                      |
|     |   url\_mobile   | text |   -  |                                                     MOBILE 환경에서 이동할 URL                                                    |
|  DS |        -        |   -  |   -  |                                                    버튼 클릭 시 배송 조회 페이지로 이동                                                   |
|  BK |        -        |   -  |   -  |                                                        해당 버튼 텍스트 전송                                                        |
|  MD |        -        |   -  |   -  |                                                    해당 버튼 텍스트 + 메시지 본문 전송                                                   |
|  BC |        -        |   -  |   -  |                                                  상담톡을 이용하는 카카오톡 채널만 이용 가능                                                  |
|     |   chat\_extra   | text |   N  |                                                      봇 전환 시 전달할 메타 정보                                                      |
|  BT |        -        |   -  |   -  |                                            카카오 \| 오픈 빌더의 챗봇을 사용하는 카카오톡 채널만 이용 가능                                           |
|     |   chat\_extra   | text |   N  |                                                      봇 전환 시 전달할 메타 정보                                                      |
|     |   chat\_event   | text |   N  |                                                      봇 전환 시 연결할 봇 이벤트명                                                     |

**----------------------------------------------------------------------------------------------------**

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

**----------------------------------------------------------------------------------------------------**

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

**----------------------------------------------------------------------------------------------------**

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

**----------------------------------------------------------------------------------------------------**

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

**----------------------------------------------------------------------------------------------------**

**MMS (Carousel Small – 슬라이드형)**

**글자 수**

| 타이틀 | 디스크립션 | 버튼명 |
| :-: | :---: | :-: |
|  5  |   6   |  5  |

**줄 수 (Media Short인 경우, RCS A2P 단말 기준)**

|                | 버튼 0개 | 버튼 1개 | 버튼 2개 |
| -------------- | :---: | :---: | :---: |
| 디스크립션 only     |   20  |   18  |   16  |
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

\* 수신 번호에 국가 코드를 포함하는 경우

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







