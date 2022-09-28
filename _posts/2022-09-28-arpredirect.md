# arp redirect

- arp spoofing 의 일종
- 라우터가 공격 대상이 포함 되면 redirect
  - 라우터 공격
    - ARP redirect : 라우터의 arp cache
    - ICMP Redirect :  host 의 라우팅 테이블 공격

<br>

구상도

![2022-09-28-08구상도](../images/2022-09-28-arpredirect/2022-09-28-08구상도.jpg)

<br>

Router 설정

![2022-09-28-02라우터](../images/2022-09-28-arpredirect/2022-09-28-02라우터.jpg)

Router interface와 P.A.T static NAT를 설정해 줍니다.

<br>

 Router ARP

![2022-09-28-01arp](../images/2022-09-28-arpredirect/2022-09-28-01arp.jpg)

<br>

XP -> 외부 ping

![2022-09-28-03외부로ping](../images/2022-09-28-arpredirect/2022-09-28-03외부로ping.jpg)

<br>

kali -> 외부 ping

![2022-09-28-04외부로ping](../images/2022-09-28-arpredirect/2022-09-28-04외부로ping.jpg)

<br>

arp spoofing

![2022-09-28-05시작ping](../images/2022-09-28-arpredirect/2022-09-28-05시작ping.jpg)

<br>

xp arp 확인

![2022-09-28-06xp확인ping](../images/2022-09-28-arpredirect/2022-09-28-06xp확인ping.jpg)

<br>

router arp 확인

![2022-09-28-07router확인](../images/2022-09-28-arpredirect/2022-09-28-07router확인.jpg)

위의 사진과 비교해 보시면 192.168.254.100 , 200의 mac 주소가 같아진 부분을 볼 수 있습니다.

<br>

PC 1대 더 추가

![2022-09-28-09구상도](../images/2022-09-28-arpredirect/2022-09-28-09구상도.jpg)

<br>

centOS -> 외부 ping

![2022-09-28-10외부로](../images/2022-09-28-arpredirect/2022-09-28-10외부로.jpg)

<br>

패키지 설치

![2022-09-28-11설치](../images/2022-09-28-arpredirect/2022-09-28-11설치.jpg)

arpwatch라는 패키지로 arp 변경점을 잡아주는 패키지 입니다.

<br>

promisc 설정

![2022-09-28-13설정jpg](../images/2022-09-28-arpredirect/2022-09-28-13설정jpg.jpg)

<br>

ifconfig 확인

![2022-09-28-12확인](../images/2022-09-28-arpredirect/2022-09-28-12확인.jpg)

mac 주소도 기억해 두시기 바랍니다.

<br>

arp 변경을 볼 수 있도록 정보가 담긴 file을 tail

![2022-09-28-14tail](../images/2022-09-28-arpredirect/2022-09-28-14tail.jpg)

arp 변경점이 모니터링 되는 모습 입니다.

<br>

arp spoofing

![2022-09-28-15스푸핑](../images/2022-09-28-arpredirect/2022-09-28-15스푸핑.jpg)

<br>

centOS에서 확인

![2022-09-28-16tail](../images/2022-09-28-arpredirect/2022-09-28-16tail.jpg)

