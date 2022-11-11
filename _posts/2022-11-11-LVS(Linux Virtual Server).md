# LVS(Linux Virtual Server)

![2022-11-11-01lvs](../images/2022-11-11-LVS(Linux Virtual Server)/2022-11-11-01lvs-1668148911099-2.jpg)

<br>

구성도

![2022-11-11-02구성도](../images/2022-11-11-LVS(Linux Virtual Server)/2022-11-11-02구성도.jpg)

<br>

##### Director 기본 설정

![2022-11-11-03통신체크](../images/2022-11-11-LVS(Linux Virtual Server)/2022-11-11-03통신체크.jpg)

<br>

LVS 패키지 설치

```
yum -y install ipvsadm
```

<br>

IP Forwarding

```
vi /etc/sysctl.conf

net.ipv4.ip_forward=1      << 내용 추가

[root@localhost ~]# sysctl -p      << 잘 들어갔는지 확인
net.ipv4.ip_forward = 1                
```

<br>

Virtual IP 설정

```
ifconfig ens32:1 172.16.0.10 netmask 255.255.255.0
```

![2022-11-11-04vip](../images/2022-11-11-LVS(Linux Virtual Server)/2022-11-11-04vip.jpg)

![2022-11-11-05핑체크](../images/2022-11-11-LVS(Linux Virtual Server)/2022-11-11-05핑체크.jpg)

<br>

ipvsadm 설정

```
iptables -F        << 방화벽 해제

부하분산 설정
Virtual IP 10 -> RealIP 11) 12) , 80

ipvsadm -A -t 172.16.0.10:80 -s rr     << 172.16.0.10:80 으로 들어오는 연결은 rr(Round robin) 이라는 방식으로 부하분산 할것  

Virtual IP 10 -> RealIP 11)
ipvsadm -a -t 172.16.0.10:80 -r 172.16.0.11:80

Virtual IP 10 -> RealIP 12) 
ipvsadm -a -t 172.16.0.10:80 -r 172.16.0.12:80
```

![2022-11-11-06설정](../images/2022-11-11-LVS(Linux Virtual Server)/2022-11-11-06설정.jpg)

<br>

<br>

<br>

##### RealServer 1: 172.16.0.11, 12] 기본 설정

![2022-11-11-07기본설정](../images/2022-11-11-LVS(Linux Virtual Server)/2022-11-11-07기본설정.jpg)

![2022-11-11-08기본설정](../images/2022-11-11-LVS(Linux Virtual Server)/2022-11-11-08기본설정-1668154048068-11.jpg)

<br>

패키지 설치

```
yum -y install httpd arptables_jf
```

<br>

httpd 설정

```
172.16.0.11
[root@localhost ~]# echo 11 > /var/www/html/index.html
[root@localhost ~]# cat /var/www/html/index.html
11

172.16.0.12
[root@localhost ~]# echo 12 > /var/www/html/index.html
[root@localhost ~]# cat /var/www/html/index.html
12
```

![2022-11-11-09httpd](../images/2022-11-11-LVS(Linux Virtual Server)/2022-11-11-09httpd.jpg)

<br>

Virtual IP 설정 

```
ifconfig ens32:1 172.16.0.10 netmask 255.255.255.0
```

![2022-11-11-10ipasdam](../images/2022-11-11-LVS(Linux Virtual Server)/2022-11-11-10ipasdam.jpg)

<br>

arptables_jf 설정 

```
VIP 를 찾는 arp는  차단
arptables -A INPUT -d 172.16.0.10 -j DROP 

172.16.0.10 으로 응답시 arp 로 알아낸 172.16.0.10 의 MAC 주소를 172.16.0.11, 12 의 MAC 주소로 대체
 arptables -A OUTPUT -s 172.16.0.10 -j mangle --mangle-ip-s 172.16.0.11, 12
```

![2022-11-11-12arptables](../images/2022-11-11-LVS(Linux Virtual Server)/2022-11-11-12arptables.jpg)

![2022-11-11-11arptables](../images/2022-11-11-LVS(Linux Virtual Server)/2022-11-11-11arptables.jpg)

<br>



