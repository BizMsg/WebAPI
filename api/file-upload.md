# File Upload



### Parameter Description

| <p><strong></strong></p><p><strong></strong></p><p><strong>설명</strong> </p> | <ul><li>파일을 업로드 하여 MMS 전송 시 사용할 파일 키를 발급합니다.</li></ul><ul><li>파일은 확장자(jpg/jpeg), 크기(300kbyte 이하) 제한이 있습니다.</li></ul><ul><li>요청 시 파일 업로드 수는 1개로 제한합니다.</li></ul> |
| :-------------------------------------------------------------------------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|                                   **URL**                                   | **\[POST] api.bizppurio.com/v1/file**                                                                                                                           |

****

### **Request**

**Headers**

```http
POST /v1/file HTTP/1.1
Content-Type: multipart/form-data; boundary=5d14-GC42dS9N5BXQAKuhpRfd4VDV54RDDsTJO4
```

![](<../.gitbook/assets/image (27) (1) (1).png>)

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

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

### **Response**

**Headers**

```http
HTTP/1.1 200 OK
Content-type: application/json
```

![](<../.gitbook/assets/image (25) (1).png>)

**Body**

**성공**

```json
{
  "filekey": "0920msg_123912934949595969"
}
```

![](<../.gitbook/assets/image (8) (2).png>)

**실패**

![](<../.gitbook/assets/image (5) (1).png>)





