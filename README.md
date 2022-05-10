# 비즈뿌리오 API 소개

본 문서는 비즈뿌리오 서비스의 기능을 HTTP 요청으로 활용할 수 있는 API에 대한 명세와 예제코드를 담은 문서입니다.



### 선결 조건

API를 사용하여 메시지 전송을 하기 위해서 아래의 조건이 선결되어야 합니다.

**1. 서비스 계정 생성 및 사용 승인**\
\- 비즈뿌리오 (https://www.bizppurio.com) 에서 API 용도로 계정 생성

{% embed url="https://www.bizppurio.com" %}

{% hint style="warning" %}
&#x20;운영과 검수 용도로 계정을 구분하여 생성
{% endhint %}



**2. 전송 결과 수신 정보 등록**\
\- 리포트 수신이 필요한 경우, 수신 받을 URL (IP/PORT)에 대한 정보 등록 요청

{% hint style="warning" %}
443,80을 제외한 포트를 사용해야 하는 경우, 별도로 방화벽 접근에 대한 허용 요청
{% endhint %}

\-----------------------------------------------------------------------------------------------------

### **카카오톡 비즈메시지 사용하는 경우**

&#x20;   1\) 카카오톡 채널 개설 및 비즈니스 채널 신청 (https://center-pf.kakao.com)

{% embed url="https://center-pf.kakao.com" %}

&#x20;   2\) 발신 프로필 키 생성 (https://www.bizppurio.com)

&#x20;    ****     3) 알림톡 템플릿 등록/승인 및 친구톡 이미지 등록 (https://www.bizppurio.com)

{% hint style="info" %}
API로 카카오톡 비즈메시지 템플릿을 생성하려면 <>을 참고하십시오
{% endhint %}



### RCS **사용하는 경우**

&#x20;   1\) RCS 브랜드 개설 및 대행사 설정 (https://www.rcsbizcenter.com)

{% embed url="https://www.rcsbizcenter.com" %}
2\) RCS 브랜드 등록
{% endembed %}

&#x20;   2\) RCS 브랜드 등록 (https://www.bizppurio.com)

&#x20;   3\) RCS 발신번호 및 템플릿 등록/승인 (https://www.bizppurio.com)

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

{% swagger method="post" path="/v1/token" baseUrl="검수 or 운영 도메인" summary="인증 토큰을 발급을 요청하는 기능입니다." %}
{% swagger-description %}
API 서비스를 이용하기 위해서 인증 토큰을 발급하기 위한 기능입니다.

인증 토큰의 유효 시간은 24시간이며, 이후에는 사용이 불가하고 재발급이 필요합니다.

Authorization 헤더에 비즈뿌리오 계정과 암호를 Base64 인코딩한 문자열을 입력합니다.
{% endswagger-description %}

{% swagger-parameter in="header" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}
{% endswagger %}
