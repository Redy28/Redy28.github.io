# ActiveHost Scanning 

<br>

##### ping

![2022-09-21-53ping](C:\Users\home\Desktop\github\깃허브 이미지\2022-09-20-정보수집\2022-09-21-53ping.PNG)

<br>

##### faipScanner.exe

![2022-09-21-47아이피스캐닝](C:\Users\home\Desktop\github\깃허브 이미지\2022-09-20-정보수집\2022-09-21-47아이피스캐닝.PNG)

<br>

##### arping

대상 컴퓨터의 Mac 주소 확인 

![2022-09-21-54arping](C:\Users\home\Desktop\github\깃허브 이미지\2022-09-20-정보수집\2022-09-21-54arping.PNG)

<br>

##### fping

sweeping : 네트워크 내에서 활성화된 시스템을 찾는것

![2022-09-21-55farp](C:\Users\home\Desktop\github\깃허브 이미지\2022-09-20-정보수집\2022-09-21-55farp.PNG)

<br>

##### nmap

구상도

![2022-09-21-56구상도](C:\Users\home\Desktop\github\깃허브 이미지\2022-09-20-정보수집\2022-09-21-56구상도.PNG)

<br>

sP : ping scan  , 로컬네트워크 ,  arp ,  원격네트워크는  icmp

![2022-09-21-48nmap](C:\Users\home\Desktop\github\깃허브 이미지\2022-09-20-정보수집\2022-09-21-48nmap.PNG)

![2022-09-21-49nmap](C:\Users\home\Desktop\github\깃허브 이미지\2022-09-20-정보수집\2022-09-21-49nmap.PNG)

<br>

외부로 ping 보낼때

![2022-09-21-51외부](C:\Users\home\Desktop\github\깃허브 이미지\2022-09-20-정보수집\2022-09-21-51외부.PNG)

![2022-09-21-52외부icmp](C:\Users\home\Desktop\github\깃허브 이미지\2022-09-20-정보수집\2022-09-21-52외부icmp.PNG)

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

