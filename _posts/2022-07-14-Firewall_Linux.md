# Firewall - Linux

<br>

### Linux - iptables

Linux 방화벽에는 대표적으로 iptables가 있습니다.

<br>

##### ip tables 란 

- Linux Kernel 내부의 네트워크 관련 프레임워크 

- 네트워크 패킷을 제어할 수 있는 기능을 제공 함

이러한 기능이 있는 ip tables의 기본적인 문법 구조부터 확인해 보겠습니다.

<br>

<br>

##### ip tables 문법 구조 확인하기

우선 ip tables를 test할 환경부터 설정 하겠습니다.

VM ware에 Linux, xp 2개의 환경을 사용 하겠습니다.

<br>

Linux에 `yum -y install httpd` 로 http를 먼저 설치하기

![2022-07-14-01httpd설치](../images/2022-07-14-Firewall_Linux/2022-07-14-01httpd설치.PNG)

<br>

httpd와 ip tables를 실행 시키기

![2022-07-14-02httpd실행](../images/2022-07-14-Firewall_Linux/2022-07-14-02httpd실행.PNG)

<br>

XP로 가서 httpd 실행 되는지 확인하기

![2022-07-14-03httpd실행확인](../images/2022-07-14-Firewall_Linux/2022-07-14-03httpd실행확인.PNG)

<br>

ip tables 시작

![2022-07-14-04iptables실행](../images/2022-07-14-Firewall_Linux/2022-07-14-04iptables실행.PNG)

<br>

다시 XP로 가서 httpd 확인

![2022-07-14-05iptables실행후 httpd재확인](../images/2022-07-14-Firewall_Linux/2022-07-14-05iptables실행후 httpd재확인.PNG)

ip tables를 실행하자 마자 httpd가 실행이 되지 않음을 확인 할 수 있습니다.

<br>

filter table 의 목록 확인

![2022-07-14-06iptables목록확인](../images/2022-07-14-Firewall_Linux/2022-07-14-06iptables목록확인.PNG)

현재 ip tables의 실행 목록을 볼 수 있는 간단한 명령어 입니다.

<br>

ip tables의 Chain 별 접근제어 방식 종류에는

- black list : 기본적으로 모든 대상을 허용(ACCEPT)하고 차단(DROP)할 대상을 제어 합니다.
- white list : 기본적으로 모든 대상을 차단(DROP)하고 허용(ACCEPT)할 대상을 제어 합니다.

이번에는 white list 제어 방식을 사용하여 실습 해 보겠습니다.

<br>

<br>

##### White list - ICMP 허용

우선 ip tables를 초기화 하고 확인

![2022-07-14-07iptables초기화후 확인](../images/2022-07-14-Firewall_Linux/2022-07-14-07iptables초기화후 확인.PNG)

-F 명령어로 초기화를 해주고 -L로 위의 사진과 비교 해보면 초기화가 됬구나 확인이 가능 합니다.

<br>

INPUT chain 의 기본정책은 DROP or ACCEPT로 정의 할 수 있습니다.

이번에는 white list 방식을 사용할 것이기 때문에 DROP을 사용 하겠습니다.

<br>

INPUT chain을 DROP으로 설정하고 확인

![2022-07-14-08chain drop으로 설정](../images/2022-07-14-Firewall_Linux/2022-07-14-08chain drop으로 설정.PNG)

<br>

XP에서 Linux로 ping 확인

![2022-07-14-09XP에서핑확인](../images/2022-07-14-Firewall_Linux/2022-07-14-09XP에서핑확인.PNG)

아직 ping이 전달되지 않음.

<br>

ip tables에서 ICMP허용 하기

![2022-07-14-10icmp허용](../images/2022-07-14-Firewall_Linux/2022-07-14-10icmp허용.PNG)

white list 방식을 사용하고 있는 상태이기 때문에 ICMP만 ACCEPT로 허용을 해줍니다.

<br>

XP에서 다시 ping확인

![2022-07-14-11ping확인](../images/2022-07-14-Firewall_Linux/2022-07-14-11ping확인.PNG)

ICMP를 허용하니 ping이 잘 전달되는 모습

<br>

<br>

