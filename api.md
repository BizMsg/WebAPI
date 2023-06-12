# API 상태코드/결과코드

### 상태코드

<table><thead><tr><th width="118" align="center">상태코드</th><th width="102" align="center">결과코드</th><th width="485.71428571428567" align="center">설명</th></tr></thead><tbody><tr><td align="center">200</td><td align="center">1000</td><td align="center">성공 </td></tr><tr><td align="center">400</td><td align="center">2000</td><td align="center">메시지가 유효하지 않음</td></tr><tr><td align="center">400</td><td align="center">3000</td><td align="center">비즈 뿌리오 계정에 접속 허용 아이피가 등록되어있지 않음</td></tr><tr><td align="center">400</td><td align="center">3001</td><td align="center">인증 토큰 발급 호출 시, Basic Authentication 정보가 유효하지 않음</td></tr><tr><td align="center">400</td><td align="center">3002</td><td align="center">토큰이 유효하지 않음</td></tr><tr><td align="center">400</td><td align="center">3003</td><td align="center">아이피가 유효하지 않음</td></tr><tr><td align="center">400</td><td align="center">3004</td><td align="center">계정이 유효하지 않음</td></tr><tr><td align="center">400</td><td align="center">3005</td><td align="center">인증 정보가 유효하지 않음 (bearer)</td></tr><tr><td align="center">400</td><td align="center">3006</td><td align="center">비즈뿌리오 계정이 존재하지 않음</td></tr><tr><td align="center">400</td><td align="center">3007</td><td align="center">비즈뿌리오 계정의 암호가 유효하지 않음</td></tr><tr><td align="center">400</td><td align="center">3008</td><td align="center">비즈뿌리오에 허용된 접속 수를 초과함</td></tr><tr><td align="center">400</td><td align="center">3009</td><td align="center">비즈뿌리오 계정이 중지 상태임</td></tr><tr><td align="center">400</td><td align="center">3010</td><td align="center">비즈뿌리오 계정에 등록된 접속 허용 IP와 일치하지 않음</td></tr><tr><td align="center">400</td><td align="center">3011</td><td align="center">비즈뿌리오 내에서 알 수 없는 오류가 발생됨</td></tr><tr><td align="center">400</td><td align="center">3012</td><td align="center">비즈뿌리오에 존재하지 않은 메시지 (예: 보관 주기 35일이 지난 메시지)</td></tr><tr><td align="center">400</td><td align="center">3013</td><td align="center">완료 처리 되지 않은 메시지 (예: 통신사로부터 결과 미 수신)</td></tr><tr><td align="center">400</td><td align="center">5000</td><td align="center">발송 결과 재 요청 실패</td></tr><tr><td align="center">400</td><td align="center">5001</td><td align="center">요청한 URI 리소스가 존재하지 않음</td></tr><tr><td align="center">500</td><td align="center">9000</td><td align="center">알 수 없는 오류 발생</td></tr></tbody></table>







{% hint style="warning" %}
API 결과코드 1000은 API 요청 성공을 의미합니다.

발송 성공/실패 확인은 비즈뿌리오 실시간 결과조회 페이지의 엑셀을 내려받거나

발송결과리포트를 수신하여 확인하시길 바랍니다.
{% endhint %}

