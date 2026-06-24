# AWS 네트워크 구축 
**실습 개요**
- AWS의 콘솔에서 vpc를 활용하여 subnet을 구성하고 gateway를 이용해 네트워크 구조를 구축한다. 
EC2 인스턴스에 서버를 구성한다.

**실습 과정**
- vpc 생성
- public subnet 생성-인터넷과 직접 통신 가능
- private subnet 생성-인터넷에서 직접 접근 불가능
- internet gateway 생성-subnet이 인터넷과 통신할 수 있도록 생성 후 vpc에 연결
- public routetable 생성-internet gateway와 연결-public subnet과 연결
- gateway 생성-private subnet 내부 인스턴스가 인터넷으로 나갈 수 있도록 함
- nat gateway는 public subnet에 배치, 탄력 ip 할당
- private route table 생성-nat gateway를 기본 경로로 설정-private subnet과 연결

**구조**
- public subnet의 인스턴스는 internet gateway를 통해 외부 인터넷과 직접 통신가능
- private subnet의 인스턴스는 외부에서 직접 접근하지 못하고 nat gateway를 통해 필요한 다운로드 혹은 업데이트 가능

**이미지**
- 실습 후 비용이 나가지 않도록 정리 후 vpc 소스맵
<img width="1590" height="346" alt="image" src="https://github.com/user-attachments/assets/29467435-5616-4ae5-84d8-0621c893bbcf" />

# AWS 고가용성 웹서비스 구축 
**실습 개요**
- AWS 서비스를 활용하여 고가용성 웹 서비스를 구축한다

**실습 과정**
- Security Group 설정
- EC2 인스턴스 생성
- Nginx 웹 서버 구축
- S3 버킷 생성 및 스토리지 구성
- AMI 생성 및 서버 복제
- Application Load Balancer 구성
- Target Group 생성
- Listener 및 Routing 설정
- CloudWatch 모니터링
- SNS 이메일 알림 구성
- Auto Scaling Group 구성
- Launch Template 생성
- Instance Maintenance Policy 설정
- Network ACL 활성화

  **EC2 및 웹 서버 구축**
  - ssh(22), http(80)
  - mobaxterm으로 접속-ssh를 통해 ec2 인스턴스에 접속
    <img width="735" height="270" alt="image" src="https://github.com/user-attachments/assets/25b6aac0-7ca6-4326-86a3-08c8ffa16e78" />
  - nginx 설치-웹 서버 정상 동작 확인

  **S3 스토리지 구성**
  - s3 버킷 생성
  - 객체 업로드
  - 접근 policy 확인

  **AMI 생성 후 서버 복제**
  - ec2 인스턴스를 이미지화해 ami 생성
  - 생성한 ami를 활용해 동일한 환경의 서버 구축 - 해당 ip주소에 접속하면 동일한 웹사이트가 나옴

  **load balancer 구성**
  - target group 생성
  - ec2 인스턴스 등록
  - listener 설정-http
  - routing 설정-target group으로 요청 전달하도록 설정
  - 트래픽이 여러 서버로 분산되는 것이 확인됨

  **cloudwatch**
  - cpu 사용률 같은 리소스 상태 모니터링하는 역할
  - sns 알림-이메일로 설정
  - 임계값 초과 시 이메일 알림이 확인
    <img width="576" height="222" alt="image" src="https://github.com/user-attachments/assets/39c7d418-e564-4248-9aa8-9533c5fcbb3d" />
  - auto scaling 구성
  - 시작 템플릿 생성
  - 최소 인스턴스, 최대 인스턴스, 원하는 용량 설정
  - cpu 사용량 증가 시 인스턴스가 자동 생성되고 후에 자동 축소되는 것이 확인됨
  
  




