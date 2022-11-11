# LVS(Linux Virtual Server)

![2022-11-11-01lvs](../images/2022-11-11-LVS(Linux Virtual Server)/2022-11-11-01lvs-1668148911099-2.jpg)

<br>

구성도

![2022-11-11-02구성도](../images/2022-11-11-LVS(Linux Virtual Server)/2022-11-11-02구성도.jpg)

<br>

###### Director 기본 설정

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
```

<br>

Virtual IP 설정

```
ifconfig ens32:1 172.16.0.10 netmask 255.255.255.0
```

![2022-11-11-04vip](../images/2022-11-11-LVS(Linux Virtual Server)/2022-11-11-04vip.jpg)

<br>