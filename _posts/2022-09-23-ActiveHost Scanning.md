# ActiveHost Scanning 

<br>

##### ping

![2022-09-21-53ping](../images/2022-09-23-ActiveHost Scanning/2022-09-21-53ping.PNG)

<br>

##### faipScanner.exe

![2022-09-21-48nmap](../images/2022-09-23-ActiveHost Scanning/2022-09-21-48nmap.PNG)

![2022-09-21-49nmap](../images/2022-09-23-ActiveHost Scanning/2022-09-21-49nmap.PNG)

<br>

##### arping

대상 컴퓨터의 Mac 주소 확인 

![2022-09-21-54arping](../images/2022-09-23-ActiveHost Scanning/2022-09-21-54arping-1663934870343-6.PNG)

<br>

##### fping

sweeping : 네트워크 내에서 활성화된 시스템을 찾는것

![2022-09-21-55farp](../images/2022-09-23-ActiveHost Scanning/2022-09-21-55farp.PNG)

<br>

##### nmap

구상도

![2022-09-21-56구상도](../images/2022-09-23-ActiveHost Scanning/2022-09-21-56구상도.PNG)

<br>

sP : ping scan  , 로컬네트워크 ,  arp ,  원격네트워크는  icmp

![2022-09-21-48nmap](../images/2022-09-23-ActiveHost Scanning/2022-09-21-48nmap-1663934884300-9.PNG)

![2022-09-21-49nmap](../images/2022-09-23-ActiveHost Scanning/2022-09-21-49nmap-1663934886929-11.PNG)

<br>

외부로 ping 보낼때

![2022-09-21-51외부](../images/2022-09-23-ActiveHost Scanning/2022-09-21-51외부.PNG)

![2022-09-21-52외부icmp](../images/2022-09-23-ActiveHost Scanning/2022-09-21-52외부icmp.PNG)

내부에서 ping을 할때는arp로 하지만 외부는 icmp로 확인한다.

<br>

-sU : UDP Scan

centOS에 bind* 설치

```
yum -y install bind*

vi /etcc/named.conf에 들어가서 설정 변경
```

![2022-09-21-57설정](../images/2022-09-23-ActiveHost Scanning/2022-09-21-57설정.PNG)

<br>

데몬 재시작 후 확인

![2022-09-21-58재시작후확인](../images/2022-09-23-ActiveHost Scanning/2022-09-21-58재시작후확인.PNG)

<br>

-sU : UDP Scan

- UDP Packet을 이용해 대상 시스템 Port Scan 

- Close Port → ICMP Destination Unreachable 응답 
- - Open Port → 응답 없음

![2022-09-21-59udp](../images/2022-09-23-ActiveHost Scanning/2022-09-21-59udp.PNG)

<br>

WireShark 확인

![2022-09-21-60udp](../images/2022-09-23-ActiveHost Scanning/2022-09-21-60udp.PNG)

![2022-09-21-61udp53](../images/2022-09-23-ActiveHost Scanning/2022-09-21-61udp53.PNG)

![2022-09-21-62udp54](../images/2022-09-23-ActiveHost Scanning/2022-09-21-62udp54.PNG)

<br>

-sT : TCP Connect Scanning (Full Connection Scan)

- 3 Way-Handshaking을 통해 대상 시스템의 포트 상태 확인 

- Port가 열려있을 경우 세션 수립 / 닫혀있을 경우 RST Packet 수신 - 결과가 정확하고 일반 계정으로 Scanning 가능 함 
- - Overhead 가 크고 Log가 남아 발각되기 쉬움

![2022-09-21-63tcp22](../images/2022-09-23-ActiveHost Scanning/2022-09-21-63tcp22.PNG)

<br>

WireShark 확인

![2022-09-21-64tcp22](../images/2022-09-23-ActiveHost Scanning/2022-09-21-64tcp22.PNG)

열려있는 22번 port는 3way-handshake 모습이 보이지만 tcp port가 아닌 100번은 바로 닫히는 모습 입니다.

<br>

-sS  : Syn Stealth Scan

- 포트가 열려있을 경우 S/A Packet을 받은 후 RST Packet을 보내 연결을 끊는 방법 

- 닫혀 있을 경우 RST Packet 수신

- 세션이 수립되지 않게 ACK 신호를 안보내기 때문에 비교적 Log를 적게 남김

![2022-09-21-65ss](../images/2022-09-23-ActiveHost Scanning/2022-09-21-65ss.PNG)

<br>

WireShark 확인

