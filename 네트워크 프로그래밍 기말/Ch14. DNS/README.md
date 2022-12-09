# 네트워크 프로그래밍 기말정리
## 주소의 변환
### > DNS 필요성
- 인터넷 보급이 미미하던 시절에는 특정 컴퓨터 시스템이 전체 호스트의 명칭 정보를 관리
  - 도메인 이름과 IP 주소의 매핑 정보를 모두 관리
- 컴퓨터 보급이 늘면서 이런 업무를 수작업으로 관리하기 어려워짐
  - 호스트의 수가 엄청나게 증가하면서 한 시스템에서 모든 호스트의 정보를 유지하기가 현실적으로 불가능
  - 도메인 이름을 중복 사용하지 않도록 통제하기도 쉽지 않았음
- **이런 문제점을 해결하려고 고안된 것이 DNS 서비스**

- **DNS**
  - 계층 구조를 지원하는 도메인 기반의 주소 표기 방법을 위한 분산 데이터베이스 시스템
  - 기본 목적은 도메인 이름에서 IP 주소를 얻는 것
  - 유닉스 시스템 에서 지원하는 nslookup 명령은 DNS를 이용해 주소 변환 요구를 수행하는 대화형 프로그램
    - 다음의 예처럼 도메인 이름이 informaiton.korea.co.kr인 호스트의 IP 주소를 얻으려면 nslookup을 ①과 같이 실행
    - 결과 ②와 ③은 DNS 서버의 도메인 이름과 IP 주소
 ![image](https://user-images.githubusercontent.com/85292541/206784951-2fa26e42-8d28-4afe-9228-0ba57eeafcf0.png)
 
### > DNS는 네임 스페이스, 네임 서버, 해석기라는 세 가지 요소로 구성
- **네임 스페이스**
  - 트리 구조의 네임 스페이스를 비롯해 데이터에 대한 이름 관련 규칙을 정의
  - 네임 스페이스의 트리에 연결된 호스트는 자원 레코드라는 정보 집합체로 표현
- **네임 서버**
  - 네임 스페이스의 트리 구조와 트리에 보관된 정보 집합체를 관리하는 프로그램
- **해석기**
  - 네임 서버로부터 사용자 응용 프로그램인 클라이언트의 요청 정보를 얻어내는 프로그램

## 네임 스페이스
### > 네임 스페이스 구조
- 계층 구조의 네임 스페이스에서 호스트의 각 레이블은 점(.)으로 구분
- 최상위부터 순차적으로 계층적 소속 관계를 나타냄
- 초상위 레이블은 기구의 성격, 그 아래 레이블은 기구 이름, 그 밑으로는 기구 내부에 있는 단위 조직의 이름.
  - 예) media.korea.com 도메인 이름에서 com은 기구의 성격, korea는 기구 이름, media는 기구 내부의 하부 조직 이름
  ![image](https://user-images.githubusercontent.com/85292541/206785822-f1534b76-2ed6-404d-8fc0-750cbcb64275.png)
- 최상위 도메인 중에서 일반 도메인은 조직의 종류에 따라 (표)와 같이 분류

|구분|설명|
|:--|:--|
|net|네트워크 지원 센터(Network support centers)를 포함한 네트워크 관련 기관|
|com|상업적인 기관(commercial organiztions)|
|biz|com과 유사한 비즈니스 목적의 회사(Businesses or firms)|
|info|정보 서비스 제공자(information service providers)|
|coop|협동조합(Cooperative business organizations)|
|pro|전문가 관련 기관(Professional individual organizations)|
|aero|항공 관련 기관(Airlines and aerospace conpanies)|
|int|국제기관(International organizations)|
|edu|교육기관(Educational institutions)|
|org|비영리 기관(Nonprofit organizations)|
|museum|박물관 관련 기관(Museum and other nonprofit organizations)
|gov|미국 연방정부 기관(Government institutions)|
|mil|미국 국방성 기관(Military groups)|
|name|개인(Personal name-individuals)|

-[그림 14-3]처럼 레이블이 부여된 각 호스트는 도메인 이름을 가짐

![image](https://user-images.githubusercontent.com/85292541/206791680-9faa5b2d-f9c6-4b3b-aebb-b09b983535be.png)

## 데이터베이스 서비스
### > 계층 구조의 네임 서버
- DNS 시스템은 전 세계에 흩어져 있는 수많은 네임 서버를 계층 구조 형식으로 관리하며 호스트에 대한 이름 정보는 이들 서버에 분산되어 저장
- 권한의 위임 과정은 하부 구조 전체에 대해 재귀적으로 적용
  - [그림 14-4]에서 사각형 호스트 전부 네임 서버이며, 그림에는 표시하지 않았지만 하부에 관리하는 도메인(Domain)이 존재

![image](https://user-images.githubusercontent.com/85292541/206796171-633378fa-3ae3-4fdc-9115-bbcb893c9183.png)

### > 도메인과 존
- 존 : 임의의 네임 서버가 관리 하는 영역
  - 특정 네임 서버가 자신의 하위에 있는 도메인을 전적으로 관리하면 존과 도메인이 동일
  - 하부에 새로운 도메인 네임 서버가 추가되면 두 영역이 일치하지 않음
![image](https://user-images.githubusercontent.com/85292541/206796573-189b8264-c6f5-4a27-9c76-89c4eb961793.png)

## 자원 레코드
- DNS 서비스는 이름과 주소 정보를 저장하기 위한 데이터베이스이므로 레코드 개념이 필요
- 이를 위하여 자원 레코드라는 개념을 사용해 DNS 데이터를 저장
- [그림 14-6]에서 네임 서버는 (a)의 자원 레코드를 이용하여 정보를 저보관하고, 해석기는 (b)의 질의 레코드를 이용하여 네임 서버에 원하는 정보를 요청

![image](https://user-images.githubusercontent.com/85292541/206798192-5b8fa428-cb63-4abf-a74d-9290d194e0c6.png)
![image](https://user-images.githubusercontent.com/85292541/206798645-dd4bd292-fd32-4fa4-acce-4bf52526a674.png)

## 네임 서버와 해석기
### > 해석기
- DNS 서비스는 클라이언트-서버 구조로 설계
- **도메인 이름과 호스트 주소의 변환 정보를 원하는 네트워크 응용 프로그램은 해석기라 불리는 DNS 클라이언트에 정보 제공을 요청**
- 해석기는 가장 가까운 네임 서버와 접촉해 정보 제공을 요청하고, 해당 서버에 정보가 없으면 다른 네임 서버와 접촉해 정보를 찾는 과정을 반복

### > 인증 데이터
- 해당 데이터를 직접 관리할 책임이 있는 네임 서버로부터 받은 정보를 의미
- 반면, 캐시 데이터는 이전 요청에 의해 호스트가 보관하던 데이터이며, 재사용 할 목적으로 한동안 저장

## 해석기
### > 존
- 인증 데이터는 네임 스페이스의 특정 영역인 존을 관리하는 네임 서버가 유지하고 관리
- 존은 자원 레코드에 포함되는 인증 데이터의 집합체로 정의되며, 다음과 같은 내용을 포함
  - 존에 속하는 모든 호스트의 전체 자원 레코드 집합체
  - 존에 포함된 최상위 호스트
  - 위임 서브 존
  - 위임된 서브 존에 관한 글루 데이터
- [그림14-7]에서 해석기가 info.mit.edu 밑에 위치한 test.info.mit.edu 호스트의 정보를 알고 싶다고 가정
![image](https://user-images.githubusercontent.com/85292541/206803083-494f44b3-b6ae-4dcc-9a21-6ec2d91c953c.png)

### > 요청의 처리
- 가장 적절한 인근 네임 서버는 질의를 받은 네임 서버가 관장하는 존의 상위에 위치하는데, 이러한 동작은 해석기가 원하는 인증 정보를 찾을 때까지 연속적으로 반복
- 질의 요청이 처리되는 과정을 두 가지로 나누어 생각
  - 호스트가 DNS 정보를 요청할 때는 인증 데이터의 필요 여부를 명시할 수 있음
    - 인증 데이터가 반드시 필요한 경우가 아니라면 로컬 네임 서버 보관된 캐시 데이터 사용할 수도 있음
  - 해석기는 질의 요청이 재귀적으로 처리되는지 명시할 수 있음
    - 재귀적이라는 뜻은 해석기가 최초로 접촉을 시도한 네임 서버가 질의 요청을 계속 추적,관리하면서 요청에 대해 인증 데이터를 회신하는 것
    - 네임 서버가 비재귀적인 요청을 받은 경우에는 두 가지 응답이 가능한데, 자신이 인증 데이터를 가지고 있으면 이를 회신하고, 그렇지 않으면 다른 네임 서버의 포인터 정보를 회신
### > 재귀적 처리
- 재귀적 요청을 받은 네임 서버는 결과적으로 해석기와 같은 클라이언트 역할을 수행
- [그림 14-8]은 재귀적 처리와 비재귀적 처리를 비교하여 설명

![image](https://user-images.githubusercontent.com/85292541/206804326-949433a5-f333-45f3-b992-ace5a147cc1e.png)

### > 반복적 처리
- [그림 14-9]는 재귀적 처리와 반복적 처리를 비교 설명
![image](https://user-images.githubusercontent.com/85292541/206804843-f8f13609-d46a-43dc-a530-92c9132102d0.png)

## DNS 프로토콜
### > DNS 메시지 구조
- DNS 요청이 필요하면 [그림 14-10]과 같은 DNS 메시지에 내용을 기록
- 모두 다섯 부분으로 구성된 DNS 메시지에 Question 필드는 질의 레코드를 사용하고, 나머지 Answer, Authority, Additional 필드는 자원 레코드를 사용

![image](https://user-images.githubusercontent.com/85292541/206805391-98dddadc-c7fd-4e76-9f09-9794d5a574b3.png)
  - Answer 필드는 질문에 대한 답볍인 자원 레코드, Authority 필드는 인증을 가리키는 자원 레코드, Additional 필드는 기타 정보를 의미하는 자원 레코드
### > DNS 헤더
- DNS 메시지에서 Header 필드 정보는 필수 사항
![image](https://user-images.githubusercontent.com/85292541/206805904-132a8e3a-6fd9-4efa-b73c-614521845ed9.png)

### > UDP 프로토콜
- 해석기와 네임 서버는 53번 포트를 기본으로 사용하여 UDP 프로토콜로 DNS 메시지를 전송
- 이때 DNS 메시지가 512바이트보다 작으면 UDP를 사용하는데 문제가 없지만, 이보다 크면 TCP를 사용하게 되는데 이때도 DNS 메시지 전송은 53번 포트를 사용
- **DNS 메시지가 512바이트보다 커 TCP 프로토콜을 사용할 떄는 다음 두 가지 경우를 고려**
  - 첫째, 응답 메시지가 512바이트보다 크다는 사실을 해석기가 미리 인지하는 경우로, 이때는 처음부터 TCP 연결을 사용
  - 둘째, 해석기가 사전에 인지하지 못한 상태에서 UDP를 사용하는 경우

## DNS 프로토콜 동작 과정
### > 질의 메시지
- 해석기가 WWW.korea.co.kr라는 호스트의 IP 주소를 찾으려고 로컬 네임 서버에 질의 메시지Query Message를 전송하는 겨우를 가정
  - [그림 14-10]의 DNS 메시지는 다음 예처럼 [그림 14-11]의 Header 부터 시작
    - Header의 첫 번째에 위치한 identification은 메시지 식별자로, UDP의 비순서적 전송 방식을 보완하려고 사용
    - 해석기는 이 번호를 사용해 서버의 응답을 순서대로 정렬하여 질의와 응답을 적절히 연결되도록 해 줌
  ![image](https://user-images.githubusercontent.com/85292541/206806814-c19beb54-74e0-4b65-99d0-d79c66ca8073.png)
  - QUCOUNT 값만 1이므로 [그림 14-10]에서 헤더에 이어지는 필드는 Question에 관한 질의 레코드 하나임을 알 수 있음
  - [그림 14-6]의 (b)에 나타난 질의 코드 값이 다음과 같다면 찾는 정보가 www.korea.co.kr 호스트의 IP 주소라는 의미가 됨
![image](https://user-images.githubusercontent.com/85292541/206806977-f4e9ad79-7fa5-4b33-847c-7b45c44f2bb3.png)

- 앞의 값을 DNS 메시지로 형식화하면 [그림 14-12]와 같음

![image](https://user-images.githubusercontent.com/85292541/206807092-c4419f9b-e3a0-4c75-8d6e-b9168752b2d3.png)
### > 응담 메시지
- 질의 메시지를 수신한 네임 서버는 DNS 클라이언트가 원하는 IP 주소를 찾아 응답 메시지로 회신
  - 다음과 같은 DNS 응답 메시지의 Header에서 Identification은 클라이언트 값을 그대로 사용해야 하며 플래그는 0x8180 값으로 주어짐
  - 이 값을 해석하면 QR = 1이므로 응답 메시지가 되고, OPcode는 여전히 표준 질의 응답임을 나타냄 RD = 1,RA = 1이므로 재귀적 질의 응답임을 알 수 있으며, Rcode 정보에 의해 오류는 발생하지 않음

![image](https://user-images.githubusercontent.com/85292541/206807862-e05ce082-4c79-4ad1-a85b-2dd432792448.png)
  - 해석기의 요청을 받은 서버는 도메인의 인증 권한이 없는 것으로 가정되어 메시지에 재귀적 응답이 포함
  - 따라서 Question 자원 레코드 1개, Answer 자원 레코드 2개, 인증 권한이 있는 네임 서버를 가리키는 Authority 자원 레코드가 2개 있음
  - 그리고 부가 정보에 관한 자원 레코드는 회신되지 않음
- Question 자원 레코드는 다음과 같이 질의 레코드의 경우와 같음

![image](https://user-images.githubusercontent.com/85292541/206808254-d760ec31-6bd2-48dd-8e52-bf4764ce69e8.png)
- 응답 메시지에는 다음과 같이 Answer 자원 레코드가 2개 존재하는데, 첫 번째 유형이 CNAME으로 되어 있음
- 이를 통해 WWW.korea.co.kr는 호스트의 정식Canonical 명칭이 아닌 별명 Alias임을 확인

![image](https://user-images.githubusercontent.com/85292541/206808713-b7eeb8ca-798d-43f6-a46f-1abb46509454.png)

- Authority 자원 레코드의 내용
![image](https://user-images.githubusercontent.com/85292541/206808803-bd910bc0-0368-42f5-a804-8b3eb2fd93a1.png)

  
