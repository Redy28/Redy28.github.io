# iSCSI service

<br>

구상도



<br>

##### iSCSI Target 설정

디스크 추가

![2022-09-05-01디스크추가](../images/2022-09-05-iSCSI service/2022-09-05-01디스크추가.PNG)

10GB 디스크를 single로 추가해 주시면 됩니다.

<br>

패키지 설치

![2022-09-05-02패키지](../images/2022-09-05-iSCSI service/2022-09-05-02패키지.PNG)

<br>

패키지 확인

![2022-09-05-03패키지확인](../images/2022-09-05-iSCSI service/2022-09-05-03패키지확인.PNG)

<br>

명령어 Test

![2022-09-05-04명령어확인](../images/2022-09-05-iSCSI service/2022-09-05-04명령어확인.PNG)

![2022-09-05-05명령어확인](../images/2022-09-05-iSCSI service/2022-09-05-05명령어확인.PNG)

block : 외부에서 공간사용요청할때 어떤디스크의 파티션같은 데서 가져올것인가 

fileio :  디스크 의 일부 디렉터리 를 외부에서 사용할수 있게 한다 

<br>

파티션 생성

![2022-09-05-06디스크생성](../images/2022-09-05-iSCSI service/2022-09-05-06디스크생성.PNG)

<br>

block 생성

![2022-09-05-07블록](../images/2022-09-05-iSCSI service/2022-09-05-07블록.PNG)

<br>

fileio 생성

![2022-09-05-08파일](../images/2022-09-05-iSCSI service/2022-09-05-08파일.PNG)

<br>

생성 확인

![2022-09-05-09생성확인](../images/2022-09-05-iSCSI service/2022-09-05-09생성확인.PNG)

<br>

iscsi 생성

![2022-09-05-10스카시](../images/2022-09-05-iSCSI service/2022-09-05-10스카시.PNG)

<br>

iscsi 내부 node를 생성

![2022-09-05-11node생성](../images/2022-09-05-iSCSI service/2022-09-05-11node생성.PNG)

![2022-09-05-13노드](../images/2022-09-05-iSCSI service/2022-09-05-13노드.PNG)

<br>

iscsi 를 이용하여 접속할 initiator 를 선언

![2022-09-05-12이니쉬에이터생성](../images/2022-09-05-iSCSI service/2022-09-05-12이니쉬에이터생성.PNG)

<br>

확인

![2022-09-05-14확인](../images/2022-09-05-iSCSI service/2022-09-05-14확인.PNG)

<br>

initiator 에 인증정보 설정

![2022-09-05-15인증설정](../images/2022-09-05-iSCSI service/2022-09-05-15인증설정.PNG)

<br>

port 확인

![2022-09-05-16포트확인](../images/2022-09-05-iSCSI service/2022-09-05-16포트확인.PNG)

<br>

<br>

<br>

##### iSCSI initiator 설정

패키지 설치

![2022-09-05-17패키지](../images/2022-09-05-iSCSI service/2022-09-05-17패키지.PNG)

![2022-09-05-18확인](../images/2022-09-05-iSCSI service/2022-09-05-18확인.PNG)

<br>

target 검색

![2022-09-05-19타겟](../images/2022-09-05-iSCSI service/2022-09-05-19타겟.PNG)

<br>

initiator 주소를 입력

![2022-09-05-22xkrpt](../images/2022-09-05-iSCSI service/2022-09-05-22xkrpt.PNG)

![2022-09-05-20포트확인](../images/2022-09-05-iSCSI service/2022-09-05-20포트확인.PNG)

<br>

데몬 실행

![2022-09-05-23데몬실행](../images/2022-09-05-iSCSI service/2022-09-05-23데몬실행.PNG)

<br>

target 에 접속

