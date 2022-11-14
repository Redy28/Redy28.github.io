# Redundancy

##### 이중화

![2022-11-11-01이중화](../images/2022-11-11-Redundancy/2022-11-11-01이중화.jpg)

![2022-11-11-02이중화](../images/2022-11-11-Redundancy/2022-11-11-02이중화.jpg)

<br>

##### STP (Spanning Tree Protocol)

![2022-11-11-03stp](../images/2022-11-11-Redundancy/2022-11-11-03stp.jpg)

<br>

###### BPDU(Bridge PDU)

![2022-11-11-04bpdu](../images/2022-11-11-Redundancy/2022-11-11-04bpdu.jpg)

![2022-11-11-05bpdu](../images/2022-11-11-Redundancy/2022-11-11-05bpdu.jpg)

![2022-11-11-06경로](../images/2022-11-11-Redundancy/2022-11-11-06경로.jpg)

<br>

###### 경로 선출 단계

Root Bridge(=switch) 선출 

```
하나의 네트워크에서 기준이 되고, STP관리를 담당할 Root Switch선출
BPDU의 Bridge ID가 제일 낮은 Switch가 선택 됨
Bridge ID = 우선순위(priority) + MAC
1 순위 → 우선순위 낮은 장비
2 순위 → MAC 주소가 낮은 장비
```

<br>

전체 Switch 정보 확인

![2022-11-11-09스패닝](../images/2022-11-11-Redundancy/2022-11-11-09스패닝.jpg)

<br>

우선순위를 변경하여 root switch 를 변경

```
switch1(config)#spanning-tree vlan 1 priority 28672
```

![2022-11-11-07변경](../images/2022-11-11-Redundancy/2022-11-11-07변경.jpg)

<br>

원상복구

```
switch1(config)#spanning-tree vlan 1 priority 32768
```

![2022-11-11-08복구](../images/2022-11-11-Redundancy/2022-11-11-08복구.jpg)

<br>

Root Port 선출

```
Root Switch가 전송하는 BDPU를 전달받을 port
Root Switch에 가장 빨리 도달할 수 있는 port
비 Root Switch 당 하나의 Root port 선출

결정 순서
Cost Path가 적은 port → Root Switch까지 도달하기 위한 경로의 전체 비용
인접 Switch의 Bridge ID가 낮은 port
인접 Switch의 Port ID가 낮은 port
자신의 Port ID가 낮은 port
```

![2022-11-11-10루트포트](../images/2022-11-11-Redundancy/2022-11-11-10루트포트.jpg)

<br>

Desiganated Port 선출

```
Designated(Forwarding) port 선출
- Designated(Forwarding) port → Frame을 전달할 수 있는 port
- 각 세그먼트 마다 하나의 Designated port 선출
   세그먼트(Segment) → 장비와 장비가 연결된 구간
- 결정 순서
   Root Switch의 모든 port
   Cost Path가 적은 port → Root Switch까지 도달하기 위한 경로의 전체 비용
   인접 Switch의 Bridge ID가 낮은 port
   인접 Switch의 Port ID가 낮은 port
   자신의 Port ID가 낮은 port
```

![2022-11-11-11데지그](../images/2022-11-11-Redundancy/2022-11-11-11데지그.jpg)

<br>

non-designated Port 선출

```
Non Designated(Blocking) port 선출
- Non Designated(Blocking) port
   Loop를 방지하기 위해 임시로 비활성화 하는 port
   Frame은 차단하지만 BDPU는 정상 수신 함
- Root/Designated로 선출되지 못한 port
```

![2022-11-11-12Non Designated(Blocking) port](../images/2022-11-11-Redundancy/2022-11-11-12Non Designated(Blocking) port.jpg)

<br>

경로 선출

![2022-11-11-13최종](../images/2022-11-11-Redundancy/2022-11-11-13최종.jpg)

<br>

<br>

<br>

###### STP 상태 변화 

![2022-11-11-14상태변화](../images/2022-11-11-Redundancy/2022-11-11-14상태변화.jpg)

<br>

###### STP 문제점

![2022-11-11-15문제점](../images/2022-11-11-Redundancy/2022-11-11-15문제점.jpg)

<br>

<br>

<br>

##### PVST(Per VLAN Spanning Tree)

![2022-11-11-16pvst](../images/2022-11-11-Redundancy/2022-11-11-16pvst.jpg)

<br>

구성도

![2022-11-11-18pvst](../images/2022-11-11-Redundancy/2022-11-11-18pvst.jpg)

<br>

각 PC IP주소 설정

![2022-11-11-19IP](../images/2022-11-11-Redundancy/2022-11-11-19IP.jpg)

<br>

각 Switch 별 VLan 설정

![2022-11-11-20VLAN](../images/2022-11-11-Redundancy/2022-11-11-20VLAN.jpg)

이런식으로 5개의 Switch 설정을 해주시면 됩니다.

<br>

DSW1 - SVI 에 주소 입력

![2022-11-11-21dsw1](../images/2022-11-11-Redundancy/2022-11-11-21dsw1.jpg)

<br>

