---
categories : IT
tag : [IT,DHCP Service]
---



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

구상도![2022-07-28-24구상도](../images/2022-07-28-DHCP Service/2022-07-28-24구상도.PNG)

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

![2022-07-28-19와이어샤크내용](../images/2022-07-28-DHCP Service/2022-07-28-19와이어샤크내용.PNG)

Wire Shark를 보면 Discover, Offer, Request, Ack가 보이는데 이것들은 DHCP 메시지 입니다. (주소 할당 순서)

동작 방식은 위의 사진대로 Client가 IP주소를 Server에 요청하면 Server가 응답하며 IP주소를 주는 방식 입니다.

이 방식은 Ack가 끝날때 까지는 주소를 사용할 수 없습니다.!!!!

<br>

이 과정을 하나씩 뜯어서 보면

Discover![2022-07-28-20discover](../images/2022-07-28-DHCP Service/2022-07-28-20discover.PNG)

Client가 Server에 IP주소를 달라고 요청하는 과정입니다.

<br>

Offer![2022-07-28-21offer](../images/2022-07-28-DHCP Service/2022-07-28-21offer.PNG)

Server가 Client에게 IP주소를 주는 모습 입니다.

<br>

Request![2022-07-28-22Request](../images/2022-07-28-DHCP Service/2022-07-28-22Request.PNG)

A를 가진 Client가 C에게 offer 받은 주소 B를 사용 하겠다 라는 뜻 입니다.

<br>

Ack![2022-07-28-23ack](../images/2022-07-28-DHCP Service/2022-07-28-23ack.PNG)

Server에서 사용 요청한 172.16.0.50를 승인을 해주고

사용기간은 8일(lease time)

4일(50% ,Renewal time) 이내에 재사용 요청 (request) 만약에 못하

면 7일(87.5% rebinding time) 정도까지 하되 그안에 못하면 8일

(lease time)되면 취소 라는 뜻의 내용들이 적혀 있습니다.

<br>

<br>

<br>

###  DHCP 임대기간 - 자동 갱신

<br>

현재 임대시간 확인![2022-07-28-26임대기간확인ipconfig all](../images/2022-07-28-DHCP Service/2022-07-28-26임대기간확인ipconfig all.PNG)

Client에서 ipconfig /all로 확인

<br>

Server에서 lease time 2분으로 변경![2022-07-28-25임대기간변경](../images/2022-07-28-DHCP Service/2022-07-28-25임대기간변경.PNG)

<br>

주소 임대 해제![2022-07-28-28릴리즈l](../images/2022-07-28-DHCP Service/2022-07-28-28릴리즈l.PNG)

<br>

주소 재임대![2022-07-28-27renewl](../images/2022-07-28-DHCP Service/2022-07-28-27renewl.PNG)

![2022-07-28-29재확인](../images/2022-07-28-DHCP Service/2022-07-28-29재확인.PNG)

주소를 재임대 하면 임대 기간이 2분으로 바뀐것이 확인 가능 합니다.

<br>

Wire Shark 확인![2022-07-28-30와이어샤크로확인](../images/2022-07-28-DHCP Service/2022-07-28-30와이어샤크로확인.PNG)

Request -> Ack가 2분 간격으로 이뤄지는데 계속 갱신이 되는 과정이 잡 Wire Shark에 나타난 부분 입니다.

<br>

DHCP 작업중지![2022-07-28-31일시중지](../images/2022-07-28-DHCP Service/2022-07-28-31일시중지.PNG)

일시중지 를 한번 해보고 Wire Shark를 보겠습니다.

<br>

Wire Shark 확인![2022-07-28-32와이어샤크확인](../images/2022-07-28-DHCP Service/2022-07-28-32와이어샤크확인.PNG)

계속 renewal을 시도 하다가 rebinding time 임대해제 된 모습 입니다.

<br>

Client 확인![2022-07-28-33CMD확인](../images/2022-07-28-DHCP Service/2022-07-28-33CMD확인.PNG)

APIPA - Bclass의 bogon IP주소로 설정이 된 모습 입니다.

<br>

filter를 해제하고 Wire Shark를 다시 보겠습니다.![2022-07-28-34필터해제와이어샤크](../images/2022-07-28-DHCP Service/2022-07-28-34필터해제와이어샤크.PNG)

Gratuitous ARP가 보입니다.

Gratuitous ARP는 APIPA 겹치는것 또는 일반적으로 컴퓨터 시작시 IP주소 중복 체크를 합니다.

<br>

<br>

<br>

### DHCP 임대기간 - 자동 갱신

DHCP 다시 시작![2022-07-28-36다시시작와이어샤크](../images/2022-07-28-DHCP Service/2022-07-28-36다시시작와이어샤크.PNG)

DHCP를 다시 시작하면 Wire Shark에 inform이 잡히는데 이게 다시 시작하는 과정 입니다.

<br>

임대기간 변경![2022-07-28-35임대기간변경](../images/2022-07-28-DHCP Service/2022-07-28-35임대기간변경.PNG)

임대기간을 다시 8일로 변경 하겠습니다.

<br>

주소 재 임대![2022-07-28-37주소재임대](../images/2022-07-28-DHCP Service/2022-07-28-37주소재임대.PNG)

ipconfig /release      ipconfig/renew로 재임대 해주시면 됩니다.

<br>

재 임대 확인 ipconfig /all![2022-07-28-38재임대확인](../images/2022-07-28-DHCP Service/2022-07-28-38재임대확인.PNG)

<br>

수동 갱신 ipconfig /renew![2022-07-28-39수동갱신](../images/2022-07-28-DHCP Service/2022-07-28-39수동갱신.PNG)

<br>

Wire Shark 확인![2022-07-28-40수동갱신확인](../images/2022-07-28-DHCP Service/2022-07-28-40수동갱신확인.PNG)

Client에서 수동 갱신 후 Server에서 Wire Shark를 확인 해 보시면 Request Ack가 확인 가능 합니다.

<br>

<br>

<br>

### DHCP 임대주소가 중복되는경우

구상도![2022-07-28-45디클라인구상도](../images/2022-07-28-DHCP Service/2022-07-28-45디클라인구상도.PNG)

<br>

이번에는 임대주소가 중복되는 경우를 보기 위해 172.16.0.50을 사용하는 컴퓨터를 한 대 더 만들어 주시면 됩니다.

<br>

Server에서 DHCP 정지![2022-07-28-41일시중지](../images/2022-07-28-DHCP Service/2022-07-28-41일시중지.PNG)

<br>

추가한 컴퓨터 IP주소 변경![2022-07-28-42설정변경](../images/2022-07-28-DHCP Service/2022-07-28-42설정변경.PNG)

<br>

Server에서 DHCP 사용![2022-07-28-44재시작확인](../images/2022-07-28-DHCP Service/2022-07-28-44재시작확인.PNG)

<br>

임대주소 중복 확인![2022-07-28-43디클라인](../images/2022-07-28-DHCP Service/2022-07-28-43디클라인.PNG)

DHCP Decline이 임대주소가 중복이 되었다는 뜻 입니다.

이렇게 임대주소 중복이 확인 가능 합니다.

<br>

<br>

<br>

