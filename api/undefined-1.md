# 메시지 발송



{% swagger method="post" path="/v3/message" baseUrl="검수 or 운영 도메인" summary="메시지 전송을 요청하는 기능입니다." %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" required="true" name="Authorization" type="" %}
**인증 토큰 발급을 통해 받은 {type} + " " + {accesstoken}**
{% endswagger-parameter %}

{% swagger-parameter in="header" required="true" name="Content-type" %}
application/json; charset=utf-8
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}
{% endswagger %}

### Request

**Headers**

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

|      Key     | Type |  길이 | 필수여부 |                     설명                    |
| :----------: | :--: | :-: | :--: | :---------------------------------------: |
|    account   | text |  20 |   Y  |                  비즈뿌리오 계정                 |
|     type     | text |  3  |   Y  | 메시지 데이터 **\* SMS, LMS, MMS, AT, FT, RCS** |
|     from     | text |  16 |   Y  |                   발신 번호                   |
|      to      | text |  16 |   Y  |                   수신 번호                   |
|    country   | text |  3  |   N  |        국가 코드 \* **● 국제 메시지 발송 참조**        |
|    content   | json |  -  |   Y  |        메시지 데이터 \* **● CONTENT 참조**        |
|    refkey    | text |  32 |   Y  |                고객사에서 부여한 키                |
|   userinfo   | text |  50 |   N  |                 정산용 부서 코드                 |
|    resend    | json |  3  |   N  |      대체 전송 메시지 유형 \* **● RESEND 참조**      |
|   recontent  | json |  -  |   N  |     대체 전송 메시지 데이터 \* **● CONTENT 참조**     |
| resellercode | text |  10 |   N  |                특부가사업자 식별코드                |

```json
{
  "account": {},
  /*text(20)*//*비즈뿌리오 계정*/
  "type": {},
  /*text(3)*//*메시지 타입*/
  "from": {},
  /*text(20)*//*발신 번호*/
  "to": {},
  /*text(20)*//*수신 번호*/
  "country": {},
  /*text(20)*//*국가 코드*/
  "content": {
  /*text(20)*//*메시지 데이터*/
  "refkey": {},
  /*text(20)*//*고객사에서 부여한 키*/
  "userinfo": {},
  /*text(20)*//*정산용 부서 코드*/
  "resend": {},
  /*text(20)*//*대체 전송 메시지 유형*/
  "recontent": {},
  /*text(20)*//*대체 전송 메시지 데이터*/
  "resellercode": {}
  /*text(20)*//*특부가 사업자 식별코드*/
}
```

**----------------------------------------------------------------------------------------------------**

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











