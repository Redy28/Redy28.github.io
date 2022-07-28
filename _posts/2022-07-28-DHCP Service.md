---
categories: IT
tag: [IT,DHCP Service]
---
# DHCP Service

<br>

##### Host 설정 종류

###### maual configuration : 직접 입력

![2022-07-28-01확인하기1번](../images/2022-07-28-DHCP Service/2022-07-28-01확인하기1번.PNG)

win + r 을 누르고 ncpa.cpl을 누르고 속성에 들어 가시면 나오는데 여기에 직접 사용할 주소를 입력 하는 방법 입니다.

<br>

###### dynamic configuration : 다른 서버에서 주소를 부여받는 방법![2022-07-28-03확인하기3번](../images/2022-07-28-DHCP Service/2022-07-28-03확인하기3번.PNG)

![2022-07-28-02확인하기2번](../images/2022-07-28-DHCP Service/2022-07-28-02확인하기2번.PNG)

자신이 사용할 주소를 직접 입력 하는게 아니라 다른 서버에서 주소를 부여 받아오는 방법 입니다.

 <br>

###### auto configuration![2022-07-28-04확인하기4번](../images/2022-07-28-DHCP Service/2022-07-28-04확인하기4번.PNG)

중간에 Autoconfiguration이 보이는데 이것은 주소를 서버로 부터 부여받지 못하는 경우 통신을 위해 자동으로 입력되는 주소 입니다.

 <br>

###### APIPA : B class 의 bogon IP주소 



