# DHCP Relay agent

<br>

구상도![2022-07-29-07-구성도](../images/2022-07-29-DHCP Relay agent/2022-07-29-07-구성도.png)

<br>

Router 인터페이스 설정![2022-07-29-08라우터네트워크](../images/2022-07-29-DHCP Relay agent/2022-07-29-08라우터네트워크.png)

![2022-07-29-01라우터인터페이스](../images/2022-07-29-DHCP Relay agent/2022-07-29-01라우터인터페이스.PNG)

![2022-07-29-02라우터인터페이스2](../images/2022-07-29-DHCP Relay agent/2022-07-29-02라우터인터페이스2.PNG)

하나는 정상적인 ip주소를 넣어 사용하고 다른 한개는 Vmnet1로 설정하고 게이트웨이로 사용하기 위해 위와 같이 설정 했습니다.

<br>

Client 인터페이스 설정![2022-07-29-03클라이언트인터페이스](../images/2022-07-29-DHCP Relay agent/2022-07-29-03클라이언트인터페이스.PNG)

<br>

DHCP Server 인터페이스 설정![2022-07-29-04서버인터페이스](../images/2022-07-29-DHCP Relay agent/2022-07-29-04서버인터페이스.PNG)

<br>

Static Routing![2022-07-29-05스태틱라우팅](../images/2022-07-29-DHCP Relay agent/2022-07-29-05스태틱라우팅.PNG)

조원 2명과 Static Routing을 적용 합니다.

<br>

ping 확인![2022-07-29-06핑확인](../images/2022-07-29-DHCP Relay agent/2022-07-29-06핑확인.PNG)

Client에서 조원들의 Client와 통신이 되는지 확인 합니다.

<br>

DHCP Server에서 DHCP 생성![2022-07-29-09dhcp설정](../images/2022-07-29-DHCP Relay agent/2022-07-29-09dhcp설정.png)

범위는 각자 192.168.x.50 ~ 60으로 공통적으로 설정 하였습니다.

<br>

DNS 설정![2022-07-29-10dhcp설정2](../images/2022-07-29-DHCP Relay agent/2022-07-29-10dhcp설정2.png)

범위옵션 에서 DNS서버로 들어가서 DNS 주소를 추가 해 주도록 합니다.

<br>

DHCP Relay agent 설정 1![2022-07-29-11에이전트1](../images/2022-07-29-DHCP Relay agent/2022-07-29-11에이전트1.png)

Router PC에서 일반 > 우클릭 > 새 라우팅 프로토콜

DHCP 릴레이 에이전트 생성 누르고 확인

<br>

DHCP Relay agent 설정 2

![2022-07-29-12에이전트2](../images/2022-07-29-DHCP Relay agent/2022-07-29-12에이전트2.png)

왼쪽에 DHCP 릴레이 에이전트 생성된거 확인

<br>

DHCP Relay agent 설정 3![2022-07-29-13에이전트3](../images/2022-07-29-DHCP Relay agent/2022-07-29-13에이전트3.png)

새 인터페이스 선택

<br>

DHCP Relay agent 설정 4![2022-07-29-14에이전트4](../images/2022-07-29-DHCP Relay agent/2022-07-29-14에이전트4.png)

이 설정은 discover 수신 전달할 영역을 설정하는 것이기 때문에 아무거나 선택 하시면 안되고 discover에 맞는 영역을 선택 해 주셔야 합니다.

<br>

DHCP Relay agent 설정 5![2022-07-29-15에이전트5](../images/2022-07-29-DHCP Relay agent/2022-07-29-15에이전트5.png)

DHCP Server IP주소를 넣어 주시면 됩니다.

<br>

Wire Shark 확인



Wire Shark를 2개 켜주시면 됩니다.![2022-07-29-16와이어샤크](../images/2022-07-29-DHCP Relay agent/2022-07-29-16와이어샤크.png)

<br>

Wire Shark 확인![2022-07-29-18와이어샤크 (1)](../images/2022-07-29-DHCP Relay agent/2022-07-29-18와이어샤크 (1).PNG)

![2022-07-29-19와이어샤크 (2)](../images/2022-07-29-DHCP Relay agent/2022-07-29-19와이어샤크 (2).PNG)

Discover, Offer, Request, Ack 모두 잘 잡혔습니다.

DHCP가 정상적으로 작동 했다는 뜻입니다.

<br>

Wire Shark를 2개를 킨 이유는 Relay agent가 있고 없고의 차이를 보기 위해서 입니다.

![2022-07-29-20와이어샤크](../images/2022-07-29-DHCP Relay agent/2022-07-29-20와이어샤크.PNG)

왼쪽은 Relay agent가 안 잡힌 모습

오른쪽은 Relay agent가 잡힌 모습 입니다.

이것을 통해서 Relay agent의 역할을 알 수 있습니다.

offer의 기준은 discover 의 relayagent IP address 와 NA  가 같은 

범위를 찾아서 offer 한다. 라고 할 수 있겠습니다.

<br>