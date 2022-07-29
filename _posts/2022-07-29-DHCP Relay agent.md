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

