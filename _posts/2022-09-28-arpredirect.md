# arp redirect

- arp spoofing 의 일종
- 라우터가 공격 대상이 포함 되면 redirect
  - 라우터 공격
    - ARP redirect : 라우터의 arp cache
    - ICMP Redirect :  host 의 라우팅 테이블 공격

<br>

구상도



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

