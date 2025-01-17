# aws-server
# aws ec2 원격 연동 방법
### 1. EC2 인스턴스의 SSH 접속 허용 <br><br>

● SSH 접속은 EC2 인스턴스 생성 시 생성된 키 페어(.pem 파일)을 사용 <br>
노트북 1에서 기존 .pem 파일을 노트북 2에 전송 <br><br>

● EC2 인스턴스의 보안 그룹에서 노트북 2의 퍼블릭 IP 주소에 대해 SSH 포트(기본: 22)를 허용한다. <br>
유형: SSH <br>
포트 범위: 22 <br>
소스: 노트북 2의 퍼블릭 IP 주소 (또는 0.0.0.0/0 테스트 용도로만) <br><br>

### 2. PowerShell에서 AWS EC2 서버 SSH 접속 준비 <br><br>

키 파일 권한 설정: PowerShell을 열고 키 파일의 권한을 설정
```
icacls "C:\경로\your-key.pem" /inheritance:r
icacls "C:\경로\your-key.pem" /grant:r "$($env:USERNAME):R"
```
<br><br>

### 2-1. USERNAME 알아내는법 <br><br>

● AWS CLI 설치 및 설정 <br>
AWS CLI 설치 후 PowerShell에서 aws --version 명령어로 정상 설치 여부를 확인 <br>
```
aws --version
```
<br><br>

AWS CLI에서 자격 증명 설정 <br>
```
aws configure
```
<br><br>

설정 시 입력할 정보: <br>
● Access Key ID: AWS에서 발급받은 키. <br>
● Secret Access Key: AWS에서 발급받은 비밀 키. <br>
● Default Region: EC2 인스턴스가 위치한 지역(예: us-east-1). <br>
● Default Output: json 또는 text 선택. <br><br>

예)
```
C:\Windows\System32>aws configure
AWS Access Key ID [None]: ********************
AWS Secret Access Key [None]: *********************************
Default region name [None]:
```
<br>
1
