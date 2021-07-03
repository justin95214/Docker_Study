# 2.3 도커 이미지  Docker Image

- 모든 컨테이너는 이미지를 기반으로 생성
- 도커에서는 애플리케이션을 실행하기 위한 파일들을 모아놓고, 애플리케이션과 함께 이미지로 만들 수 있음
- 이미지를 기반으로 애플리케이션을 바로 배포 가능
- 도커 이미지 = 가상머신에서 사용하는 이미지와 비슷한 역할

                        = 어떤 애플리케이션을 실행하기 위한 환경

                        =  파일들의 집합

    - 도커 허브(Docker Hub)

        도커 허브(중앙 이미지 저장소)에서 이미지를 내려받음

        도커 허브는 계정만있다면, 누구든지 이미지를 올리고 내려받을 수있어, 쉽게 공유 가능

        ![2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled.png](2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled.png)

    - docker create & docker run & docker pull 명령어

## 2.3.1 도커 이미지 생성

컨테이너에 애플리케이션을 위한 특정 개발 환경을 직접 구축한 뒤 사용자만의 이미지를 직접 생성

컨테이너 안에서 작업한 내용을 이미지로 만드는 방법

1. 이미지로 만들 컨테이너를 생성, 컨테이너 내부에 first라는 이름의 파일을 하나 생성해 기존의 이미지로부터 변경사항을 만듬

     keypoint : 컨테이너 생성 = commit 명령어

    ![2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%201.png](2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%201.png)

2. docker commit [options] container [repository[:tag]] >> docker commit 명령어를 통해 컨테이너 이미지를 생성

    commit옵션을 지정하고 커밋할 컨테이너 이름을 명시한 뒤 생설될 이미지의 이름을 생성

    -a = author / -m = 커밋 메세지

    ![2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%202.png](2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%202.png)

    ![2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%203.png](2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%203.png)

  3. commit_test:first 이미지로 새로운 이미지를 생성하여 commit_test:second 라고 생성

![2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%204.png](2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%204.png)

![2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%205.png](2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%205.png)

![2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%206.png](2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%206.png)

## 2.3.2 이미지 구조 이해

- inspect 명령어

    = 컨테이너뿐만 아니라 네트워크,볼륨, 이미지등 모든 도커 단위의 정보를 얻을 때 사용함

