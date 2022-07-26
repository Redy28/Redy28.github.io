---
categories : Linux
tag : [IT, Linux, MailServer]
---



# Linux Mail Server

<br>

구상도

<br>

Interface 설정![2022-07-26-02환경설정](../images/2022-07-26-Linux Mail Server/2022-07-26-02환경설정.PNG)

<br>

postfix 설치하기![2022-07-26-01postfix다운](../images/2022-07-26-Linux Mail Server/2022-07-26-01postfix다운.PNG)

postfix는 smtp 역할을 해주기 때문에 필수로 설치해 주셔야 합니다.

<br>

postfix 설정변경![2022-07-26-03etcpostfixmaincf](../images/2022-07-26-Linux Mail Server/2022-07-26-03etcpostfixmaincf.PNG)

`vi /etc/postfix/main.cf` 로 들어가시면 됩니다.![2022-07-26-04설정추가](../images/2022-07-26-Linux Mail Server/2022-07-26-04설정추가.PNG)

하나라도 틀리면 postfix가 동작하지 않습니다.

정확하게 입력 해주셔야 합니다!!

<br>

postfix 재시작 상태확인![2022-07-26-05restart,status](../images/2022-07-26-Linux Mail Server/2022-07-26-05restart,status.PNG)

<br>

dovecot 설치![2022-07-26-06dovecot설치](../images/2022-07-26-Linux Mail Server/2022-07-26-06dovecot설치.PNG)

dovecot또한 pop3 역할을 해주기 때문에 필수로 설치 해 주셔야 합니다.

<br>

dovecot 설정변경 1![2022-07-26-07dovecot설정변경1](../images/2022-07-26-Linux Mail Server/2022-07-26-07dovecot설정변경1.PNG)

`/etc/dovecot/dovecot.conf`  들어가서 24행을 복사해서 붙여넣고 주석해제만 해주시면 됩니다.

<br>

dovecot 설정변경 2![2022-07-26-08dovecot설정변경2 24행복붙](../images/2022-07-26-Linux Mail Server/2022-07-26-08dovecot설정변경2 24행복붙.PNG)

`/etc/dovecot/conf.d/10-mail.conf` 24행을 복사해서 26행 밑에 붙여넣어 주시고 주석을 해제 해주시면 됩니다.

메일함 위치 홈디렉터리 아래 Maildir/ 에 두겠다는 뜻 입니다.

<br>

dovecot 설정변경 3![2022-07-26-08dovecot설정변경3 10행복붙](../images/2022-07-26-Linux Mail Server/2022-07-26-08dovecot설정변경3 10행복붙.PNG)

10 행을 복사해서 11행에 붙여넣고 10행을 주석처리 해주신 다음에 yes를 no로 바꾸면 됩니다.

암호화를 평문으로 사용 하겠다는 뜻 입니다.

<br>

dovecot 설정변경 4![2022-07-26-08dovecot설정변경4 8행복붙](../images/2022-07-26-Linux Mail Server/2022-07-26-08dovecot설정변경4 8행복붙.PNG)

8행을 복사 붙여넣고 ssl = no 로 바꿔주시면 됩니다.

<br>

dovecot 재시작, 상태확인![2022-07-26-09dovecot재시작 상태확인](../images/2022-07-26-Linux Mail Server/2022-07-26-09dovecot재시작 상태확인.PNG)

설정을 변경 했으니 제대로 적용이 되었는지 재시작, 상태확인을 해 봅니다.

<br>

이제 메일이 잘 보내 지는지 Test를 해 보겠습니다.

<br>

mailx 확인![2022-07-26-10mailx확인](../images/2022-07-26-Linux Mail Server/2022-07-26-10mailx확인.PNG)

<br>

메일 보내기![2022-07-26-11메일보내기](../images/2022-07-26-Linux Mail Server/2022-07-26-11메일보내기.PNG)

마지막에 ctrl + d를 누르시면 종료 됩니다.

<br>

메일함 가서 확인 하기![2022-07-26-12메일함가서확인](../images/2022-07-26-Linux Mail Server/2022-07-26-12메일함가서확인.PNG)

아마 스팸 메일함에 메일이 하나 와 있을 겁니다.

naver가 안되시는 분들은 gmail로 시도 해보시기 바랍니다.

<br>

이제 DNS주소를 x4 주소로 바꿔 줍니다.![2022-07-26-13dns주소변경](../images/2022-07-26-Linux Mail Server/2022-07-26-13dns주소변경.PNG)

<br>

nslookup을 사용해서 서버 확인 해보기![2022-07-26-14nslookup확인 type=mx](../images/2022-07-26-Linux Mail Server/2022-07-26-14nslookup확인 type=mx.PNG)

`set type=mx` 로 먼저 확인 한 상태 입니다.

<br>

`set type=a ` 로 확인 한 상태 입니다. ![2022-07-26-15nslookup확인 type=a](../images/2022-07-26-Linux Mail Server/2022-07-26-15nslookup확인 type=a.PNG)



