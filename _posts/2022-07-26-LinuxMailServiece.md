---
categories : IT
tag : [IT,Linux,Maillservice]
---

# Linux Mail Serviece

<br>

구상도

<br>

interface 설정![2022-07-26-02환경설정](../images/2022-07-26-LinuxMailServiece/2022-07-26-02환경설정.PNG)

<br>

postfix 설치![2022-07-26-01postfix다운](../images/2022-07-26-LinuxMailServiece/2022-07-26-01postfix다운.PNG)

postfix는 smtp 역할을 합니다. 필수적으로 설치 해주셔야 합니다.

<br>

postfix 설정 변경![2022-07-26-03etcpostfixmaincf](../images/2022-07-26-LinuxMailServiece/2022-07-26-03etcpostfixmaincf.PNG)

vi etc/postfix/main.cf에 들어가시면 됩니다.

<br>

postfix 설정 변경 2![2022-07-26-04설정추가](../images/2022-07-26-LinuxMailServiece/2022-07-26-04설정추가.PNG)

위의 내용들을 맨 밑줄에 추가해 주시면 끝 입니다.

<br>

postfix 재시작, 상태확인![2022-07-26-05restart,status](../images/2022-07-26-LinuxMailServiece/2022-07-26-05restart,status.PNG)

설정을 변경 하였으니 재시작 하고 제대로 작동하는지 확인을 해줍니다.

<br>

dovecot 설치![2022-07-26-06dovecot설치](../images/2022-07-26-LinuxMailServiece/2022-07-26-06dovecot설치.PNG)

<br>

dovecot 설정 변경 1![2022-07-26-07dovecot설정변경1](../images/2022-07-26-LinuxMailServiece/2022-07-26-07dovecot설정변경1.PNG)

/etc/dovecot/dovecot.conf에 가서 24행을 복사 25행에 붙여넣고 주석해제

<br>

dovecot 설정 변경 2![2022-07-26-08dovecot설정변경2 24행복붙](../images/2022-07-26-LinuxMailServiece/2022-07-26-08dovecot설정변경2 24행복붙.PNG)

/etc/dovecot/conf.d/10-mail.conf에 가서 24행 복사 27행에 붙여넣고 주석해제

메일함 위치를 홈 디렉터리 밑에 /Maildir로 지정하겠다 입니다.

<br>

dovecot 설정 변경 3![2022-07-26-08dovecot설정변경3 10행복붙](../images/2022-07-26-LinuxMailServiece/2022-07-26-08dovecot설정변경3 10행복붙.PNG)

/etc/dovecot/conf.d/10-auth.conf에 가서 10행을 복사 11행에 붙여넣기 주석해제 yes를 no로 수정 합니다.

<br>

dovecot 설정 변경 4![2022-07-26-08dovecot설정변경4 8행복붙](../images/2022-07-26-LinuxMailServiece/2022-07-26-08dovecot설정변경4 8행복붙.PNG)

/etc/dovecot/conf.d/10-ssl.conf에 가서 8행을 복사 9행에 붙여넣기 ssl = no 로 수정해 주시면 됩니다.

<br>

dovecot 재시작, 상태확인![2022-07-26-09dovecot재시작 상태확인](../images/2022-07-26-LinuxMailServiece/2022-07-26-09dovecot재시작 상태확인.PNG)

설정을 수정 했으니 재시작 하고 제대로 작동하는지 확인해 줍니다.

<br>

mailx 확인![2022-07-26-10mailx확인](../images/2022-07-26-LinuxMailServiece/2022-07-26-10mailx확인.PNG)

<br>

mail 보내기![2022-07-26-11메일보내기](../images/2022-07-26-LinuxMailServiece/2022-07-26-11메일보내기.PNG)

마지막에 ctrl + d를 눌러 주시면 끝납니다.

<br>

메일함 가서 확인![2022-07-26-12메일함가서확인](../images/2022-07-26-LinuxMailServiece/2022-07-26-12메일함가서확인.PNG)

위에서 입력 하신 메일함으로 가서 확인해 보시면 메일이 아마 스팸 메일함에 있을 겁니다. naver가 안되시는 분들은 gmail로 해보시기 바랍니다.

<br>

DNS 주소 변경![2022-07-26-13dns주소변경](../images/2022-07-26-LinuxMailServiece/2022-07-26-13dns주소변경.PNG)

<br>

서버 구축 확인 set type=mx![2022-07-26-14nslookup확인 type=mx](../images/2022-07-26-LinuxMailServiece/2022-07-26-14nslookup확인 type=mx.PNG)

<br>

서버 구축 확인 set type=a![2022-07-26-15nslookup확인 type=a](../images/2022-07-26-LinuxMailServiece/2022-07-26-15nslookup확인 type=a.PNG)

서버가 제대로 구축 되었는지 조원들과 자신의 서버를 확인 해 볼 수 있는 명령어 입니다.

<br>

test용 user01 생성![2022-07-26-16user01생성1](../images/2022-07-26-LinuxMailServiece/2022-07-26-16user01생성1.PNG)

![2022-07-26-17user01생성2](../images/2022-07-26-LinuxMailServiece/2022-07-26-17user01생성2.PNG)

<br>

아웃룩 설정 변경![2022-07-26-18아웃룩설정변경](../images/2022-07-26-LinuxMailServiece/2022-07-26-18아웃룩설정변경.PNG)

Linux는 window와 다르게 계정 이름에 주소를 넣으면 안됩니다.

계정 이름 user01만 넣으시기 바랍니다.

<br>

메일 주고 받기![2022-07-26-19메일주고받기1](../images/2022-07-26-LinuxMailServiece/2022-07-26-19메일주고받기1.PNG)

![2022-07-26-20메일주고받기2](../images/2022-07-26-LinuxMailServiece/2022-07-26-20메일주고받기2.PNG)

메일 주고 받기에 성공 하였습니다.

<br>

Linux에서 tcp pop3 확인![2022-07-26-21리눅스에서확인](../images/2022-07-26-LinuxMailServiece/2022-07-26-21리눅스에서확인.PNG)

제대로 작동하는 모습을 확인 가능 합니다.

<br>









