---
categories : Linux
tag : [IT, Linux, MailServer]
---



# Linux Mail Server

<br>

구상도

<br>

Interface 설정![2022-07-26-02환경설정](../images/2022-07-26Linux Mail Server/2022-07-26-02환경설정.PNG)

<br>

postfix 설치하기![2022-07-26-01postfix다운](../images/2022-07-26Linux Mail Server/2022-07-26-01postfix다운.PNG)

<br>

postfix 설정변경![2022-07-26-03etcpostfixmaincf](../images/2022-07-26Linux Mail Server/2022-07-26-03etcpostfixmaincf.PNG)

`vi /etc/postfix/main.cf` 로 들어가시면 됩니다.![2022-07-26-04설정추가](../images/2022-07-26Linux Mail Server/2022-07-26-04설정추가.PNG)

하나라도 틀리면 postfix가 동작하지 않습니다.

정확하게 입력 해주셔야 합니다!!

<br>

postfix 재시작 상태확인![2022-07-26-05restart,status](../images/2022-07-26Linux Mail Server/2022-07-26-05restart,status.PNG)

<br>





