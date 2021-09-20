# blockchain
블록체인은 데이터 분산 처리 기술. 네트워크에 참여하는 모든 사용자가 모든 거래 내역 등의 데이터를 분산, 저장하는 기술을 지칭함.

## 용어 해석
- 블록 : 개인과 개인의 거래의 데이터가 기록되는 장부.
- 블록들이 서로 연결되어있는 사슬(체인)의 구조를 가지게 됨 → 블록체인


> 각 사용자가 이 블록(장부)를 가지고 있기 때문에 어떠한 거래를 하면 모든 기록들이 저장됨. 10개의 블록이 있고 10명의 사용자가 있으면 모든 사용자가 10개의 같은 블록을 가지고 있게 됨.

## 블록체인 네트워크 유형

1. 퍼블릭 블록체인 네트워크
    1. 누구든지 신청하여 참여할 수 있음. (예: 비트코인)
    2. 누구나 거래 검증 및 승인을 수행함
    3. 누구나 블록 열람 가능
    4. 누구나 참여가능하기 때문에 트랜잭션(거래)의 프라이버시 보장은 불가능. 불특정다수가 사용하기 때문.
2. 프라이빗 블록체인 네트워크 (예: 하이퍼레저)
    1. 블록체인을 관리하는 '중앙' 안에서 거래함. 
    2. 퍼블릭보다 적은 인원이 있어 블록 검정 시간이 퍼블릭 보다 빠름
    3. 중앙이 허가한 기관/사용자만 참여 가능
    4. 그러므로 익명성 보장은 힘듬

## ERC 토큰 종류

1. **ERC-20**
    - 대중적으로 많이 쓰이는 토큰
    - 개발도 쉽고 대부분의 거래소에서도 지원하는 표준
2. **ERC-223**
    - ERC-20의 문제점에 대한 대안 버전
    - ERC-20의 경우 잘못된 주소로 토큰이 전송되었을 때 소유권을 잃어버리는 문제가 있는데, ERC-223의 경우 이 문제를 방지함.
3. **ERC- 621**

4. **ERC-721**
    - NFT토큰을 만들때 사용되는 토큰.
    - ERC-721로 발행된 토큰들은 서로가 대체불가능(Non-Fungible) 하다.
    - ERC-20의 경우 대체 가능하다. ('화폐'의 개념으로 생각하면 쉬울듯 하다.
5. **ERC-1155**


## 출처 / 참고
- [블록체인 기술이란?](https://www.ibm.com/kr-ko/topics/what-is-blockchain) 

- [퍼블릭 블록체인](http://wiki.hash.kr/index.php/%ED%8D%BC%EB%B8%94%EB%A6%AD_%EB%B8%94%EB%A1%9D%EC%B2%B4%EC%9D%B8)

- [프라이빗 블록체인](http://wiki.hash.kr/index.php/%ED%94%84%EB%9D%BC%EC%9D%B4%EB%B9%97_%EB%B8%94%EB%A1%9D%EC%B2%B4%EC%9D%B8)

- [다 아는 것 같은데 은근 잘 모르는 블록체인의 개념](https://www.markany.com/kr/portfolio-posts/%EC%9D%80%EA%B7%BC-%EC%9E%98-%EB%AA%A8%EB%A5%B4%EB%8A%94-%EB%B8%94%EB%A1%9D%EC%B2%B4%EC%9D%B8-%EA%B0%9C%EB%85%90/)

- [블록체인 비즈니스 사례 1. 스마트계약,송금,사물인터넷](https://www.markany.com/kr/portfolio-posts/%eb%b8%94%eb%a1%9d%ec%b2%b4%ec%9d%b8-%eb%b9%84%ec%a6%88%eb%8b%88%ec%8a%a4-%ec%82%ac%eb%a1%80-1/)

- [암호화폐 첫걸음 3] 다양한 암호화폐 토큰 종류의 이해](https://blog.makerdao.com/ko/6-3-%EB%8B%A4%EC%96%91%ED%95%9C-%EC%95%94%ED%98%B8%ED%99%94%ED%8F%90-%ED%86%A0%ED%81%B0-%EC%A2%85%EB%A5%98%EC%9D%98-%EC%9D%B4%ED%95%B4/)

- [암호화폐 토큰의 종류 (ERC 표준의 종류)](https://isnow.tistory.com/248#)

## 구축 참고
- [13. 리믹스 솔리디티 8.0 버전 ERC20토큰 만들기](https://kimsfamily.kr/342)

- [[Ethereum] Solidity 문법 이해(1)](https://d2fault.github.io/2018/03/19/20180319-about-solidity-1/)

- [Creating ERC20 Supply](https://docs.openzeppelin.com/contracts/4.x/erc20-supply)