![2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%207.png](2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%207.png)

                                                                             '''''

![2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%208.png](2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%208.png)

1. 이미지를 commit할 때 컨테이너에서 변경된 사항만 새로운 레이어로 저장
2. 그 레이어를 포함한 새로운 이미지를 생성하기 때문

= 전체 이미지의 실제크기는 기존 +새로운 파일 크기 ...

![2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%209.png](2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%209.png)

- docker rmi = 이미지 삭제 명령
    1. 도커 이미지를 삭제한다
    2. 이미지를 사용 중인 컨테이너를 삭제 한다

```bash
docker stop commit_test2 && docker rm commit_test2
docker rmi commit_test:first
```

![2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%2010.png](2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%2010.png)

컨테이너를 삭제하지않고 이미지 삭제 시도 시에 오류 발생

이미지를 삭제했지만, 해당 이미지의 레이어 파일이 삭제되지는 않음

해당 이미지 기반의 하위 이미지가 존재하기 때문

## 2.3.3 이미지 추출

- docker save 명령어

컨테이너의 커맨드, 이미지 이름, 태그 등이 이미지의 모든 메타데이터를 포함해 하나의 파일로 추출 할 수가 있음

```bash
docker save -o ubuntu_14_04.tar ubuntu:14.04
```

- docker load 명령어

추출된 이미지를 load명령어를 도커에 다시 로드 할 수있음

그러면 이전 이미지와 동일한 도커 엔진에 생성

```bash
docker load -i ubuntu_14_04.tar
```

- export & import

    docker commit명령어로 컨테이너를 이미지로 만들면 컨테이너에서 변경된 사항뿐만 아니라 컨테이너가 생성 될 떄detached모드, 컨테이너 커맨드, 설정 등이 미지에 함께 저장

    하지만 export는 이미지 설정 정보를 저장하지 않음

    import는 다시 이미지로 저장하는 것

```bash
docker export -o rootFS.tar mycontainer
docker import rootFS.tar muimage:0.0
```

## 2.3.4 이미지 배포

 docker save 또는 export 같은 방법으로 이미지를 단일 파일로 추출해서 배포할 수 도 있지만, 

1. 이미지 파일 크기가 너무 큼
2. 도커 엔진의 수가 많다면 이미지 배포의 어려움

- The Method
1. 도커 허브 이미지 저장소를 활용하자

    도커 허브 = 클라우드 서비스 개념

    docker push/ pull 으로 이미지를 올리고/내려받기

2. 도커 사설 레지스트리(Docker Private Registry)를 사용하자

    도커 허브처럼 사용자가 직접 이미지 저장소를 생성

    but, 이미지 저장소 및 서버, 저장 공간을 관리해야 하므로 까다로움

### 2.3.4.1  도커 허브 저장소

- docker search 명령어를 입력하여 이미지 검색 가능
- docker inspect 명령어를 입력하여 CPU아키텍쳐 check 가능

```bash
docker inspect ubuntu | grep Architecture
```

- 이미지 저장소(Repository) 생성

![2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%2011.png](2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%2011.png)

github처럼 private와 public 이 있음

- 저장소에 이미지 올리기

```bash
docker run -i -t --name commit_container1 ubuntu:14.04
# echo my first push >> test

docker commit commit_container1 my-image-name:0.0
```

1. ubuntu:14.04 이미지에 test라는 파일을 생성해 변경 사항을 만듬

    (도커 이미지 생성)

 2. " my-image-name:0.0"  = 이미지 명명하여 저장

 3. docker tag로 이미지 이름 추가 하기

```bash
docker tag my-image-name:0.0 alicek107/my-image-anme:0.0
```

docker tag명령어로 "my-image-name:0.0"이미지 파일에

"alicek107/my-image-anme:0.0" 이름 추가 하기

 4. docker login 로그인하여, 이미지를 허브 서버에 올리기

```bash
docker login
```

username/ password를 통해 권한을 얻는다

 5. push명령어로 이미지를 저장소에 올리기

```bash
docker push alicek107/my-image-name:0.0
```

docker push 명령어를 통해서, docker tag명령어로 추가한 이미지 이름인 "alicek107/my-image-name:0.0" 이미지를 올리기

6.  docker pull 명령어로 올린 저장소에서 이미지 내려받기

```bash
docker pull alicek107/my-image-name:0.0
```

'

- 조직.팀 생성은 100~103p를 통해 참고 가능

### 2.3.4.2  도커 사설 레지스트리

예제로 사용하는 myregistry는 컨테이너로서 구현이 되어있어서 이미지가 존재함 >> 이 이미지는 도커에서 공식적으로 제공

1. **사설 레지스트리 컨테이너 생성**

```bash
docker run -d --name myregistry -p 5000:5000 --restart=always registry:2.6
```

- - - restart옵션

- - restart옵션 = 컨테이너가 종료가 될때 재시작에 대한 정책 설정

도커 호스트나 도커 엔진을 재시작하면 컨테이너도 함께 재시작하게 됨

- -restart의 다른 입력으로는  on-failur와 unless-stopped가 존재

컨테이너 종료코드가 0이 아닐 때 컨테이너 재시작을 5번까지 시도 가능

- -p 옵션

레지스트리 컨테이너는 기본적으로 5000번 포트를 사용으로 -p 옵션으로 컨테이너의 5000번 포트를 호스트의 5000번 포트와 연결

```bash
curl localhost:5000/v2/
```

(curl 은 HTTP요청을 보내는 도구 중 하나)

2. **사설 레지스트리에 이미지 push 하기**

```bash
docker tag my-image-name:0.0 ${DOCKER_HOST_IP}:5000/my-image-name:0.0
```

- ${DOCKER_HOST_IP} =레지스트리 컨테이너를 생성한 도커 호스트의 IP입력
- 호스트 IP 뒤에는 : 를 붙이고 포트번호를 붙여함
- "my-image-name:0.0" =이미지 파일 이름
    - docker push 사용법

     도커 데몬은 HTTPS를 사용하므로 인증서 적용해 별도의 설정 필요함

    하지만, 2.3단원에서는 설정하지않은 방법을 제시

    도커 데몬은 HTTPS를 사용하지않은 레지스트리 컨테이너에 접근하지 못하도록 설정되어 push되지 않음

    push되지않은 오류 화면

    ```bash
     docker push 192.168.99.101:5000/my-image-name:0.0
    ```

    ![2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%2012.png](2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%2012.png)

3. **부록A를 참고해 다음 옵션을 도커 시작 옵션에 추가한 뒤에 도커 재시작**

```bash
DOCKER_OPTS="--insecure-registry=192.168.99.101:5000"
```

- --insecure-registry옵션 = HTTPS를 사용하지않은 레지스트리 컨테이너에 이미지를  push/pull 가능

```bash
 docker push 192.168.99.101:5000/my-image-name:0.0
```

4. **이미지 pull 하기**

```bash
docker pull 192.168.99.101:5000/my-image-name:0.0
```

pull할 때 레지스트리 컨테이너의  URL을 뒤에 입력해야함

5. **Nginx서버 케이스로 접근 권한생성**

책에서는 Nginx로 예제로 서버 케이스로 접근 권한을 생성하는 케이스를 보여주는 AWS나 AZURE에선 https TSL보안기능을 제공하므로 다른 곳에 활용할 때는 문제가 없을 것이라 예상됨

 

- 보안관련 솔루션
1. Self-Signed 인증서와 키를 발급하여 TLS를 적용하는 방법
2. 회사나 기업같은 경우 구입한 신뢰할수있는 인증서와 키가 있다면 활용해도 무관

책에서는 1번 솔루션으로 Self-Signed ROOT 인증서(CA)파일 생성하여 접근 권한을 생성

![2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%2013.png](2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%2013.png)

1. 새로운 디렉토리를 생성
2. 디렉토리 안에서 개인 키를 생성(openssl 명령어를 설치할 필요없음)

![2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%2014.png](2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%2014.png)

    IP를 통해 Nginx 서버 컨테이너에 접근 할 것

1. ${DOCKER_HOST_IP} 에는 레지스트리 컨테이너가 존재하는 도커 호스트 서버 IP나 도메인이름을 입력

```bash
echo subjectAltName = IP:${DOCKER_HOST_IP} > extfile.cnf
```

이 명령어를 통해서 IP를 extfile.cnf configure하는 파일에 입력

 2. 인증서 서명 요청파일인 CSR(certificate signing request)파일을 생성하여 ROOT인증서로 새로운 인증서를 발급

6.  **레지스트리에 로그인 할 때, 사용할 계정과 비밀번호 를 저장하는 파일 생성**(mv명령어를 통해 위에서 생성한 cert 디렉토리안에 인증서와 같이 넣어야함)

![2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%2015.png](2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%2015.png)

- htpasswd 설치방법
- 데비안 계열(우분투)

```bash
apt-get install apache2-utils
```

- 레드햇 계열(CentOS)

```bash
yum install httpd-tools
```

7. **위에서 생성한 certs디렉토리 안에 nignx.conf안에 아래 항목의 코드를 작성**(vi 보다 개인적으로 nano 를 쓰시는걸 추천드림)

                 >>>>>github의 수정사항 반영 완료 <<<<<<<<<<<<<<<

![2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%2016.png](2%203%20%E1%84%83%E1%85%A9%E1%84%8F%E1%85%A5%20%E1%84%8B%E1%85%B5%E1%84%86%E1%85%B5%E1%84%8C%E1%85%B5%20Docker%20Image%2020c44330057c494c9122287494bfae89/Untitled%2016.png)

```bash
upstream docker-registry {
  server registry:5000;
}
server {
  listen 443;
  server_name ${DOCKER_HOST_IP};
  ssl on;
  ssl_certificate /etc/nginx/conf.d/domain.crt;
  ssl_certificate_key /etc/nginx/conf.d/domain.key;
  client_max_body_size 0;
  chunked_transfer_encoding on;

  location /v2/ {
    if ($http_user_agent ~ "^(docker\/1\.(3|4|5(?!\.[0-9]-dev))|Go ).*$" ) {
      return 404;
    }
    auth_basic "registry.localhost";
    auth_basic_user_file /etc/nginx/conf.d/htpasswd;
    add_header 'Docker-Distribution-Api-Version' 'registry/2.0' always;

    proxy_pass http://docker-registry;
    proxy_set_header Host $http_host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header X-Forwarded-Proto $scheme;
    proxy_read_timeout 900;
  }
}
```

8. **Nginx서버 컨테이너를 생성하여, nginx.conf domiain.crt [domain.ky](http://domain.ky) 파일들을 auth 디렉터리를 -v옵션으로 컨테이너에 공유**

이 컨테이너 포트는 443으로 Docker호스트의 443포트와 바인딩됨(걸리게 됨)

```bash
docker run -d --name nginx_fronted \
-p 443:443 \
--link myregistry:registry \
-v $(pwd)/certs/etc/nginx/conf.d\
```

도커 허브와 동일하게 docker login명령어로 레지스트리 컨테이너로 로그인함

```bash
docker login https://IP
```

https사용으로 자동르로 호스트 IP 443포트와 연결하여 Nginx 서버 컨테이너로 포워딩(맵핑)됨

9. **직접 서명한 인증서를 신뢰할 수있는 인증서 목록으로 추가**

Self-signed 인증서를 사용했으므로 도커에서 이를 사용하지 못하도록 에러가 발생 >> ca.crt파일을 인증서 목록에 추가해야함

(데비안 우분투)

```bash
cp certs/ca.crt /usr/local/share/ca-certificates/

update-ca-certificated
```

(레드햇 계열 CentOS)

```bash
cp certs/ca.crt /etc/pki/ca-trust/source/anchors/

update-ca-trust
```

10. **도커 재시작**

```bash
service docker restart

docker start nginx_frontend
```

2단원 깃허브

[https://github.com/justin95214/start-dockerkubernetes/tree/master/chapter2](https://github.com/justin95214/start-docker-kubernetes/tree/master/chapter2)