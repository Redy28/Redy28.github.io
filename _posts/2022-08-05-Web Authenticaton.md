# Web Authenticaton

<br>

### System Authentication

2008 R2를 Web Server로 사용 하겠습니다.

<br>

환경설정

관리도구 > 서버관리자 > 역할 > 역할  추가 > 웹서버(IIS) > 설치

![2022-08-05-1역할추가](../images/2022-08-05-Web Authenticaton/2022-08-05-1역할추가.PNG)

![2022-08-05-2웹서버체크](../images/2022-08-05-Web Authenticaton/2022-08-05-2웹서버체크.PNG)

<br>

Client(xp)에서 확인

![2022-08-05-10인증성공](../images/2022-08-05-Web Authenticaton/2022-08-05-10인증성공.PNG)

<br>

2008 R2 WebServer

관리도구 > IIS 관리자 > 사이트 > default website > 인증 확인

![2022-08-05-3웹서버설정](../images/2022-08-05-Web Authenticaton/2022-08-05-3웹서버설정.PNG)

![2022-08-05-5인증](../images/2022-08-05-Web Authenticaton/2022-08-05-5인증.PNG)

여기까지 들어와 주시기만 하면 됩니다.

<br>

관리도구 > 서버관리자 > 역할 > IIS > 역할 서비스 추가 > 보안 부분 전부체크 > 다음 > 설치

![2022-08-05-4역할서비스추가](../images/2022-08-05-Web Authenticaton/2022-08-05-4역할서비스추가-16596912202017.PNG)

![2022-08-05-6보안다체크](../images/2022-08-05-Web Authenticaton/2022-08-05-6보안다체크.PNG)

설치해 주시고 다시 인증창으로 넘어 오시면 됩니다.

<br>

기본 인증만 사용 나머지 사용 안함

![2022-08-05-8기본인증만사용](../images/2022-08-05-Web Authenticaton/2022-08-05-8기본인증만사용.PNG)

익명인증 사용 안함 해주시고 기본 인증 사용으로 설정 해주시면 됩니다.

<br>

Client에서 확인

![2022-08-05-9인증창](../images/2022-08-05-Web Authenticaton/2022-08-05-9인증창.PNG)

![2022-08-05-21인증성공](../images/2022-08-05-Web Authenticaton/2022-08-05-21인증성공.PNG)

이렇게 익명 사용자 접근을 방지 하기위해 위처럼 로그인을 한 뒤 접속이 가능 합니다.

<br>

<br>

<br>





