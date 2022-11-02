# 비즈뿌리오 API 소개

본 문서는 비즈뿌리오 서비스의 기능을 HTTP 요청으로 활용할 수 있는 API에 대한 명세와 예제코드를 담은 문서입니다.



### 선결 조건

API를 사용하여 메시지 발송을 하기 위해서 아래의 조건이 선결되어야 합니다.

**1. 서비스 계정 생성 및 사용 승인**\
\- 비즈뿌리오 ([https://www.bizppurio.com](https://www.bizppurio.com)) 에서 API 용도로 계정 생성

{% embed url="https://www.bizppurio.com" %}

{% hint style="warning" %}
&#x20;운영과 검수 용도로 계정을 구분하여 생성
{% endhint %}



**2. 전송 결과 수신 정보 등록**\
\- 리포트 수신이 필요한 경우, 수신 받을 URL (IP/PORT)에 대한 정보 등록 요청

{% hint style="warning" %}
443,80을 제외한 포트를 사용해야 하는 경우, 별도로 방화벽 접근에 대한 허용 요청
{% endhint %}

### **카카오톡 비즈메시지 사용하는 경우**

&#x20;   1\) 카카오톡 채널 개설 및 비즈니스 채널 신청 ([https://center-pf.kakao.com](https://center-pf.kakao.com))

{% embed url="https://center-pf.kakao.com" %}

&#x20;   2\) 발신 프로필 키 생성 ([https://www.bizppurio.com](https://www.bizppurio.com))

&#x20;    ****     3) 알림톡 템플릿 등록/승인 및 친구톡 이미지 등록 ([https://www.bizppurio.com](https://www.bizppurio.com))

{% hint style="info" %}
API로 카카오톡 비즈메시지 템플릿을 생성하려면 <>을 참고하십시오
{% endhint %}



### RCS **사용하는 경우**

&#x20;   1\) RCS 브랜드 개설 및 대행사 설정 ([https://www.rcsbizcenter.com](https://www.rcsbizcenter.com))

{% embed url="https://www.rcsbizcenter.com" %}
2\) RCS 브랜드 등록
{% endembed %}

&#x20;   2\) RCS 브랜드 등록 ([https://www.bizppurio.com](https://www.bizppurio.com))

&#x20;   3\) RCS 발신번호 및 템플릿 등록/승인 ([https://www.bizppurio.com](https://www.bizppurio.com))

{% embed url="https://www.bizppurio.com" %}

### 연동 규격

**1. HTTPS**

API를 위한 모든 HTTP 요청의 경우 SSL 환경의 HTTPS (443) 를 이용합니다.

**2. UTF-8**

UTF-8 인코딩을 기본으로 제공합니다.



### **API 도메인**

**운영 : api.bizppurio.com**

**검수 : dev-api.bizppurio.com**

****

### **API 기능**

**인증 토큰 발급**

| **설명**  | <ul><li>API 서비스를 이용하기 위해서 인증 토큰을 발급하기 위한 기능입니다.</li></ul><ul><li>인증 토큰의 유효 시간은 24시간이며, 이후에는 재발급이 필요합니다.</li></ul><ul><li>Authorization 헤더에 비즈뿌리오 계정과 암호를 Base64 인코딩한 문자열을 입력합니다.</li></ul>     |
| :-----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **URL** | <p><strong>[POST]</strong> <strong>api.bizppurio.com/v1/token</strong><br><strong></strong><a href="api/authToken.md"><strong><code>세부스펙</code></strong></a><strong><code></code></strong></p> |



**메시지 발송**

| **설명**  | <ul><li>메시지 전송을 요청하는 기능입니다.</li></ul>                                                                                                            |
| :-----: | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| **URL** | <p><strong>[POST] api.bizppurio.com/v3/message</strong><br><strong></strong><a href="api/dispatch.md"><strong><code>세부스펙</code></strong></a></p> |

****

**File Upload**

| **설명**  | <ul><li>파일을 업로드 하여 MMS 전송 시 사용할 파일 키를 발급합니다.</li></ul><ul><li>파일은 확장자(jpg/jpeg), 크기(300kbyte 이하) 제한이 있습니다.</li></ul><ul><li>요청 시 파일 업로드 수는 1개로 제한합니다.</li></ul>                |
| :-----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **URL** | <p><strong>[POST] api.bizppurio.com/v1/file</strong><br><strong></strong><a href="api/file-upload.md"><strong><code>세부스펙</code></strong></a><strong><code></code></strong></p> |

****

**전송 결과**

| **설명**  | <ul><li>전송 결과를 재요청하는 기능입니다.</li></ul>                                                                                                                                                   |
| :-----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **URL** | <p><strong>api.bizppurio.com/v2/report</strong><br><strong></strong><a href="api/undefined/dispatch-result.md"><strong><code>세부스펙</code></strong></a><strong><code></code></strong></p> |



**발송 결과 요청 (POLLING 방식)**

| **설명**  | <ul><li>전송 결과를 요청하는 기능입니다. (POLLING 방식)</li></ul>                                                 |
| :-----: | ------------------------------------------------------------------------------------------------- |
| **URL** | <p><strong>api.bizppurio.com/v1/result/request</strong><br><strong><code>세부스펙</code></strong></p> |



**발송 결과 완료 처리 (POLLING 방식)**

| **설명**  | <ul><li>전송 결과 요청을 완료하는 기능입니다. <br>(POLLING 방식, 전송 결과 요청 후 완료 필요)</li></ul>                 |
| :-----: | ------------------------------------------------------------------------------------------ |
| **URL** | <p><strong>api.bizppurio.com/v1/confirm</strong><br><strong><code>세부스펙</code></strong></p> |
