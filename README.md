# aws-server
# aws ec2 원격 연동 방법
### 1. EC2 인스턴스의 SSH 접속 허용 <br>
● SSH 접속은 EC2 인스턴스 생성 시 생성된 키 페어(.pem 파일)을 사용 <br><br>

노트북 1에서 기존 .pem 파일을 노트북 2에 전송 <br><br>

● EC2 인스턴스의 보안 그룹에서 노트북 2의 퍼블릭 IP 주소에 대해 SSH 포트(기본: 22)를 허용한다. <br><br>
유형: SSH <br>
포트 범위: 22 <br>
소스: 노트북 2의 퍼블릭 IP 주소 (또는 0.0.0.0/0 테스트 용도로만) <br><br>

### 2. PowerShell에서 AWS EC2 서버 SSH 접속 준비 <br>
키 파일 권한 설정: PowerShell을 열고 키 파일의 권한을 설정
```
icacls "C:\경로\your-key.pem" /inheritance:r
icacls "C:\경로\your-key.pem" /grant:r "$($env:USERNAME):R"
```
<br><br>

### 3. PowerShell로 EC2 SSH 접속 <br>
AWS 콘솔 > EC2 > 보안 그룹 > 인바운드 규칙 편집 <br><br>

● 인바운드 규칙 추가 <br>
유형: SSH <br>
포트 범위: 22 <br>
소스: 노트북 2의 퍼블릭 IP 주소 <br>
