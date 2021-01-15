> 아마존 웹 서비스에 관련된 서비스를 적는 markdown입니다.

# 목차
- [컴퓨팅](#컴퓨팅)
  - [Lambda](#Lambda)
- [데이터베이스 서비스](#데이터베이스-서비스)
  - [RDS](#RDS)

# 컴퓨팅
## Lambda
Lambda는 특정 코드(ex. 이미지 리사이징, api)를 서버구축 없이(Serverless) 코드를 실행, 관리하게 해주는 서비스이다. 코드가 실행되면 사용된 시간 만큼 비용을 청구하고 그 외 사용하지 않을시 청구되지 않는다. Node.js, Python, Ruby, Java 등 다양한 언어를 지원한다.

### 람다를 실행시키는 여러가지 방법
1. API Gateway
	- API Gateway로 api의 구축, 배포 및 관리를 하고 Lambda로 코드 구현하는 방식.
2. CloudWatch
	- CloudWatch로 주기적인 Lambda 호출 가능
3. S3
	- S3에서 발생하는 특정 이벤트를 통해 람다 함수를 실행할 수 있다. [당근마켓에서 이 방법으로 이미지 썸네일을 만들었다고 한다.](https://medium.com/daangn/aws-lambda%EB%A5%BC-%EC%9D%B4%EC%9A%A9%ED%95%9C-%EC%9D%B4%EB%AF%B8%EC%A7%80-%EC%8D%B8%EB%84%A4%EC%9D%BC-%EC%83%9D%EC%84%B1-%EA%B0%9C%EB%B0%9C-%ED%9B%84%EA%B8%B0-acc278d49980)
4. Lambda@Edge
	- Amazon CloudFront의 기능 중 하나로 코드를 aws의 cdn에 프로비저닝시켜 사용자가 코드를 가까운 장소에서 사용할 수 있도록 한다.
	- 이 기능을 사용할 때 여러가지 [제한사항](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/lambda-requirements-limits.html)이 있다.
	  1. Lambda@Edge의 리전은 미국 동부(N. Virginia) 고정
	  2. 지원 언어 한정 (2021-01 기준)
		- Python 3.8 or 3.7
		- Node.js 12 or 10
		- Node.js 8 or 6 (지원 중단으로 만들거나 수정 불가)
	  3. VPC의 리소스를 접근하는 용도로 Lambda function 사용 불가
	
### Serverless
Serverless는 서버가 없다는 의미이다. 엄밀히 말하면 작업을 하는 서버는 존재하나 이것에 대해 따로 관심을 가질 필요가 없다는 의미이다. 예로 Lambda를 사용할 때 이 서비스의 서버 사양, 네트워크, 구축 등에 신경쓰지 않아도 된다.

# 데이터베이스 서비스
## RDS
RDS는 Relational Database Service의 약자이다. 관계형 데이터베이스를 설치하고 운영하는 서비스이다.
자동 백업, 다중 AZ(Available Zone, 가용 영역) 배포를 지원한다.
다중 AZ 배포는 다른 AZ의 보조 DB 인스턴스를 자동으로 프로비저닝* 하게 해주는 기능이다. 이 기능을 사용하면 주 AZ 장애가 생겼을 때 보조 AZ의 DB 인스턴스를 사용하도록 장애 조치를 자동으로 수행해준다.
MySQL, MariaDB, PostgreSQL 등 다양한 시스템 지원.
> 프로비저닝 : 자원을 미리 배치, 배포하여 즉시 사용할 수 있는 상태로 미리 준비해 두는 것

# 출처
- [서버리스 아키텍쳐(Serverless)란?](https://velopert.com/3543)
- [AWS 람다(AWS Lambda)란?](https://www.44bits.io/ko/keyword/aws-lambda)
- [AWS Lambda란 무엇입니까?](https://docs.aws.amazon.com/ko_kr/lambda/latest/dg/welcome.html)
- [AWS Lambda@edge로 실시간 이미지 리사이징(updated)](https://heropy.blog/2019/07/21/resizing-images-cloudfrount-lambda/)
- [Requirements and Restrictions on Lambda Functions](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/lambda-requirements-limits.html)