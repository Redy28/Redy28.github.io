#  DoS (Denial of Service)

- 서비스 거부 공격 

- CIA Triad 에서 가용성(Availability)을 침해하는 공격 행위 

- 시스템 또는 네트워크의 구조적인 취약점을 이용하여 공격 대상이 정상적인 서비스를 수행하지 못하도록 마비 시키는 공격 

- 기본적으로 공격의 형태가 1 vs 1 → 공격자(1) vs 공격대상(1)

<br>

 공격 방식 

- 물리적인 파괴 
- 시스템 리소스(resource) 공격 → CPU, Memory, Disk, 특정 Application ...
-  네트워크 대역폭 (bandwidth) 공격 → 대역폭 고갈

<br>

##### Ping of Death (죽음의 핑) 

- 시스템 리소스 공격 → 운영체제의 오작동 유발, 메모리 부하, CPU 부하 
- 초기에 사용된 ICMP를 이용하는 DoS 공격

<br>

공격 원리 

- MTU를 초과하는 비 정상으로 큰 "ICMP Echo Request“를 전달(단편화)하여 재조합 과정에서 시스템 충돌 또는 Buffer Overflow를 유발 함 
-  현재는 단편화 된 많은 양의 Echo Request를 전달하여 재 조합 과정에 부하를 유발시키는 형식으로 공격 함 → ICMP Flooding

<br>

구상도

![2022-10-04-02구상도](../images/2022-10-04DenialofService/2022-10-04-02구상도.jpg)

<br>

xp -> cpu 점유율 상태

![2022-10-04-01xp상태](../images/2022-10-04DenialofService/2022-10-04-01xp상태.jpg)

<br>

kali -> 공격

![2022-10-04-04kali공격](../images/2022-10-04DenialofService/2022-10-04-04kali공격.jpg)

<br>

xp -> cpu 점유율 상태

![2022-10-04-03xp상태](../images/2022-10-04DenialofService/2022-10-04-03xp상태.jpg)

cpu 점유율이 갑자기 크게 올라 갔습니다.

<br>

보안

-  ICMP 패킷 필터링(차단) 

- 일정 시간 내 일정 개수 이상의 ICMP Packet이 들어올 경우 해당 출발지의 ICMP Message 차단 
  - MAC / IP 주소로 차단 - 재조합 패킷의 전체 크기를 검사 
- IP 패킷의 크기를 검사하여 65535이상의 패킷을 필터링 함

<br>

