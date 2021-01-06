# Docker
도커는 컨테이너 기반의 오픈소스 가상화 플랫폼이다. 여러 컨테이너가 호스트 OS의 자원을 공유하여 사용한다.

## 컨테이너?
컨테이너란 호스트 OS의 자원을 논리적으로 분리한 구역(프로세스)을 뜻함. 호스트 OS의 환경에 구애받지 않고 실행할 수 있는 장점을 가지고 있다.

## 그럼 VM과의 차이는?
VM(Virtual Machine)은 한 가상화에 OS가 포함되고 가상화끼리 호스트 OS의 자원을 공유하지 않고 분리해서 사용하나, 도커는 컨테이너간 호스트 OS의 자원을 공유하여 사용하기 때문에 가상화에 비해 성능에 큰 우위를 점한다.

VM(Virtual Machine) | Container
:----------:|:----------:
![vm](../img/docker/vm.png)|![container](../img/docker/container.png)

# 컨테이너라는 특징에서 사용해야 할 이유가 더 있다
컨테이너는 Docker 위에서 작동한다. 컨테이너화 된 프로그램들은 컨테이너의 장점에 의해 OS에 구애받지 않고 똑같이 작동한다. 그러므로 다른 OS라도 같은 실행을 보장할 수 있는 것이다. 조금씩 버전과 설정이 다른 다수의 서버에 똑같은 환경을 구현할 때 Docker를 사용하면 보장될 수 있는 것이다.

# 작업흐름(Workflow, 작성에서 베포까지)
![docker_workflow](../img/docker/docker_workflow.png)
1. Dockerfile 작성
2. Docker Image 빌드
3. Docker Container 작동

> [Microsoft에서 제공하는 workflow](https://docs.microsoft.com/ko-kr/dotnet/architecture/microservices/docker-application-development-process/docker-app-development-workflow)가 더 구체적이지만 입문 기준으로는 저 3가지 핵심만 봐도 충분하다 생각합니다.

# 작업흐름에 따른 Docker Container 만들어보기
> 우분투 기준입니다. Docker 설치는 [이쪽](https://www.44bits.io/ko/post/easy-deploy-with-docker)을 참고하시면 됩니다.

## Dockerfile 작성
```dockerfile
FROM ubuntu:bionic # FROM : 어떤 이미지로부터 이미지를 생성할 것인지 지정
RUN apt-get update # RUN : 명령어를 실행해라
RUN apt-get install -y git
```

## Docker Image 빌드
```
sudo docker build -t ubuntu:git-from-dockerfile .
```
docker로 build하는데 -t : 이름을 설정한다, ubuntu:git-from-dockerfile로, .(현재 경로의 Dockerfile 기준으로)

현재 경로의 Dockerfile을 읽어서 이미지를 빌드한다는 의미.

```
Step 1/3 : FROM ubuntu:latest
latest: Pulling from library/ubuntu
da7391352a9b: Pull complete 
14428a6d4bcd: Pull complete 
2c2d948710f2: Pull complete
Step 2/3 : RUN apt-get update
 ---> Running in 9e14afdb6878
Step 3/3 : RUN apt-get install -y git
...
 ---> 0ca5b5553167
Successfully built 0ca5b5553167
Successfully tagged ubuntu:git-from-dockerfile
```
작성한 순서대로 작동하는 것을 확인할 수 있다.

### 실행해보기
```
$ sudo docker run -it ubuntu:git-from-dockerfile bash
root@07b830ee9cd5:/# git --version
git version 2.25.1
```
> -it는 -i 옵션과 -t의 옵션이 합쳐진건데 [이쪽](http://pyrasis.com/book/DockerForTheReallyImpatient/Chapter20/28) 에서 확인하시면 됩니다.
생성한 이미지에서 깃이 잘 설치된 것을 확인할 수 있다.

<!-- 더 작성할 내용
*docker image 베포하기*
docker image와 container의 차이
ssh와 셸의 차이? (docker container 실행했을때랑 ssh로 실행했을 때 차이. 프로세스가 유지가 되어 있는지)
한 가지 재미있는 점은 pull이라는 명령어 이름입니다. 도커에서는 이미지를 다운 받을 때  install이나 download와 같은 명령 대신 pull을 사용합니다. 앞으로 살펴보겠지만 이는 단순히 이미지를 다운로드 받는 데서만 그런 것은 아닙니다. 이미지를 업로드 할 때는 push라는 명령어를 쓰고, 새로운 이미지를 생성할 때는 commit, 이미지의 차이를 확인할 때는 diff라는 명령어를 사용합니다. 이러한 명령어 이름은 깃Git이나 서브버전Subversion에서 사용되는 명령어들로 개발자들에게는 친숙한 이름들입니다. 기능적으로는 이미지를 다운로드 받아온다고 이해해주시기 바랍니다.
 - 44bits, easy-deploy-with-docker
-->
## 참고
- [Docker - 컨테이너란? (Container)](https://captcha.tistory.com/46)
- [왜 굳이 도커(컨테이너)를 써야 하나요?](https://www.44bits.io/ko/post/why-should-i-use-docker-container)
- [[Container 시리즈] 00. Container/ Docker란 뭔가요?](https://tech.osci.kr/2020/03/03/91690167/)
-[도커(Docker) 입문편 - 컨테이너 기초부터 서버 배포까지](https://www.44bits.io/ko/post/easy-deploy-with-docker)
- [Using Docker Containers to Improve Reproducibility in Software and Web Engineering](https://www2.slideshare.net/vincenzoferme/using-docker-containers-to-improve-reproducibility-in-software-and-web-engineering/37)
- [Docker 앱에 대한 개발 워크플로](https://docs.microsoft.com/ko-kr/dotnet/architecture/microservices/docker-application-development-process/docker-app-development-workflow)
- [가장 빨리 만나는 Docker 20장 - 2. build](http://pyrasis.com/book/DockerForTheReallyImpatient/Chapter20/02)