# Docker
도커는 컨테이너 기반의 오픈소스 가상화 플랫폼이다. 여러 컨테이너가 호스트 OS의 자원을 공유하여 사용한다.

## 컨테이너?
컨테이너란 호스트 OS의 자원을 논리적으로 분리한 구역을 뜻함. 호스트 OS의 환경에 구애받지 않고 실행할 수 있는 장점을 가지고 있다.

## 그럼 VM과의 차이는?
VM(Virtual Machine)은 한 가상화에 OS가 포함되고 가상화끼리 호스트 OS의 자원을 공유하지 않고 분리해서 사용하나, 도커는 컨테이너간 호스트 OS의 자원을 공유하여 사용하기 때문에 가상화에 비해 성능에 큰 우위를 점한다.

VM(Virtual Machine) | Container
:----------:|:----------:
![vm](../img/docker/vm.png)|![container](../img/docker/container.png)

# 컨테이너라는 특징에서 사용해야 할 이유가 더 있다
컨테이너는 Docker 위에서 작동한다. 컨테이너화 된 프로그램들은 컨테이너의 장점에 의해 OS에 구애받지 않고 똑같이 작동한다. 그러므로 다른 OS라도 같은 실행을 보장할 수 있는 것이다. 조금씩 버전과 설정이 다른 다수의 서버에 똑같은 환경을 구현할 때 Docker를 사용하면 보장될 수 있는 것이다.

## 참고
- [Docker - 컨테이너란? (Container)](https://captcha.tistory.com/46)
- [왜 굳이 도커(컨테이너)를 써야 하나요?](https://www.44bits.io/ko/post/why-should-i-use-docker-container)
- [[Container 시리즈] 00. Container/ Docker란 뭔가요?](https://tech.osci.kr/2020/03/03/91690167/)