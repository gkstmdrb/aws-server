# aws-server
# aws ec2 원격 연동 방법
### 1. AWS EC2에서 서버 공개
● 보안 그룹 설정 <br>
유형: HTTP 또는 Custom TCP <br>
포트: 서버에서 사용하는 포트 (예: 8080) <br>
소스: 노트북 2의 공인 IP 주소 또는 0.0.0.0/0 (테스트 용도로만 사용, 보안에 취약) <br><br>

● 서버 실행 포트 확인 <br> 
Spring Boot 서버가 실행 중인 포트는 <br>
application.properties 또는 application.yml에서 설정된 server.port 값 찾기 (기본값은 8080) <br><br>

● EC2 퍼블릭 IP 또는 DNS 확인 <br> 
EC2 인스턴스의 퍼블릭 IP 또는 퍼블릭 DNS를 복사해야함 <br><br>

예: <br>
퍼블릭 IP: 3.125.xxx.xxx <br>
퍼블릭 DNS: ec2-3-125-xxx-xxx.compute-1.amazonaws.com <br><br>

