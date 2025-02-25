# Routing Linux

### 구성도

![2022-07-13-02패킷구성도](../images/2022-07-13-Routing Linux/2022-07-13-02패킷구성도.PNG)

Router를 Linux라고 생각하고 각각 xp환경과 2003 환경에 연결하여 서로 다른 망끼리 통신이 되도록 구축 하겠습니다.

조원은 3명이며 한명당 망 1개씩 구축 하였습니다.

<br><br><br>

우선 VM ware의 network환경을 설정 하겠습니다.

VMnet2 Host-only를 만들어 놓겠습니다.

![2022-07-13-01vmnet2만들기](../images/2022-07-13-Routing Linux/2022-07-13-01vmnet2만들기.PNG)

xp와 2003환경도 설정 하겠습니다.

![2022-07-13-01xp설정](../images/2022-07-13-Routing Linux/2022-07-13-01xp설정.PNG)

![2022-07-13-012003설정](../images/2022-07-13-Routing Linux/2022-07-13-012003설정.PNG)

<br><br><br>

그리고 Linux에 인터페이스를 추가 하겠습니다.

![2022-07-13-03리눅스인터페이스추가](../images/2022-07-13-Routing Linux/2022-07-13-03리눅스인터페이스추가.PNG)

<br><br><br>

Linux에 접속해서 인터페이스가 제대로 추가 되었는지 확인을 해 봅니다.

![2022-07-13-04인터페이스추가확인](../images/2022-07-13-Routing Linux/2022-07-13-04인터페이스추가확인.PNG)

<br><br><br>

원활한 통신을 위해 조원들과 network address가 겹치지 않도록 ip주소를 설정 하겠습니다.

![2022-07-13-05리눅스ip정보변경](../images/2022-07-13-Routing Linux/2022-07-13-05리눅스ip정보변경.PNG)

<br><br><br>

변경을 하고 `systemctl restart network` 를 입력하여 네트워크를 재시작 하겠습니다.

![2022-07-13-06systemctl restart network](../images/2022-07-13-Routing Linux/2022-07-13-06systemctl restart network.PNG)

<br><br><br>

조원들과 통신이 잘 되는지 ping을 확인해 보겠습니다.

200.200.200.163 200.200.200.169 둘 다 잘 가는것을 확인을 합니다.

![2022-07-13-07조원들과 ping확인](../images/2022-07-13-Routing Linux/2022-07-13-07조원들과 ping확인.PNG)

<br><br><br>

아까 만들었던 인터페이스의 설정을 변경 하겠습니다.

ifcfg-ens32 파일을 확인하고 복사를 ifcfg-ens33으로 설정 합니다.

![2022-07-13-08ens32확인](../images/2022-07-13-Routing Linux/2022-07-13-08ens32확인.PNG)

![2022-07-13-09ens32를ens33을카피후확인](../images/2022-07-13-Routing Linux/2022-07-13-09ens32를ens33을카피후확인.PNG)

<br><br><br>

복사를 한 뒤 vi로 들어가서 설정을 변경 합니다.

이름과 UUID IP주소를 바꿔야 합니다. UUID는 처음에 인터페이스 확인 차 입력한 명령어  `nmcli connection` 로 확인 할 수 있습니다.

![2022-07-13-10ens33설정](../images/2022-07-13-Routing Linux/2022-07-13-10ens33설정.PNG)

<br><br><br>

`systemctl restart network` 를 한 뒤에 ifconfig로 확인해 보겠습니다.

![2022-07-13-11ens33설정ifconfig로확인](../images/2022-07-13-Routing Linux/2022-07-13-11ens33설정ifconfig로확인.PNG)

<br><br><br>

똑같이 ens34를 만들면 됩니다.

ens33 파일을 복사해서 ens34 파일로 만들겠습니다.

![2022-07-13-12ens34설정하기](../images/2022-07-13-Routing Linux/2022-07-13-12ens34설정하기.PNG)

<br><br><br>

vi로 들어가서 설정을 변경 하는데 ens33과 다르게 UUID를 빼고 MAC주소를 넣어서 설정해 보겠습니다.

ifconfig로 ens34에 있는 MAC주소를 복사해서 HWADDR을 입력 해주시면 됩니다.

