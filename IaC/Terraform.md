# Terraform
테라폼은 하시코프에서 클라우드 인프라스트럭처 자동화를 지향하는 [IaC(Infrastructure as Code)](#IaC) 도구이다. AWS, Azure, GCP 같은 클라우드 뿐만 아니라 더 많은 서비스들도 지원한다.

# 작업 흐름
1. Scope - 프로젝트를 위해 만들어야 할 리소스가 무엇인지 확인한다.
2. Author - 파일 작성 (Create the configuration file in HCL)
3. Initialize - ```terraform init```으로 프로젝트에 필요한 플러그인을 다운로드 한다.
4. Plan & Apply - ```terraform plan```으로 과정을 검증하고 ```terraform apply```로 클라우드에 적용한다.
5. Destroy - 리소스 제거

> plan을 통해서 꼭! 검증하고 apply를 해야 실제 배포시 일어나는 문제점을 최대한 줄일 수 있다고 합니다. 잊지말고 apply!!

## IaC
Infrastructure as Code의 줄임말로 코드를 통해 인프라 구성요소들을 구축하고 관리하는 것을 뜻한다.
IaC는 코드의 장점인 작성용이성, 재사용성, 유지보수 등의 장점을 가진다.

# AWS와 연결
## 테라폼으로 AWS VPC를 만드는 대략적 과정
1. AWS에서 IAM 액세스 키 발급하기
2. 테라폼 설치
3. 리소스 정의
4. 선언한 리소스들 확인(Plan)
5. 적용(Apply)
  
## 1. AWS에서 IAM 액세스 키 발급하기
1. aws에 로그인을 한 후 '내 보안 자격 증명'을 클릭해 들어갑니다.
![aws_main](../img/terraform/aws_main.png)
2. 좌측에 있는 액세스 관리 > 사용자를 들어가 사용자 추가를 해줍니다.
![IAM_menu](../img/terraform/IAM_menu.png)
3. 사용자 이름은 자유롭게, AWS 엑세스 유형 선택은 프로그래밍 방식 엑세스를 선택해줍니다.
> AWS Management Console 엑세스는 웹에서 접속을 하게 해줍니다. terraform은 웹에서 사용하는 것이 아니기 때문에 필요 없습니다.
![user_name](../img/terraform/user_name.png)
4. 권한 설정을 해줍니다.
> 현재는 vpc - ec2 구축이 목적이고 IAM에 대해 공부하는 것이 아니기 때문에 ec2fullaccess와 vpcfullaccess를 해줍니다.
그룹에 사용자 추가 > 그룹 생성 > 그룹 이름 입력, ec2fullaccess, vpcfullaccess 선택
![ec2f](../img/terraform/ec2f.png)
![vcpf](../img/terraform/vcpf.png)
5. 생성된 사용자의 액세스 키 ID와 비밀 엑세스 키를 기억해둡니다.
**유출될 경우 다른 누군가가 여러분의 계정에 침투하여 수많은 비용을 야기시킬수 있습니다.**
![accesskey_secretkey](../img/terraform/accesskey_secretkey.png)


## 2. 테라폼 설치
> Ubuntu 18.04 LTS를 기준으로 합니다.
1. 압축 해제 설치.
```
sudo apt-get install unzip
```
2. [Terraform](https://www.terraform.io/downloads.html) 홈페이지에서 최신 버전을 확인하고 다운로드 링크를 복사합니다
3. Terraform 다운로드
```
wget https://releases.hashicorp.com/terraform/0.14.3/terraform_0.14.3_linux_amd64.zip
```
4. 압축풀기
```
unzip terraform_0.14.3_linux_amd64.zip
```
5. bin으로 파일 이동
```
sudo mv terraform /usr/local/bin
```
6. 설치 확인 (버전 확인)
```
terraform --version
```

## 3. 리소스 정의


# 출처 / 참고
- [Introduction to Infrastructure as Code with Terraform - Workflows](https://learn.hashicorp.com/tutorials/terraform/infrastructure-as-code?in=terraform/aws-get-started#workflows)
- [how-to-install-terraform-in-ubuntu](https://qastack.kr/ubuntu/983351/how-to-install-terraform-in-ubuntu)
- [Terraform으로 AWS 관리하기](https://blog.outsider.ne.kr/1260)
- [만들면서 배우는 아마존 버추얼 프라이빗 클라우드(Amazon VPC)](https://www.44bits.io/ko/post/understanding_aws_vpc)
