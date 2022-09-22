## SEMI PROJECT

<br>

구상도

![2022-09-22-01구상도](C:\Users\home\Desktop\github\깃허브 이미지\2022-09-22-semi\2022-09-22-01구상도.PNG)

<br>

### Interface 구성

<br>

vyos Interface

![2022-09-22-02인터페이스구성](C:\Users\home\Desktop\github\깃허브 이미지\2022-09-22-semi\2022-09-22-02인터페이스구성.PNG)

<br>

S NAT

![2022-09-22-04인터페이스구성s](C:\Users\home\Desktop\github\깃허브 이미지\2022-09-22-semi\2022-09-22-04인터페이스구성s.PNG)

![2022-09-22-05인터페이스구성s](C:\Users\home\Desktop\github\깃허브 이미지\2022-09-22-semi\2022-09-22-05인터페이스구성s.PNG)

<br>

D NAT

![2022-09-22-03인터페이스구성d](C:\Users\home\Desktop\github\깃허브 이미지\2022-09-22-semi\2022-09-22-03인터페이스구성d.PNG)

<br>

Web Server Interface 100,110

![2022-09-22-06웹서버인터페이스](C:\Users\home\Desktop\github\깃허브 이미지\2022-09-22-semi\2022-09-22-06웹서버인터페이스.PNG)

![2022-09-22-07웹서버인터페이스110](C:\Users\home\Desktop\github\깃허브 이미지\2022-09-22-semi\2022-09-22-07웹서버인터페이스110.PNG)

<br>

MariaDB Interface

![2022-09-22-08마리아db인터페이스120](C:\Users\home\Desktop\github\깃허브 이미지\2022-09-22-semi\2022-09-22-08마리아db인터페이스120.PNG)

<br>

Storage Interface

![2022-09-22-09스토리지인터페이스200](C:\Users\home\Desktop\github\깃허브 이미지\2022-09-22-semi\2022-09-22-09스토리지인터페이스200.PNG)

<br>

DNS Interface

![2022-09-22-10dns인터페이스130](C:\Users\home\Desktop\github\깃허브 이미지\2022-09-22-semi\2022-09-22-10dns인터페이스130.PNG)

<br>

### NFS Service

NFS Server 설정 - NFS 설치

![2022-09-22-11nfs서버설치](C:\Users\home\Desktop\github\깃허브 이미지\2022-09-22-semi\2022-09-22-11nfs서버설치.PNG)

<br>

NFS Clinet 접근 설정

![2022-09-22-12nfs클라이언트접근설정](C:\Users\home\Desktop\github\깃허브 이미지\2022-09-22-semi\2022-09-22-12nfs클라이언트접근설정.PNG)

![2022-09-22-13nfs클라이언트접근설정](C:\Users\home\Desktop\github\깃허브 이미지\2022-09-22-semi\2022-09-22-13nfs클라이언트접근설정.PNG)

10.10.10.xx로 접근하는 모든것에 허용

<br>

NFS 환경설정 파일 주요 옵션 (/etc/exports) 

① ro: 읽기 전용 (기본값) 

② rw: 읽기/쓰기 

③ no_root_squash: 클라이언트에서 접근하는 root 인정

 ④ root_squash: 클라이언트에서 접근하는 root 무시. 서버 상의 nobody로 매핑 (기본값) 

⑤ all_squash: root를 포함하여 모든 사용자의 권한을 nobody로 매핑 

⑥ no_subtree_check: 하위 디렉터리를 검사하지 못하도록 설정 

⑦ secure: 포트 번호가 1024 이하의 요청에만 허가

 ⑧ async: 데이터 변경을 비동기식으로 처리. 쓰기가능한 디스크 스토리지에 사용하면 유용 

⑨ anonuid: 접근하는 사용자 권한을 지정한 uid로 매핑 

⑩ anongid: 접근하는 그룹 권한을 지정한 gid로 매핑

<br>

디렉터리 생성 후 파일 만들기

```
mkdir /nfs_server
echo nfs1.txt > /nfs_server/nfs_server_01.txt
```

<br>

NFS 관련 서비스 시작

```
systemctl start nfs-server
systemctl start rpcbind
```

<br>

NFS 되어있는 디렉터리 목록, 설정

![2022-09-22-14nfs확인](C:\Users\home\Desktop\github\깃허브 이미지\2022-09-22-semi\2022-09-22-14nfs확인.PNG)

<br>

NFS Clinet(10.10.10.100) NFS 패키지 설치

```
yum -y install nfs-utils
```

<br>

원격 디렉터리 mount

```
mount -t nfs 10.10.10.200:/nfs_server /var/www/html
```

<br>

<br>

<br>

### ISCSI Service

ISCSI target 구성 - 설치

```
yum -y install targetcli
systemctl restart target
```

<br>

파티션 생성

```
fdisk /dev/sdb
```

<br>

block 생성

```
backstores/block create block1 /dev/sdb1
```

<br>

fileio 생성

```
backstores/fileio create target_01 /tmp/target_01 50M write_back=false
```

<br>

iscsi 내부 node 생성

```
iscsi/iqn.2022-09.kh.b00.target:linux-target/tpg1/luns create /backstores/block/block1

 iscsi/iqn.2022-09.kh.b00.target:linux-target/tpg1/luns create /backstores/fileio/target_01
```

<br>

iscsi 이용하여 접속할 initiator 설정 (10.10.10.120)

```
iscsi/iqn.2022-09.kh.b00.target:linux-target/tpg1/acls create iqn.2022-09.kh.b00.initiator:linux-initiator
```

<br>

ISCSI initiator 설정

패키지 설치

```
yum -y install iscsi-initiator-utils lsscsi
```

<br>

target 검색

```
iscsiadm -m discovery -t st -p 172.16.0.120
```

<br>

initiator 주소 입력

```
vim /etc/iscsi/initiatorname.iscsi
InitiatorName=iqn.2022-09.kh.b00.initiator:linux-initiator
```

<br>

관련 서비스 활성화

```
systemctl restart iscsi
systemctl restart iscsid
```

<br>

target 접속

```
iscsiadm -m node -T iqn.2022-09.kh.b00.target:linux-target -l -p 10.10.10.200
```

<br>

initiator를 disk로 활용

```
mkdir /iscsi_01
mount /dev/sdb /iscsi_01
```

<br>

### MariaDB 설정

준비한 DB 불러오기

```
mysql -u root -pP@ssw0rd < /root/WebTest.sql
```

<br>

외부 접속을 위한 사용자 생성

```
create user `root`@`% `identified by 'P@ssw0rd';
```

<br>

퍼미션 부여

```
grant all privileges on *.* to `root`@'%';
```

모든 데이터베이스, 테이블에 모든 퍼미션을 부여한다.

<br>

MariDB 경로 수정

```
vi /etc/my.cnf
datadir=/iscsi_01/data/mysql
```

<br>

수정한 경로로 MariaDB 파일 옮기기

```
cp -Rv /var/lib/mysql /iscsi_01/data/
```

<br>

### DNS 설정

![2022-09-22-15DNS](C:\Users\home\Desktop\github\깃허브 이미지\2022-09-22-semi\2022-09-22-15DNS.PNG)

- 단 웹서버 접근정보 제공 (A 레코드)
- 영역전송은 모든 서버가 가능하도록

<br>

<br>

<br>

<br>

<br>

<br>

<br>

<br>

<br>

