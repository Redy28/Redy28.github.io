# openvas  & metasploit 

##### OpenVAS

- 오픈 소스 취약점 스캐너
- OpenVAS는 취약점 검색 및 취약점 관리를 제공하는 여러 서비스 및 도구의 프레임워크
- 취약점 스캐너란 컴퓨터, 컴퓨터 시스템, 네트워크 또는 애플리케이션의 취약점을 평가하는 용도로 만들어 진 컴퓨터 프로그램
- 단순 취약점 스캔 뿐만 아니라, 해당 취약점의 원인, 그래프 형태로 도식화 등을 지원
- 오픈 소스이기 때문에 상용 버전보다 수가 적은 취약점을 찾아내지만, 일반적으로 취약점 스캐너가 하는 모든 작업을 지원함

<br>

gvm-start

![2022-09-27-01gvmstart](../images/2022-09-27openvas&metasploit/2022-09-27-01gvmstart.jpg)

<br>

login

![2022-09-27-02로그인](../images/2022-09-27openvas&metasploit/2022-09-27-02로그인.jpg)

<br>

configuration -> targets

![2022-09-27-03컨피그타겟](../images/2022-09-27openvas&metasploit/2022-09-27-03컨피그타겟.jpg)

<br>

new target

![2022-09-27-03컨피그타겟2](../images/2022-09-27openvas&metasploit/2022-09-27-03컨피그타겟2.jpg)

![2022-09-27-04타겟](../images/2022-09-27openvas&metasploit/2022-09-27-04타겟.jpg)

<br>

target 만들어진거 확인

![2022-09-27-05타겟](../images/2022-09-27openvas&metasploit/2022-09-27-05타겟.jpg)

<br>

configuration -> scan configs

![2022-09-27-06컨피그스캔컨피그](../images/2022-09-27openvas&metasploit/2022-09-27-06컨피그스캔컨피그.jpg)

스캔 방향이나 방법을 정하는 곳 입니다.

<br>

scans -> tasks

![2022-09-27-07scans tasks](../images/2022-09-27openvas&metasploit/2022-09-27-07scans tasks.jpg)

<br>

new tasks

![2022-09-27-07scans tasks2](../images/2022-09-27openvas&metasploit/2022-09-27-07scans tasks2.jpg)

![2022-09-27-08newtasks](../images/2022-09-27openvas&metasploit/2022-09-27-08newtasks.jpg)

<br>

tasks 생성 확인

![2022-09-27-09tasks확인](../images/2022-09-27openvas&metasploit/2022-09-27-09tasks확인.jpg)

<br>

start

![2022-09-27-10start](../images/2022-09-27openvas&metasploit/2022-09-27-10start.jpg)

취약점 scanning 시작

<br>

scan 완료

![2022-09-27-11완료](../images/2022-09-27openvas&metasploit/2022-09-27-11완료.jpg)

![2022-09-27-12완료](../images/2022-09-27openvas&metasploit/2022-09-27-12완료.jpg)

<br>

취약점 부분

![2022-09-27-13완료](../images/2022-09-27openvas&metasploit/2022-09-27-13완료.jpg)

CVE에 들어가서 보시면 취약점 번호가 나옵니다.

<br>

같은 취약점이 있는 software

![2022-09-27-14취약점소프트웨어](../images/2022-09-27openvas&metasploit/2022-09-27-14취약점소프트웨어.jpg)

<br>

<br>

<br>

##### Metasploit

- https://www.metasploit.com/
- 2003년 오픈 소스로 발표된 취약점 점검 도구
- 단순 공격 도구라기보다 복잡한 작업들을 자동화하는데 필요한 인프라 구조를 제공하는 프레임워크
- 2009년 rapid7에 인수된 이 후 2개의 상용 제품인 express와 pro 발표
- Windows / Linux 플랫폼에서 사용 가능

<br>

실행

![2022-09-27-15메타](../images/2022-09-27openvas&metasploit/2022-09-27-15메타.jpg)

![2022-09-27-16메타](../images/2022-09-27openvas&metasploit/2022-09-27-16메타.jpg)

<br>

search

![2022-09-27-17ms17](../images/2022-09-27openvas&metasploit/2022-09-27-17ms17.jpg)

<br>

OpenVAS를 이용하여 R2 스캔 결과를 확인하고 metasploit을 이용하여 공 격

![2022-09-27-18ms17](../images/2022-09-27openvas&metasploit/2022-09-27-18ms17.jpg)

![2022-09-27-19옵션](../images/2022-09-27openvas&metasploit/2022-09-27-19옵션.jpg)

![2022-09-27-20exploit](../images/2022-09-27openvas&metasploit/2022-09-27-20exploit.jpg)

![2022-09-27-21exploit](../images/2022-09-27openvas&metasploit/2022-09-27-21exploit.jpg)

![2022-09-27-22sir](../images/2022-09-27openvas&metasploit/2022-09-27-22sir.jpg)

![2022-09-27-22mkdir](../images/2022-09-27openvas&metasploit/2022-09-27-22mkdir.jpg)

![2022-09-27-23확인](../images/2022-09-27openvas&metasploit/2022-09-27-23확인.jpg)

현재 인증을 받지 않고 R2 PC에 들어가 제어권을 뺏어온 상황 입니다.

<br>