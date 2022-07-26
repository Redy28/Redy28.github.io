---
categories : IT
tag : [IT,Linux,MailService]
---

# Linux Mail Service

<br>

구상도

<br>

Interface 변경![2022-07-26-02환경설정](../images/2022-07-26-Linux Mail Service/2022-07-26-02환경설정.PNG)

<br>

postfix 설치![2022-07-26-01postfix다운](../images/2022-07-26-Linux Mail Service/2022-07-26-01postfix다운.PNG)

postfix는 smtp 역할을 해주기 때문에 필수적으로 설치 해주셔야 합니다.

<br>

postfix 설정 변경 1![2022-07-26-03etcpostfixmaincf](../images/2022-07-26-Linux Mail Service/2022-07-26-03etcpostfixmaincf.PNG)

/etc/postfix/main.cf에 들어가셔서 아래와 같이 변경 해주시면 됩니다.

<br>

postfix 설정 변경 2![2022-07-26-04설정추가](../images/2022-07-26-Linux Mail Service/2022-07-26-04설정추가.PNG)

위의 내용을 맨밑에 넣어 주시면 됩니다.

<br>

postfix 재시작, 상태확인![2022-07-26-05restart,status](../images/2022-07-26-Linux Mail Service/2022-07-26-05restart,status.PNG)

설정을 변경 하였기 때문에 재시작 하고 잘 동작하고 있나 확인 해주는 과정 입니다.

<br>

dovecot 설치![2022-07-26-06dovecot설치](../images/2022-07-26-Linux Mail Service/2022-07-26-06dovecot설치.PNG)

dovecot은 pop3의 역할을 해주기 때문에 역시 필수적으로 설치 해주셔야 합니다.

<br>

dovecot 설정 변경 1![2022-07-26-07dovecot설정변경1](../images/2022-07-26-Linux Mail Service/2022-07-26-07dovecot설정변경1.PNG)

/etc/dovecot/dovecot.conf에서 24번행 복사 25행에 붙여넣기

24번행 주석처리 25번행 주석해제 해주시면 됩니다.

<br>

dovecot 설정 변경 2![2022-07-26-08dovecot설정변경2 24행복붙](../images/2022-07-26-Linux Mail Service/2022-07-26-08dovecot설정변경2 24행복붙.PNG)

/etc/dovecot/conf.d/10-mail.conf에서 24번행 복사 27행에 붙여넣기 하고 주석해제 해주시면 됩니다.

메일함의 위치를 홈디렉터리 아래 Maildir로 하겠다 라는 뜻 입니다.

<br>

dovecot 설정 변경 3![2022-07-26-08dovecot설정변경3 10행복붙](../images/2022-07-26-Linux Mail Service/2022-07-26-08dovecot설정변경3 10행복붙.PNG)

/etc/dovecot/conf.d/10-auth.conf에서 10번행 복사 11번행에 붙여넣기 하고 yes를 no로 수정 해주시면 됩니다.

<br>

dovecot 설정 변경 4![2022-07-26-08dovecot설정변경4 8행복붙](../images/2022-07-26-Linux Mail Service/2022-07-26-08dovecot설정변경4 8행복붙.PNG)

/etc/dovecot/conf.d/10-ssl.conf에서 8번행 복사 9번행에 붙여넣기 하고 no로 수정 해주시면 됩니다.

<br>

dovecot 재시작, 상태확인![2022-07-26-09dovecot재시작 상태확인](../images/2022-07-26-Linux Mail Service/2022-07-26-09dovecot재시작 상태확인.PNG)

이번에도 설정을 변경 하였기에 재시작 하고 잘 동작하는지 확인 해 주셔야 합니다.

<br>

mailx 확인![2022-07-26-10mailx확인](../images/2022-07-26-Linux Mail Service/2022-07-26-10mailx확인.PNG)

<br>

mail 보내기![2022-07-26-11메일보내기](../images/2022-07-26-Linux Mail Service/2022-07-26-11메일보내기.PNG)

마지막에 ctrl + d를 누르시면 종료 됩니다.

<br>

mail 확인![2022-07-26-12메일함가서확인](../images/2022-07-26-Linux Mail Service/2022-07-26-12메일함가서확인.PNG)

naver로 하시면 보통 스팸 메일함에 있습니다. naver로 했는데 안되신 분들은 gmail로 해보시기 바랍니다.

<br>

DNS 주소변경![2022-07-26-13dns주소변경](../images/2022-07-26-Linux Mail Service/2022-07-26-13dns주소변경.PNG)

<br>

서버 구성 확인 1![2022-07-26-14nslookup확인 type=mx](../images/2022-07-26-Linux Mail Service/2022-07-26-14nslookup확인 type=mx.PNG)

set type = mx 입니다.

<br>

서버 구성 확인 2![2022-07-26-15nslookup확인 type=a](../images/2022-07-26-Linux Mail Service/2022-07-26-15nslookup확인 type=a.PNG)

set type = a 입니다.

두개의 명령어 다 서버 구성을 확인 할 때 쓰는 명령어 입니다.

<br>

test용 user01 생성![2022-07-26-16user01생성1](../images/2022-07-26-Linux Mail Service/2022-07-26-16user01생성1.PNG)

![2022-07-26-17user01생성2](../images/2022-07-26-Linux Mail Service/2022-07-26-17user01생성2.PNG)

<br>

x1에서 아웃룩 설정 변경![2022-07-26-18아웃룩설정변경](../images/2022-07-26-Linux Mail Service/2022-07-26-18아웃룩설정변경.PNG)



리눅스 에서는 계정 이름에 user01만 써주셔야 합니다.

<br>

메일 주고 받기![2022-07-26-19메일주고받기1](../images/2022-07-26-Linux Mail Service/2022-07-26-19메일주고받기1.PNG)

![2022-07-26-20메일주고받기2](../images/2022-07-26-Linux Mail Service/2022-07-26-20메일주고받기2.PNG)

메일 주고 받기 성공입니다!!

<br>

Linux에서 pop3 smtp 확인하기![2022-07-26-21리눅스에서확인](../images/2022-07-26-Linux Mail Service/2022-07-26-21리눅스에서확인.PNG)

정상적으로 동작하는 것도 확인 하였습니다.

<br>

