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

### > 라우팅 테이블
- 패킷 전송 과정에서 라우터들이 적절한 경로를 쉽게 찾을 수 있도록, 가장 기본적인 도구로 라우팅 테이블을 사용
- **라우팅 테이블에 포함해야 하는 필수 정보는 (목적지 호스트, 다음 홉) 의 조합**
![image](https://user-images.githubusercontent.com/85292541/206204122-bb64505f-d2e7-43b2-9003-ada718160059.png)

### > 라우팅 정보의 처리
- 라우팅을 효과적으로 수행하려면 라우팅 정보가 현재 상황을 정확히 반영할 수 있도록 관리해야 함
- 라우팅 정보 관리와 관련된 처리 방법
![image](https://user-images.githubusercontent.com/85292541/206208691-6335ad74-0e9e-422b-9d3d-02755e1d8c16.png)


>![image](https://user-images.githubusercontent.com/85292541/206211094-3eab3287-1157-4e3c-9113-2445c8bb2cc6.png)
![image](https://user-images.githubusercontent.com/85292541/206211149-0a6ffdd7-00c5-40e3-9105-96dc8da6e59e.png)
![image](https://user-images.githubusercontent.com/85292541/206211227-44a84c39-59e9-42dc-8cdb-642a523829a9.png)
![image](https://user-images.githubusercontent.com/85292541/206211301-9d05d9f2-b6cd-48a6-9ee4-4f3b532369f8.png)

  ## 혼잡 제어
- **네트워크의 성능 감소 현상이 급격하게 악하되는 현상을 혼잡**이라고 하고, 혼잡 문제를 해결하기 위한 방안을 혼잡 제어라고 함.
- 흐름 제어는 송신 호스트와 수신 호스트사이의 논리적인 점대점 전송 속도를 다룸.
- **혼잡 제어는 더 넓은 관점에서 호스트와 라우터를 포함한 서브넷에서 네트워크의 전송 능력 문제를 다룸**
![image](https://user-images.githubusercontent.com/85292541/206431866-e1568e4d-88ae-4309-bea6-a41e1f9b6248.png)

### > 혼잡의 원인
![image](https://user-images.githubusercontent.com/85292541/206432449-5a96a01c-37ff-4c8f-88a5-f5f81005ae7c.png)
- 혼잡이 심화되는 쥬요인은 전송 시간 초과에 의한 **타임아웃 기능을 통해 패킷들이 재전송되는 데 있음**
- 패킷의 도착 순서가 뒤바뀌면 수신 호스트는 패킷을 보관하거나 그냥 버릴 수도 있음
- 패킷을 버리면 패킷 재전송 현상이 발생해 네트워크 혼잡도 높이는 원인이 됨
- ***라우팅 알고리즘***도 혼잡에 영향을 미칠 수 있음

### > 트래픽 성형
- 혼잡은 트래픽이 특정 시간에 집중되는 버스트 현상에서 기인하는 경우가 많음
- 송신 호스트가 전송하는 패킷의 발생 빈도가 네트워크에서 예측할 수 있는 전송률로 이루어지게 하는 기능이 필요한데, 이를 트래픽 성형이라 함.
> ![image](https://user-images.githubusercontent.com/85292541/206433734-b9467580-f961-45b3-aca8-49e533f529b8.png)

### > 리키 버킷 알고리즘
- 리키 버킷 알고리즘을 사용하면 송신 호스트로부터 입력되는 패킷이 시간대별로 일정하지 않아도, 즉 가변적이어도 깔때기를 통과하면서 일정한 전송률로 변경됨

    ![image](https://user-images.githubusercontent.com/85292541/206434649-a63381d8-e365-4cf9-92b4-51d1b9b9a5fb.png)

### > 혼잡 제거
- 특정 지역에 혼잡이 발생하면 패킷의 전송 경로를 적절히 조정해줌으로써 혼잡이 발생한 곳을 거치지 않도록 가상 회선을 설정
- 호스트와 서브넷이 가상 회선 연결 과정에서 협상
- ECN 패킷을 사용

    ![image](https://user-images.githubusercontent.com/85292541/206434919-b48bbc41-a369-437b-ba51-7e812f4ba94a.png)

## 라우팅 프로토콜

### > 최단 경로 라우팅
- **최단 경로 라우팅 방식은 패킷이 목적지에 도달할때 까지 거치는 라우터 수가 최소화될 수 있도록 경로를 선택**
- 패킷이 목적지까지 도착하느 여러 경로 중 ***가장 짧은 경로***를 선택
    ![image](https://user-images.githubusercontent.com/85292541/206435536-9fa5abed-0fcf-4f13-82f9-f288cd6ef0e2.png)

    ![image](https://user-images.githubusercontent.com/85292541/206435769-50a601a9-e668-414e-832a-ddf4352716e1.png)

### > 플러딩
- 라우터가 자신에게 입력된 패킷을 출력 가능한 모든 경로로 중개하는 방식
- 중요한 데이터를 모든 호스트에 동시에 전달하는 환경에서 제한적으로 사용

## 거리 벡터 라우팅 프로토콜

### > 거리벡터 라우팅 프로토콜
- **거리 벡터 라우팅 프로토콜**은 라우터가 자신과 직접 연결된 이웃 라우터와 라우팅 정보를 교환하는 방식
- **거리 벡터 알고리즘**을 구현하려면 라우터가 세 가지 필수 정보를 관리해야 함
    - ***링크 벡터, 거리 벡터, 다음 홉 벡터***

### > [링크 벡터]
- 링크 벡터 L(x)는 라우터 x와 직접 연결된 이웃 네트워크에 대한 연결 정보를 보관
- 라우터 x와 직접 연결된 네트워크가 M개일 때 링크 벡터 정보는 다음과 같이 나타냄
      
![image](https://user-images.githubusercontent.com/85292541/206437649-4a63b19e-04fa-4525-8c86-6e8dd20f2047.png)
                                                                                                        
![image](https://user-images.githubusercontent.com/85292541/206438309-fbc86ac7-04de-4e61-8128-d27c34f3720c.png) 
- 라우터 R1의 링크 벡터 정보: L(R1) = [포트(Net.1) = 1, 포트(Net.2) = 3]
- 라우터 R2의 링크 벡터 정보: L(R2) = [포트(Net.1) = 1, 포트(Net.4) = 8]
- 라우터 R7의 링크 벡터 정보: L(R7) = [포트(Net.3) = 6, 포트(Net.5) = 9]

### > [거리 벡터]
- 거리벡터 D(x)는 전체 네트워크에 소속된 개별 네트워크들까지의 거리 정보를 관리
- 네트워크가 N개라고 가정하면 거리 벡터 정보는 **거리 벡터 D(x) = [거리(1),거리(2), ....... , 거리(n), ..... ,포트(N)]**
![image](https://user-images.githubusercontent.com/85292541/206440351-89147399-219f-4f25-aaab-b6d5d22572be.png)
           ![image](https://user-images.githubusercontent.com/85292541/206440555-80db8838-615b-406e-8f96-71d6fe4bd6a3.png)

### > [다음 홉 벡터]
- 다음 홈 벡터 H(x)는 개별 네트워크까지 패킷을 전송하는 경로에 있는 다음 홉 정보를 관리
- 보관하는 정보의 수는 전체 네트워크에 속한 네트워크의 개수로, 거리 벡터의 경우와 같음
![image](https://user-images.githubusercontent.com/85292541/206440979-2922543e-1e54-4835-a503-e539aab0cfc8.png)
![image](https://user-images.githubusercontent.com/85292541/206443426-0ad9e3ea-ffc9-4564-9682-a884af4c74d0.png)
      ![image](https://user-images.githubusercontent.com/85292541/206443474-4881f66a-3168-4edc-b5b2-1c8574f240d1.png)

### > **[RIP(Routing Information Protocol)]** 프로토콜
- RIP는 거리 벡터 방식을 사용하는 내부 라우팅 프로토콜 중에서 가장 간단하게 구현된 것
- 소규모 네트워크 환경에 적합하며, 현재 가장 많이 사용하는 라우팅 프로토콜 중 하나
- RIP는 다음과 같은 제한을 두어 개별 거리 정보가 라우팅 테이블에 순차적으로 적용되도록함 
    - 입력되는 거리 벡터 정보가 **새로운 네트워크의 목적지 주소**이면 라우팅 테이블에 적용
    - 입력되는 거리 벡터 정보가 기존 정보와 비교해 **목적지까지 도착하는 지연이 더 적으면 대체함**
        - 이전 정보와 *홉 수*가 같아도 추가 지연 측정을 통해 지연 시간이 적으면 새로운 경로를 선택
    - 임의의 라우터로부터 거리 벡터 정보가 들어왔을 때, 라우팅 테이블에 해당 라우터를 다음 홉으로 하는 등록 정보가 있으면 새로운 정보로 수정

- [그림7-8]에서 라우터 R1의 라우팅 테이블에 [표7-1]과 같은 정보가 기록 되어 있다고 가정
![image](https://user-images.githubusercontent.com/85292541/206446191-09fd2be4-5709-4dbc-a338-d9ae9dbe7c3a.png)-------------------![image](https://user-images.githubusercontent.com/85292541/206446580-d9407bb9-cccd-41f2-b0f9-2fbd40358781.png)
- 라우터 R1과 직접 연결된 **주변 라우터 R2, R3, R4, R6**으로부터 라우팅 정보가 주기적으로 입력
- 임의의 시점에 다음의 거리 벡터 정보가 들어온다고 가정해보자. 각 값은 순서대로 Net.1, Net.2, Net.3, Net.4, Net.5까지의 거리임

     ![image](https://user-images.githubusercontent.com/85292541/206448490-b67936e0-b3c9-4932-852d-3ab22b5ff442.png)

