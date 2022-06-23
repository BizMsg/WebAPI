# File Upload



### Parameter Description

| **설명**  | <ul><li>파일을 업로드 하여 MMS 전송 시 사용할 파일 키를 발급합니다.</li></ul><ul><li>파일은 확장자(jpg/jpeg), 크기(300kbyte 이하) 제한이 있습니다.</li></ul><ul><li>요청 시 파일 업로드 수는 1개로 제한합니다.</li></ul> |
| :-----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **URL** | <p><strong>[POST] api.bizppurio.com/v1/file</strong><br><strong>세부스펙</strong></p>                                                                               |

****

**Request**

**Headers**

|       키      |   타입   |                값                |
| :----------: | :----: | :-----------------------------: |
| Content-type | String | application/json; charset=utf-8 |

**Body**

|             키             |      타입      |             값             |   |   |
| :-----------------------: | :----------: | :-----------------------: | - | - |
|    Content-Disposition    |    String    | form-data; name="account" |   |   |
|        Content-Type       |    String    | text/plain; charset=UTF-8 |   |   |
| Content-Transfer-Encoding |    String    |            8bit           |   |   |
|            file           | File(String) |          filename         |   |   |
|            name           |    String    |            file           |   |   |
|          account          |    String    |           계정 ID           |   |   |

****\
**Response**

**Headers**

|       키      |   타입   |                값                |
| :----------: | :----: | :-----------------------------: |
| Content-type | String | application/json; charset=utf-8 |

**Body**

**성공**

|    키    |  타입  |  길이 |  필수 |  설명  |
| :-----: | :--: | :-: | :-: | :--: |
| filekey | text |  40 |  Y  | 파일 키 |

**실패**

|      키      |  타입  |  길이 |  필수 |                  설명                  |
| :---------: | :--: | :-: | :-: | :----------------------------------: |
|     code    | text |  5  |  Y  | 결과 코드 **\* 8. API 응답 상태 및 결과 코드 참조** |
| description | text |  32 |  Y  |                 결과 메시                |

### Examples

**Request**

**Header**

```http
POST /v1/file HTTP/1.1
Content-Type: multipart/form-data; boundary=5d14-GC42dS9N5BXQAKuhpRfd4VDV54RDDsTJO4
```



**Body**

```http
--5d14-GC42dS9N5BXQAKuhpRfd4VDV54RDDsTJO4
Content-Disposition: form-data; name="account"
Content-Type: text/plain; charset=UTF-8
Content-Transfer-Encoding: 8bit
{비즈뿌리오 계정}
--5d14-GC42dS9N5BXQAKuhpRfd4VDV54RDDsTJO4
Content-Disposition: form-data; name="file"; filename="sample.jpg"
Content-Type: image/jpeg
Content-Transfer-Encoding: binary
<actual file content, not shown here>
--5d14-GC42dS9N5BXQAKuhpRfd4VDV54RDDsTJO4--
```



**Response**

**Header**

```http
HTTP/1.1 200 OK
Content-type: application/json
```

**Body**

* 성공

```json
{
  "filekey": "0920msg_123912934949595969"
}
```

* 실패

|      키      |  타입  |  길이 |  필수 |                  설명                  |
| :---------: | :--: | :-: | :-: | :----------------------------------: |
|     code    | text |  5  |  Y  | 결과 코드 **\* 8. API 응답 상태 및 결과 코드 참조** |
| description | text |  32 |  Y  |                결과 메시지                |





