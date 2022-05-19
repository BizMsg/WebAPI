# File Upload



{% swagger method="post" path="/v1/file" baseUrl="검수 or 운영 도메인" summary="서버에 파일을 업로드하여 MMS 전송에 필요한 파일 키를 발급받는 기능입니다." %}
{% swagger-description %}
파일은 확장자(jpg/jpeg), 크기(300kbyte 이하) 제한이 있습니다.

요청 시 파일 업로드 수는 1개로 제한합니다.
{% endswagger-description %}

{% swagger-parameter in="header" required="true" name="Content-type" %}
multipart/form-data; boundary=

**{사용자 지정 문자열}**
{% endswagger-parameter %}

{% swagger-parameter in="body" name="Content-Disposition" required="true" %}
form-data; name="account"
{% endswagger-parameter %}

{% swagger-parameter in="body" name="Content-Type" %}
text/plain; charset=UTF-8
{% endswagger-parameter %}

{% swagger-parameter in="body" name="Content-Transfer-Encoding" %}
8bit
{% endswagger-parameter %}

{% swagger-parameter in="body" name="Content-Disposition" %}
form-data; name="file"; filename="1.jpg"
{% endswagger-parameter %}

{% swagger-parameter in="body" name="Content-Type" %}
image/jpeg
{% endswagger-parameter %}

{% swagger-parameter in="body" name="Content-Transfer-Encoding" %}
binary
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
//Headers
HTTP/1.1 200 OK
Content-type: application/json
//body
{
  "filekey" : "0920msg_123912934949595969"
}

```
{% endswagger-response %}
{% endswagger %}

## MMS 파일 업로드

* 파일을 업로드 하여 MMS 전송 시 사용할 파일 키를 발급합니다.
* 파일은 확장자(jpg/jpeg), 크기(30kbyte 이하) 제한이 있습니다.
* 요청 시 파일 업로드 수는 1개로 제한합니다.

### Request

**Header**

```http
POST /v1/file HTTP/1.1
Content-Type: multipart/form-data; boundary=5d14-GC42dS9N5BXQAKuhpRfd4VDV54RDDsTJO4
```



**Body**

```http
--5d14-GC42dS9N5BXQAKuhpRfd4VDV54RDDsTJO4
Content-Disposition: form-data; name=”account”
Content-Type: text/plain; charset=UTF-8
Content-Transfer-Encoding: 8bit
{비즈뿌리오 계정}
--5d14-GC42dS9N5BXQAKuhpRfd4VDV54RDDsTJO4
Content-Disposition: form-data; name=”file”; filename=”1.jpg”
Content-Type: image/jpeg
Content-Transfer-Encoding: binary
<actual file content, not shown here>
--5d14-GC42dS9N5BXQAKuhpRfd4VDV54RDDsTJO4--
```



### Response

**Header**

```http
HTTP/1.1 200 OK
Content-type: application/json
```

**Body**

* 성공

|    키    |  타입  |  길이 |  필수 |  설명  |
| :-----: | :--: | :-: | :-: | :--: |
| filekey | text |  40 |  Y  | 파일 키 |

* 실패

|      키      |  타입  |  길이 |  필수 |                  설명                  |
| :---------: | :--: | :-: | :-: | :----------------------------------: |
|     code    | text |  5  |  Y  | 결과 코드 **\* 8. API 응답 상태 및 결과 코드 참조** |
| description | text |  32 |  Y  |                결과 메시지                |



**ex)**

```json
{
  "filekey": "0920msg_123912934949595969"
}
```