![2022-09-21-67ss](../images/2022-09-23-ActiveHost Scanning/2022-09-21-67ss.PNG)

<br>

-sF : FIN Scan

- RST Flag 가 설정된 Packet을 확인 함으로써 포트가 닫혔음을 판단함 

- IDS 를 회피할 수 있는 가능성이 높지만, 목표 시스템이 UNIX 플랫폼일 경우만 가능 
- Open/Filter/오류의 결과가 불분명 함

![2022-09-21-68sf](../images/2022-09-23-ActiveHost Scanning/2022-09-21-68sf.PNG)

<br>

WireShark 확인

![2022-09-21-69sf](../images/2022-09-23-ActiveHost Scanning/2022-09-21-69sf.PNG)

![2022-09-21-70sf](../images/2022-09-23-ActiveHost Scanning/2022-09-21-70sf.PNG)

<br>

-sN  : NULL Scan 

- 모든 Flag를 설정하지 않고 Scan 함 

- IDS 를 회피할 가능성이 높지만, 목표 시스템이 UNIX/Linux 플랫폼일 경우만 가능 

- Open/Filter/오류의 결과가 불분명 함

![2022-09-21-71sn](../images/2022-09-23-ActiveHost Scanning/2022-09-21-71sn.PNG)

<br>

WireShark 확인

![2022-09-21-72sn](../images/2022-09-23-ActiveHost Scanning/2022-09-21-72sn.PNG)

![2022-09-21-73sn](../images/2022-09-23-ActiveHost Scanning/2022-09-21-73sn.PNG)

<br>

-sX : X-MAS

- FIN, PSH, URG Flag 를 동시에 설정하여 scan 함 

- IDS 를 회피할 가능성이 높지만, 목표 시스템이 UNIX/Linux 플랫폼일 경우만 가능 

- Open/Filter/오류의 결과가 불분명 함

  ![2022-09-21-74sx](../images/2022-09-23-ActiveHost Scanning/2022-09-21-74sx.PNG)

  <br>

  WireShark 확인

  ![2022-09-21-76sx](../images/2022-09-23-ActiveHost Scanning/2022-09-21-76sx.PNG)

  ![2022-09-21-75sx](../images/2022-09-23-ActiveHost Scanning/2022-09-21-75sx.PNG)

  <br>

TCP scan 시 방화벽 유무 

![2022-09-21-79tcp.PNG](../images/2022-09-23-ActiveHost Scanning/2022-09-21-79tcp.PNG.jpg)

1번째는 방화벽 설정이 되지 않은 상태이고 2번째는 방화벽이 설정된 상태 입니다.

<br>

![2022-09-21-80tcp.PNG](../images/2022-09-23-ActiveHost Scanning/2022-09-21-80tcp.PNG.jpg)

![2022-09-21-81tcp.PNG](../images/2022-09-23-ActiveHost Scanning/2022-09-21-81tcp.PNG.jpg)

TCP 22,100번의 사진 입니다.

22번은 3wayhand-shake가 이뤄지는 모습이 보이고 100번은 22번 과 결과가 다른 것을 알 수 있습니다.

<br>

UDP scan 시 방화벽 유무 

![2022-09-21-82udp.PNG](../images/2022-09-23-ActiveHost Scanning/2022-09-21-82udp.PNG.jpg)

![2022-09-21-83udp.PNG](../images/2022-09-23-ActiveHost Scanning/2022-09-21-83udp.PNG.jpg)

![2022-09-21-84udp.PNG](../images/2022-09-23-ActiveHost Scanning/2022-09-21-84udp.PNG.jpg)

nmap은 udp, tcp에서 close port 응답은 Port Unreachable으로 하도록 약속이 되어있는 것이 기본 약속 입니다.

하지만 지금 iptables로 방화벽을 열고 했을 경우에는 Port Unreachable이 아닌 다른 모습으로 확인이 되고 있습니다.

![2022-09-21-85udp.PNG](../images/2022-09-23-ActiveHost Scanning/2022-09-21-85udp.PNG.jpg)

iptables 설정에 prohibited가 설정 되어 udp 54번 port가 영향을 받아 마지막에 Port Unreachable이 아닌 prohibited가 나오게 되는 것입니다.

<br>

##### IDLE Scanning

<br>

구상도

![2022-09-21-86아이들G](../images/2022-09-23-ActiveHost Scanning/2022-09-21-86아이들G.jpg)

<br>

kali -> xp ping check

![2022-09-21-87아이들G](../images/2022-09-23-ActiveHost Scanning/2022-09-21-87아이들G.jpg)

<br>

