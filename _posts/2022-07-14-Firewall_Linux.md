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

<br>

##### 리눅스 서버로 ICMP 접근시 기록 (LOG) 를 남긴다

XP에서 -t 옵션을 사용해서 ping을 계속 보내기

![2022-07-14-34xp에서핑보내기PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-34xp에서핑보내기PNG-16578678240362.PNG)

<br>

Linux에서 LOG확인 하기![2022-07-14-35리눅스에서log보기PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-35리눅스에서log보기PNG.PNG)

<br>

tail -f 사용해서 실시간으로 LOG계속 확인하기![2022-07-14-36tail로확인하기PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-36tail로확인하기PNG.PNG)

<br>

LOG에 별도 표기하기![2022-07-14-38log에별도표기하기PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-38log에별도표기하기PNG.PNG)

<br>

XP에서 다시 ping보내고 tail로 확인![2022-07-14-39tail로표기확인PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-39tail로표기확인PNG.PNG)

[ICMP LOG] 뜨는게 확인되면 성공 입니다.

<br>

<br>

##### 로컬 루프백 인터페이스 차단

루프백 인터페이스 확인![2022-07-14-40루프백인터페이스차단하기1PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-40루프백인터페이스차단하기1PNG.PNG)

<br>

루프백 인터페이스 ping으로 확인

루프백 인터페이스는 내부에서만 사용하기 때문에 외부에서 ping을 보낼 수 없습니다. 내부인 Linux에서 확인 하겠습니다.![2022-07-14-41루프백인터페이스차단하기2PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-41루프백인터페이스차단하기2PNG.PNG)

<br>

루프백 인터페이스 차단하기![2022-07-14-42루프백인터페이스차단하기3PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-42루프백인터페이스차단하기3PNG.PNG)

<br>

ping으로 차단 확인하기![2022-07-14-43루프백인터페이스차단하기4PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-43루프백인터페이스차단하기4PNG.PNG)

<br>

##### 사용자 정의 chain 을 만들어서 특정한 상황에 대한 정책을 별도로 만들어서 처리 

icmp 로 접근한 내역은 모두 기록하고 특정 IP  주소(XP) 면 별도 응답없이 차단(DROP) 처리 하겠습니다.

<br>

사용자 체인 추가, 삭제 해보기![2022-07-14-47test체인생성PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-47test체인생성PNG.PNG)

![2022-07-14-48test체인삭제PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-48test체인삭제PNG.PNG)

<br>

built-in chain 을 삭제 시도![2022-07-14-49빌드인체인삭제시도실패PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-49빌드인체인삭제시도실패PNG.PNG)

built-in chain은 사용자가 만든 chain이 아니라 -X 옵션 으로는 삭제가 불가능 합니다.

사용자 chain만 삭제가 가능 하다는 걸 알 수 있는 부분 입니다.

<br>

다시 사용자 chain생성![2022-07-14-50사용자체인생성PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-50사용자체인생성PNG.PNG)

<br>

사용자 정의 chain에 정책 추가![2022-07-14-51사용자체인생성2PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-51사용자체인생성2PNG.PNG)

<br>

INPUT chain 으로 들어오는 작업으로 사용자 정의 chain으로 연결![2022-07-14-52사용자체인생성하고input설정PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-52사용자체인생성하고input설정PNG.PNG)

-j 사용자 정의 chain명을 해주시면 됩니다.

<br>

Linux에서 xp로 ping확인![2022-07-14-53리눅스에서xp로핑실패PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-53리눅스에서xp로핑실패PNG.PNG)





<br>

<br>

<br>

### mangle tables

패킷의 필드를 변조할 수 있는 table입니다.

<br>

Window의 기본 TTL은 128 Linux는 64 입니다.

mangle table을 사용해서 Linux의 TTL 셋팅을 바꿔 보겠습니다.

<br>

mangle table로 TTL셋팅 변경![2022-07-14-44ttl셋팅변경PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-44ttl셋팅변경PNG.PNG)

<br>

바로 XP로 가서 ping을 해보면 원래 TTL이 64로 와야 하지만 128로 오는 것을 확인이 가능합니다.![2022-07-14-45xp에서ttl확인PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-45xp에서ttl확인PNG.PNG)

<br>

XP에서 Wire shark로 확인![2022-07-14-46xp에서ttl와이어샤크로확인PNG](../images/2022-07-14-Firewall_Linux/2022-07-14-46xp에서ttl와이어샤크로확인PNG.PNG)

request reply 확인하면 바뀐점 확인 가능

<br>



















































