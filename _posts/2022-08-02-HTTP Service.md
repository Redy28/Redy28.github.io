# HTTP Service

<br>

구상도

![2022-08-02-10구상도](../images/2022-08-02-HTTP Service/2022-08-02-10구상도.PNG)

<br>

### 웹서버 기본문서 index.html 만들기

<br>

httpd 설치

![2022-08-02-01httpd설치](../images/2022-08-02-HTTP Service/2022-08-02-01httpd설치.PNG)

<br>

httpd 시작

![2022-08-02-03httpd시작](../images/2022-08-02-HTTP Service/2022-08-02-03httpd시작.PNG)

<br>

httpd Test

![2022-08-02-02httpd설치확인](../images/2022-08-02-HTTP Service/2022-08-02-02httpd설치확인.PNG)

<br>

httpd 상태확인

![2022-08-02-04httpd상태확인](../images/2022-08-02-HTTP Service/2022-08-02-04httpd상태확인.PNG)

<br>

web server 기본문서 만들기 1

![2022-08-02-05웹서버구축1](../images/2022-08-02-HTTP Service/2022-08-02-05웹서버구축1.PNG)

<br>

web server 기본문서 만들기 2

![2022-08-02-06웹서버구축2](../images/2022-08-02-HTTP Service/2022-08-02-06웹서버구축2.PNG)

<br>

web server 기본문서 Test

![2022-08-02-07웹서버구축3](../images/2022-08-02-HTTP Service/2022-08-02-07웹서버구축3.PNG)

<br>

Wire Shark 확인

![2022-08-02-09와이어샤크](../images/2022-08-02-HTTP Service/2022-08-02-09와이어샤크.PNG)

![2022-08-02-08와이어샤크](../images/2022-08-02-HTTP Service/2022-08-02-08와이어샤크-165943572054610.PNG)

html의 헤더와 포트번호 해당 페이지의 내용등 확인이 가능 합니다.

<br>

<br>

<br>

### 전역 설정 파일

<br>

전역 설정 파일 위치

![2022-08-02-11전역설정파일](../images/2022-08-02-HTTP Service/2022-08-02-11전역설정파일.PNG)

<br>

파일 수정, 주요 내용

![2022-08-02-13파일주요내용](../images/2022-08-02-HTTP Service/2022-08-02-13파일주요내용.PNG)

http://서버주소  를 입력하면 사용자에게 최상위로 보여지는 디렉터리 입니다.

![2022-08-02-14디폴트다큐먼트수정](../images/2022-08-02-HTTP Service/2022-08-02-14디폴트다큐먼트수정.PNG)

1.html로 수정 해주시면 됩니다.

<br>

파일 생성

![2022-08-02-15파일생성](../images/2022-08-02-HTTP Service/2022-08-02-15파일생성.PNG)

1.html 파일을 생성 해주시고

<br>

재시작

![2022-08-02-16재시작](../images/2022-08-02-HTTP Service/2022-08-02-16재시작.PNG)

<br>

Client에서 확인

![2022-08-02-17확인해보기](../images/2022-08-02-HTTP Service/2022-08-02-17확인해보기.PNG)

확인 해보시면 1.html 파일 안에 있는 내용이 나오게 됩니다.

<br>

<br>

<br>

### Port번호 바꾸기

Server의 전역 파일 들어가서 수정

![2022-08-02-18포트번호바꾸기](../images/2022-08-02-HTTP Service/2022-08-02-18포트번호바꾸기.PNG)

<br>

바뀐 Port번호 확인

![2022-08-02-19포트번호확인](../images/2022-08-02-HTTP Service/2022-08-02-19포트번호확인.PNG)

<br>

Client에서 확인

![2022-08-02-20httpd확인](../images/2022-08-02-HTTP Service/2022-08-02-20httpd확인.PNG)

끝에 바꾼 Port번호를 넣어 주시면 확인 가능 합니다.

<br>

<br>

<br>

### 지역 설정 파일