![2022-07-13-13ens34설정하기](../images/2022-07-13-Routing Linux/2022-07-13-13ens34설정하기.PNG)

<br><br><br>

다시 나가서 `systemctl restart network` 를 한 뒤에 ifconfig로 확인해 보겠습니다.

![2022-07-13-14ens34설정확인](../images/2022-07-13-Routing Linux/2022-07-13-14ens34설정확인.PNG)

<br><br><br>

바꾼 설정들이 통신이 잘 되나 확인해 보겠습니다.

ens33은 xp로 연결이 되어있고 ens34는 2003 환경에 연결이 되어 있습니다.

<br><br><br>

두 군데 다 통신이 잘 되는것을 확인 합니다.

![2022-07-13-16ping확인xp](../images/2022-07-13-Routing Linux/2022-07-13-16ping확인xp.PNG)

![2022-07-13-15ping확인2003](../images/2022-07-13-Routing Linux/2022-07-13-15ping확인2003.PNG)

<br><br><br>

이제 xp환경에서 Router와 Gateway에 ping이 잘 가는지 확인 해보겠습니다.

<br>

Router와 Gateway에 ping이 잘 가지만 아직 2003과는 ping이 안되는 상황입니다.

![2022-07-13-16pxp에서게이트웨이핑확인](../images/2022-07-13-Routing Linux/2022-07-13-16pxp에서게이트웨이핑확인.PNG)

![2022-07-13-16pxp에서라우터로핑확인](../images/2022-07-13-Routing Linux/2022-07-13-16pxp에서라우터로핑확인.PNG)

<br>

Router역할을 하는 Linux에 가서 Routing table을 만들어 보겠습니다.

sysctl.conf 파일에 들어가서 맨 밑에 net.ipv4.ip_forward=1 만 추가해 주겠습니다.

![2022-07-13-18라우터가되도록설정하기2](../images/2022-07-13-Routing Linux/2022-07-13-18라우터가되도록설정하기2.PNG)

![2022-07-13-17라우터가되도록설정하기1](../images/2022-07-13-Routing Linux/2022-07-13-17라우터가되도록설정하기1.PNG)

<br>

추가한 후 네트워크를 재시작 해주시면 net.ipv4.ip_forward=0 에서 net.ipv4.ip_forward=1로 바뀌게 됩니다.

![2022-07-13-18라우터가되도록설정하기3](../images/2022-07-13-Routing Linux/2022-07-13-18라우터가되도록설정하기3.PNG)

<br>

Routing table을 확인 해 보겠습니다.

xp, 2003 둘 다 잘 생성되어 있습니다.

![2022-07-13-19라우팅테이블확인](../images/2022-07-13-Routing Linux/2022-07-13-19라우팅테이블확인.PNG)

<br>

xp환경으로 가서 2003에 ping을 보내 보겠습니다.

<br>

Routing table을 설정하니 xp에서 2003으로 통신이 됩니다.

![2022-07-13-20라우팅후xp에서2003ping확인](../images/2022-07-13-Routing Linux/2022-07-13-20라우팅후xp에서2003ping확인.PNG)

<br>

이제 조원들과 Routing을 한 후에 통신을 확인해 보겠습니다.

route add -net Network Address netmask xxx.xxx.xxx.xxx gw xxx.xxx.xxx.xxx 을 입력하면 됩니다.

![2022-07-13-21조원ip주소라우팅하고통신확인](../images/2022-07-13-Routing Linux/2022-07-13-21조원ip주소라우팅하고통신확인-165770808993627.PNG)

<br>

이제 조원들의 남은 ip주소도 마저 다 넣고 통신을 확인해 보겠습니다.

<br>

전체적으로 잘 가는 모습이 보입니다.

![2022-07-13-22조원ip주소라우팅하고통신확인조원전체](../images/2022-07-13-Routing Linux/2022-07-13-22조원ip주소라우팅하고통신확인조원전체.PNG)

<br>

마지막으로 Routing table을 보여드리고 마치겠습니다.

![2022-07-13-23라우팅테이블확인](../images/2022-07-13-Routing Linux/2022-07-13-23라우팅테이블확인.PNG)