##### White list - SSH

XP에서 putty를 사용해서 SSH로 Linux 접속해 보기

![2022-07-14-12ssh확인하기](../images/2022-07-14-Firewall_Linux/2022-07-14-12ssh확인하기.PNG)

접속 불가능

<br>

ip tables에서 SSH 허용하고 확인

![2022-07-14-13SSH허용하기](../images/2022-07-14-Firewall_Linux/2022-07-14-13SSH허용하기.PNG)

<br>

XP에서 putty로 다시 SSH 접근

![2022-07-14-14SSH접근성공PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-14SSH접근성공PNG.PNG)

성공!!!!

<br>

##### White list - SSH

###### SSH를 172.16.0.1 에서만 허용하기

<br>

SSH를 삭제

![2022-07-14-15line명령어 2행삭제PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-15line명령어 2행삭제PNG.PNG)

-L 명령어 뒤에 --line 옵션을 쓰면 행number가 보입니다.

-D 명령어를 사용해서 SSH가 허용되어 있는 2행을 삭제 합니다.

<br>

삭제된거 확인![2022-07-14-16삭제확인PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-16삭제확인PNG.PNG)

<br>

172.16.0.1만 SSH허용 하겠다는 정책을 추가하기![2022-07-14-17옵션주면서SSH다시허용PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-17옵션주면서SSH다시허용PNG.PNG)

<br>

XP에서 putty로 SSH접근 해보기![2022-07-14-18XP에서접근실패PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-18XP에서접근실패PNG.PNG)

접근실패

<br>

<br>

##### White list - Httpd 허용

ip tables에서 httpd 허용하기![2022-07-14-19httpd허용확인PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-19httpd허용확인PNG.PNG)

httpd 허용된거 확인

<br>

XP에서 확인해 보기![2022-07-14-20httpd성공PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-20httpd성공PNG.PNG)

httpd 허용 성공!!

<br>

<br>

##### -I Insert 활용하기

목록확인![2022-07-14-21목록확인PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-21목록확인PNG-165780113218828.PNG)

<br>

3번째행 지우고 확인![2022-07-14-22세번째지우고확인PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-22세번째지우고확인PNG-165780115840431.PNG)

<br>

맨 앞에 Insert하기![2022-07-14-23행제일위로인써트PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-23행제일위로인써트PNG-165780118480834.PNG)

<br>

다시 지우고 확인![2022-07-14-24첫번째행지우기PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-24첫번째행지우기PNG.PNG)

![2022-07-14-25목록확인PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-25목록확인PNG.PNG)

<br>

2번째 행 앞에 Insert하기![2022-07-14-26두번째행앞에인써트PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-26두번째행앞에인써트PNG.PNG)

<br>

<br>

##### REJECT , DROP 차이

ip tables 초기화![2022-07-14-27다시초기화PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-27다시초기화PNG-165780136014440.PNG)

<br>

Chain INPUT DROP에서 ACCEPT로 바꾸기![2022-07-14-28정책바꾸기ㅣPNG](../images/2022-07-14-Firewall_Linux/2022-07-14-28정책바꾸기ㅣPNG.PNG)

<br>

Httpd 차단![2022-07-14-29httpd차단PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-29httpd차단PNG.PNG)

<br>

XP에서 와이어샤크 켜고 http://172.16.0.121 으로 접속하고 와이어샤크에 172.16.0.121 은 필터해서 출력하기![2022-07-14-30와이어샤크](../images/2022-07-14-Firewall_Linux/2022-07-14-30와이어샤크-165780167643045.PNG)

<br>

Httpd 차단 삭제![2022-07-14-30차단해제](../images/2022-07-14-Firewall_Linux/2022-07-14-30차단해제.PNG)

<br>

REJECT  사용하면서 메시지를 출력하도록 옵션 설정![2022-07-14-32rejec설정PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-32rejec설정PNG.PNG)

<br>

XP에서 와이어샤크 켜고 http://172.16.0.121 으로 접속하고 와이어샤크에 172.16.0.121 은 필터해서 출력하기![2022-07-14-33와이어샤크확인PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-33와이어샤크확인PNG.PNG)

ICMP 확인하기

<br>





































