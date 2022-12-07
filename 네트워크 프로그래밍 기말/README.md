# 네트워크프로그래밍 기말정리
라우팅
  - 송수신 호스트 사이의 패킷 전달 경로를 선택

혼잡제어
  - 네트워크의 특정 지역에 트래픽이 몰리는 현상(혼잡)을 다룸

패킷의 분할과 병합
  - 패킷 분할: 큰 데이터를 여러 패킷으로 나누는 과정
  - 병합 : 목적지에서 분할된 패킷을 다시 모으는 과정

## 연결형 서비스와 비연결형 서비스
- 네트워크 계층이 전송 계층에 제공하는 서비스
 - ① 패킷을 전송하기 전에 송수신 호스트 사이에 연결을 설정하는 연결형 서비스
 - ② 연결 설정 없이 데이터를 패킷 단위로 전송하는 비연결형 서비스
 
   ![image](https://user-images.githubusercontent.com/85292541/206193857-28e697fd-d68e-422b-ab9a-b9a5a8366840.png)
   
### > 비연결형 서비스
>![image](https://user-images.githubusercontent.com/85292541/206194732-4baf0b58-8dde-4d87-995e-6b05a96b18bb.png)
![image](https://user-images.githubusercontent.com/85292541/206194783-6fdfe756-d55d-4142-8de2-588952fe04f4.png)
![image](https://user-images.githubusercontent.com/85292541/206194566-949fb124-3271-4d27-a3ed-4f2146a398e4.png)

### > 연결형 서비스
>![image](https://user-images.githubusercontent.com/85292541/206195001-52298a11-6784-4bc5-b6be-5283f4f68840.png)
![image](https://user-images.githubusercontent.com/85292541/206195088-578aaefb-3f42-43a5-9845-e3439171a50a.png)

## 라우팅
- 패킷의 전송 경로를 지정
- 라우터의 주요 기능은 입력된 패킷을 어느 출력 경로를 통해 다음 라우터로 전달해야 가장 효과적인지 결정 하는 것
- 패킷의 전송 경로를 결정할 때는 고려할 사항이 많은데, 특정 패킷을 우선 처리하려고 다른 패킷들에 손해를 입히지 않는 정책도 이중 하나
![image](https://user-images.githubusercontent.com/85292541/206196569-d00f807a-9fb4-4ab8-85e8-7ed33155ce5c.png)

### > 정적,동적 라우팅
- 의도적 호는 비의도적으로 발생하는 네트워크 구성의 변화에 효과적으로 대처할 수 있는 신뢰성 확보도 라우팅 경로 선택 시 중요하게 고려할 사항
- 라우팅 경로는 정적 라우팅이나 동적 라우팅 방식으로 선택
>![image](https://user-images.githubusercontent.com/85292541/206197467-8920053f-1a39-4b40-a3ad-aa4e645ce721.png)
![image](https://user-images.githubusercontent.com/85292541/206197789-487b8331-391f-40f7-8fd6-4734b3078c1b.png)

### > HELLO/ECHO 패킷
- 라우터의 초기화 과정에서 가장 먼저 할 일은 이웃 라우터의 경로정보를 파악하는 것
- 각 라우터는 이웃에 연결된 라우터에 초기화를 위한 HELLO 패킷을 전송해 경로 정보를 얻음
- 라우터 사이의 전송 지연 시간을 측정하기 위해서 ECHO 패킷을 전송

## 라우팅 테이블
- 패킷 전송 과정에서 라우터들이 적절한 경로를 쉽게 찾을 수 있도록, 가장 기본적인 도구로 라우팅 테이블을 사용
- **라우팅 테이블에 포함해야 하는 필수 정보는 (목적지 호스트, 다음 홉) 의 조합**
![image](https://user-images.githubusercontent.com/85292541/206204122-bb64505f-d2e7-43b2-9003-ada718160059.png)
