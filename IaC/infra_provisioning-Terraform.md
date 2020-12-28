# Terraform
테라폼은 하시코프에서 클라우드 인프라스트럭처 자동화를 지향하는 [IaC(Infrastructure as Code)](#IaC) 도구이다. AWS, Azure, GCP 같은 클라우드 뿐만 아니라 더 많은 서비스들도 지원한다.

# 작업 흐름
1. Scope - 프로젝트를 위해 만들어야 할 리소스가 무엇인지 확인한다.
2. Author - 파일 작성 (Create the configuration file in HCL)
3. Initialize - ```terraform init```으로 프로젝트에 필요한 플러그인을 다운로드 한다.
4. Plan & Apply - ```terraform plan```으로 과정을 검증하고 ```terraform apply```로 클라우드에 적용한다.
5. Destroy - 리소스 제거

> plan을 통해서 꼭! 검증하고 apply를 해야 실제 배포시 일어나는 문제점을 최대한 줄일 수 있다고 합니다. 잊지말고 apply!!

# 설치 방법
> Ubuntu 18.04 LTS를 기준으로 합니다.
1. 압축 해제 설치.
```
sudo apt-get install unzip
```
2. [Terraform](https://www.terraform.io/downloads.html) 홈페이지에서 최신 버전을 확인하고 다운로드 링크를 복사한다.
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

## IaC
Infrastructure as Code의 줄임말로 코드를 통해 인프라 구성요소들을 구축하고 관리하는 것을 뜻한다.
IaC는 코드의 장점인 작성용이성, 재사용성, 유지보수 등의 장점을 가진다.

# AWS와 연결
## 준비
- AWS 계정
- AWS CLI 설치
- 자신의 AWS 자격증명이 local로 되어있는지 확인

# 출처
- [Introduction to Infrastructure as Code with Terraform - Workflows](https://learn.hashicorp.com/tutorials/terraform/infrastructure-as-code?in=terraform/aws-get-started#workflows)
- [how-to-install-terraform-in-ubuntu](https://qastack.kr/ubuntu/983351/how-to-install-terraform-in-ubuntu)

