---
categories : IT
tag : [IT,Linux,MailServer]
---

# Linux Mail Server

<br>

구상도

<br>

interface 설정 변경![2022-07-26-02환경설정](../images/2022-07-26-Linux Mail Server/2022-07-26-02환경설정.PNG)

<br>

postfix 설치![2022-07-26-01postfix다운](../images/2022-07-26-Linux Mail Server/2022-07-26-01postfix다운.PNG)

postfix는 smtp 역할 입니다. 필수로 설치 해주시기 바랍니다.

<br>

postfix 설정 변경![2022-07-26-03etcpostfixmaincf](../images/2022-07-26-Linux Mail Server/2022-07-26-03etcpostfixmaincf.PNG)

`vi /etc/postfix/main.cf` 로 들어가시면 됩니다.

<br>

postfix 설정 변경![2022-07-26-04설정추가](../images/2022-07-26-Linux Mail Server/2022-07-26-04설정추가.PNG)

맨 밑에 위의 내용들을 추가해 주시면 됩니다.

<br>

postfix 재시작, 상태확인![2022-07-26-05restart,status](../images/2022-07-26-Linux Mail Server/2022-07-26-05restart,status.PNG)

설정을 바꿧으니 재시작 하고 제대로 동작 하는지 확인 해 봅니다.

<br>dovecot 설치![2022-07-26-06dovecot설치](../images/2022-07-26-Linux Mail Server/2022-07-26-06dovecot설치.PNG)

dovecot은 pop3 역할을 해줍니다. 역시 필수로 설치 하셔야 합니다.

<br>

dovecot 설정변경 1![2022-07-26-07dovecot설정변경1](../images/2022-07-26-Linux Mail Server/2022-07-26-07dovecot설정변경1.PNG)

`/etc/dovecot/dovecot.conf` 로 들어가셔서 24행을 복사 후 25행에 붙여넣기

<br>

dovecot 설정변경 2![2022-07-26-08dovecot설정변경2 24행복붙](../images/2022-07-26-Linux Mail Server/2022-07-26-08dovecot설정변경2 24행복붙.PNG)

`/etc/dovecot/conf.d/10-mail.conf` 24행 복사 후 27행에 붙여넣기 주석해제

메일함 위치를 홈디렉터리 아래 maildir/에 두겠다는 뜻 입니다.

<br>

dovecot 설정변경 3![2022-07-26-08dovecot설정변경3 10행복붙](../images/2022-07-26-Linux Mail Server/2022-07-26-08dovecot설정변경3 10행복붙.PNG)

`/etc/dovecot/conf.d/10-auth.conf` 10행을 주석처리 후 복사 붙여넣기 하고 yes -> no 로 변경

<br>

dovecot 설정변경 4







