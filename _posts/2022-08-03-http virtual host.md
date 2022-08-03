# http virtual host

<br>

구상도

![2022-08-03-10구상도](../images/2022-08-03-http virtual host/2022-08-03-10구상도.PNG)

<br>

### port-based virtual host

<br>

Server에서 파일수정 1

![2022-08-03-04파일수정4](../images/2022-08-03-http virtual host/2022-08-03-04파일수정4.PNG)

<br>

Server에서 파일수정 2

![2022-08-03-01파일수정1](../images/2022-08-03-http virtual host/2022-08-03-01파일수정1.PNG)

<br>

Server에서 파일수정 3

![2022-08-03-02파일수정2](../images/2022-08-03-http virtual host/2022-08-03-02파일수정2.PNG)

포트번호를 8080까지 쓰겠다 선언 해주시면 됩니다.

<br>

Server에서 파일수정 4

![2022-08-03-03파일수정3](../images/2022-08-03-http virtual host/2022-08-03-03파일수정3.PNG)

host를 2개 만들면서 무슨 ip주소가 오든 포트번호가 같으면 /var/ww1,2 로 가겠다 라는 설정 입니다.

<br>

Server에서 필요한 디렉터리와 피일 생성

![2022-08-03-05파일디렉터리생성](../images/2022-08-03-http virtual host/2022-08-03-05파일디렉터리생성.PNG)

구상도에 나와있는 대로 /var 밑에 파일과 디렉터리를 생성 해주시면 됩니다.

<br>

Client에서 확인

![2022-08-03-06확인](../images/2022-08-03-http virtual host/2022-08-03-06확인.PNG)

포트번호에 따라서 다르게 나오는 모습이 확인 되었습니다.

<br>

<br>

<br>

### ip-based virtual host

<br>

Server에서 ip주소 추가

![2022-08-03-07ip추가](../images/2022-08-03-http virtual host/2022-08-03-07ip추가.PNG)

ens32를 2개로 나누어서 사용 하겠습니다.

<br>

Client에서 ping 확인

![2022-08-03-08ping확인](../images/2022-08-03-http virtual host/2022-08-03-08ping확인.PNG)

나눈 ip주소 들이 제대로 통신이 되는지 확인 한번 해주시고

<br>

MAC주소 확인

![2022-08-03-09맥주소확인](../images/2022-08-03-http virtual host/2022-08-03-09맥주소확인.PNG)

MAC주소가 똑같은지 확인 도 한번 해주시면 좋습니다.

<br>

Server에서 파일 수정

![2022-08-03-11파일수정](../images/2022-08-03-http virtual host/2022-08-03-11파일수정.PNG)

아까는 어떤 주소가 들어오든 포트번호만 같으면 그쪽으로 가줘라 였지만 이번에는 IP주소에 다라 달라 지도록 설정을 해 줍니다.

<br>

Server에서 데몬 재시작

![2022-08-03-12재시작](../images/2022-08-03-http virtual host/2022-08-03-12재시작.PNG)

<br>

Client 확인

![2022-08-03-13확인](../images/2022-08-03-http virtual host/2022-08-03-13확인.PNG)

IP주소에 따라 제대로 나오는 모습 입니다.

<br>

<br>

<br>

### name-based virtual host

<br>

구상도

![2022-08-03-18dns구상도](../images/2022-08-03-http virtual host/2022-08-03-18dns구상도.PNG)

<br>

DNS 생성

![2022-08-03-14dns생성](../images/2022-08-03-http virtual host/2022-08-03-14dns생성-165951384991116.PNG)

우선 DNS를 2개 생성해 주시면 됩니다.

<br>

Server에서 파일 수정

![2022-08-03-15파일수정](../images/2022-08-03-http virtual host/2022-08-03-15파일수정.PNG)

Server에서 파일을 수정 해주시는데 ServerName을 선언하여 주소로 구분 하겠습니다.

<br>

Client DNS주소 변경

![2022-08-03-16dns주소수정](../images/2022-08-03-http virtual host/2022-08-03-16dns주소수정.PNG)

DNS의 IP주소로 변경 해주시면 됩니다.

<br>

Client에서 확인

![2022-08-03-17확인](../images/2022-08-03-http virtual host/2022-08-03-17확인.PNG)

3가지 다 설정한 대로 나오시면 성공 입니다.

<br>

Client에서 Wire Shark 확인

![2022-08-03-19b12와이어](../images/2022-08-03-http virtual host/2022-08-03-19b12와이어.PNG)

![2022-08-03-20c12와이어](../images/2022-08-03-http virtual host/2022-08-03-20c12와이어.PNG)

www.b12.kh   www.c12.kh 가 정상적으로 dns를 통해 생성된 모습 입니다.

<br>

