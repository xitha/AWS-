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


