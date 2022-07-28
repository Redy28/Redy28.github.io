# DHCP Service

<br>

### Host 설정 종류

##### maual configuration : 직접 입력

![2022-07-28-01확인하기1번](../images/2022-07-28-DHCP Service/2022-07-28-01확인하기1번.PNG)

win + r 을 누르고 ncpa.cpl을 누르고 속성에 들어 가시면 나오는데 여기에 직접 사용할 주소를 입력 하는 방법 입니다.

<br>

##### dynamic configuration : 다른 서버에서 주소를 부여받는 방법![2022-07-28-03확인하기3번](../images/2022-07-28-DHCP Service/2022-07-28-03확인하기3번.PNG)

![2022-07-28-02확인하기2번](../images/2022-07-28-DHCP Service/2022-07-28-02확인하기2번.PNG)

자신이 사용할 주소를 직접 입력 하는게 아니라 다른 서버에서 주소를 부여 받아오는 방법 입니다.

 <br>

##### auto configuration![2022-07-28-04확인하기4번](../images/2022-07-28-DHCP Service/2022-07-28-04확인하기4번.PNG)

중간에 Autoconfiguration이 보이는데 이것은 주소를 서버로 부터 부여받지 못하는 경우 통신을 위해 자동으로 입력되는 주소 입니다.

 <br>

##### APIPA : B class 의 bogon IP주소 

###### bogon IP주소 종류

 <br>

###### zero 주소

특수 목적으로 사용되는 예약 주소

###### Network 주소

각 네트워크를 대표하는 네트워크 주소

###### Direct Brodcast 주소

각 네트워크에서만 사용되는 Brodcast 주소

###### Local Brodcast 주소

전체 네트워크에서 사용되는 Brodcast 주소

###### Multicast 주소

Multicast Group을 위해 할당되는 주소

###### Loopback 주소

자기자신을 나타내는 로컬 주소

###### 자동 대체 할당 주소

자동 할당에 실패했을 때 임의로 할당하는 주소

###### 사설 IP 주소

공식적인 승인 없이 임의로 사용할 수 있는 주소

내부 통신용으로만 사용 가능

 <br>

##### TCP/IP configuration![2022-07-28-05확인하기5번](../images/2022-07-28-DHCP Service/2022-07-28-05확인하기5번.PNG)

![2022-07-28-06확인하기6번](../images/2022-07-28-DHCP Service/2022-07-28-06확인하기6번.PNG)

IP address, Subnet mask, routing(G/W), DNS Server 는 네트워크내에서의 유일성을 위해 필요

 <br>

 <br>

##### DHCP  서버 만들기

구상도

 <br>

Client 설정![2022-07-28-07사용안함](../images/2022-07-28-DHCP Service/2022-07-28-07사용안함.PNG)

ncpa.cpl > 로컬 영역 연결 사용안함 

 <br>

Server 구성 1![2022-07-28-08dhcp만들기](../images/2022-07-28-DHCP Service/2022-07-28-08dhcp만들기.PNG)

제어판 > 프로그램 추가 제거 > Windows 구성요소 > 네트워킹 서비스 > DHCP 서비스 추가

 <br>

Server 구성 2![2022-07-28-09dhcp만들기2](../images/2022-07-28-DHCP Service/2022-07-28-09dhcp만들기2.PNG)

관리도구 > DHCP

컴퓨터 이름 > 새 범위 > 이름 : 172.16.0.50~60 >

<br>

Server 구성 3![2022-07-28-10dhcp만들기3](../images/2022-07-28-DHCP Service/2022-07-28-10dhcp만들기3.PNG)

<br>

Server 구성 4![2022-07-28-11dhcp만들기4](../images/2022-07-28-DHCP Service/2022-07-28-11dhcp만들기4.PNG)

<br>

Server 구성 5![2022-07-28-12dhcp만들기5](../images/2022-07-28-DHCP Service/2022-07-28-12dhcp만들기5.PNG)

<br>

Server 구성 6![2022-07-28-13dhcp만들기6](../images/2022-07-28-DHCP Service/2022-07-28-13dhcp만들기6.PNG)

<br>

Server 구성 7![2022-07-28-14dhcp만들기7](../images/2022-07-28-DHCP Service/2022-07-28-14dhcp만들기7.PNG)

<br>

Server 구성 8![2022-07-28-15dhcp만들기8](../images/2022-07-28-DHCP Service/2022-07-28-15dhcp만들기8.PNG)

완료 입니다.

<br>

2003에서 Wire Shark 실행![2022-07-28-17와이어샤크](../images/2022-07-28-DHCP Service/2022-07-28-17와이어샤크.PNG)

Filter에 bootp 입력

<br>

Client 네트워크 연결 ![2022-07-28-16클라이언트연결](../images/2022-07-28-DHCP Service/2022-07-28-16클라이언트연결.PNG)

<br>

Wire Shark 확인![2022-07-28-18와이어샤크확인](../images/2022-07-28-DHCP Service/2022-07-28-18와이어샤크확인.PNG)



