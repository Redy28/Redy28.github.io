# ICMP redirect, DNS spoofing



<br>

구성도

![2022-09-29-06구성도](../images/2022-09-29-ICMPredirect DNS spoofing/2022-09-29-06구성도.jpg)

<br>

파일 준비

![2022-09-29-01icmp다운](../images/2022-09-29-ICMPredirect DNS spoofing/2022-09-29-01icmp다운.jpg)

<br>

gcc 를 이용하여 icmp_redir.c 를 compile 하여 실행 가능한 파일로 생성

![2022-09-29-02컴파일](../images/2022-09-29-ICMPredirect DNS spoofing/2022-09-29-02컴파일.jpg)

![2022-09-29-03컴파일](../images/2022-09-29-ICMPredirect DNS spoofing/2022-09-29-03컴파일.jpg)

![2022-09-29-04컴파일](../images/2022-09-29-ICMPredirect DNS spoofing/2022-09-29-04컴파일.jpg)

<br>

ip forwarding준비

![2022-09-29-05포워딩](../images/2022-09-29-ICMPredirect DNS spoofing/2022-09-29-05포워딩.jpg)

<br>

icmp redirect 공격하기 

1. WireShark

![2022-09-29-07와이어샤크](../images/2022-09-29-ICMPredirect DNS spoofing/2022-09-29-07와이어샤크.jpg)

2. 공격도구 실행

./icmp_redir 192.168.254.254(원래gw) 192.168.254.100(공격대상) 203.248.252.2 (위조대상주소) 192.168.254.200(공격자주소) 

![2022-09-29-09공격](../images/2022-09-29-ICMPredirect DNS spoofing/2022-09-29-09공격.jpg)

<br>

WireShark 확인

![2022-09-29-08와이어샤크](../images/2022-09-29-ICMPredirect DNS spoofing/2022-09-29-08와이어샤크.jpg)

type:5 code:1이 보입니다.

<br>

xp확인

![2022-09-29-13라우트프린트](../images/2022-09-29-ICMPredirect DNS spoofing/2022-09-29-13라우트프린트.jpg)

<br>

xp -> ping 203.248.252.2

![2022-09-29-10핑](../images/2022-09-29-ICMPredirect DNS spoofing/2022-09-29-10핑.jpg)

<br>

ipforwarding 확인

![2022-09-29-11지나가는거](../images/2022-09-29-ICMPredirect DNS spoofing/2022-09-29-11지나가는거.jpg)

xp -> ping 203.248.252.2가 kali에 머무르는 모습이 보입니다.

<br>

WireShark

![2022-09-29-12mac](../images/2022-09-29-ICMPredirect DNS spoofing/2022-09-29-12mac.jpg)

보시면 출발지는 xp인데 MAC주소는 kali로 되어있는 모습입니다.

<br>

##### DNS spoofig

파일생성

![2022-09-29-15파일생성](../images/2022-09-29-ICMPredirect DNS spoofing/2022-09-29-15파일생성.jpg)

![2022-09-29-14내용](../images/2022-09-29-ICMPredirect DNS spoofing/2022-09-29-14내용.jpg)

<br>

dns spoofing

![2022-09-29-16확인](../images/2022-09-29-ICMPredirect DNS spoofing/2022-09-29-16확인.jpg)

<br>

확인

![2022-09-29-17스푸핑확인](../images/2022-09-29-ICMPredirect DNS spoofing/2022-09-29-17스푸핑확인.jpg)

![2022-09-29-18와이어샤크](../images/2022-09-29-ICMPredirect DNS spoofing/2022-09-29-18와이어샤크.jpg)





