---
layout: post
title: Microsoft Azure Fundamentals - AZ-900 개인 정리본
excerpt: MS 애저 클라우드 기본 내용 정리 - Microsoft Azure Virtual Training Day for Microsoft Azure Fundamentals 요약 정리 글
category: [azure]
tags: [azure, cloud, 클라우드, 애저]
---

This exam measures your ability to understand the following concepts: cloud concepts; core Azure services; security, privacy, compliance, and trust; and Azure pricing and support.
온라인에서 진행된 Microsoft Azure Virtual Training Day 요약본입니다. 그냥 듣는 대로 막 써 놓습니다. 책임질 수 없습니다 내용의 검증은 ^^
전체 배우는 내용은 아래 그림과 같네요.

![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597823307150_img515.png)

- toc
{: toc }

{% include tsad10.html %}

# 클라우드 개념

## 클라우드 왜 도입?

-   비용 - 유연하게
-   생산성 - 데이터 사이언스 모델 테스트, 바로 해 볼 수 있다.
-   신기술 진입장벽 낮춤 - HPC, 하둡 등등 자세히 몰라도 테스트 가능

## 클라우드 컴퓨팅

-   컴퓨터 파워
-   스토리지
-   네트워킹
-   분석, 시각화 - 위치 성능 데이터 분석 시각화

## 클라우드의 특성 - 주요 용어

-   내결함성 (Fault tolerance) - 장애를 인정, 빠른 서비스 복구를 고민하고 있다.
    -   백업본으로 부터 복원
    -   여러개 복제하고 있다가 대체
-   고가용성 (High availability) - 장시간 서버 중지시간을 줄이는데 맞춘것
    -   프라이머리 서버, 세컨더리 서버가 바로 대체 사용
    -   한 데이터센터, 혹은 한 지역내 장비/네트워크/ 고장 발생에 대응하는 것
    -   지진 등의 지역적으로 완전히 문제가 생겼을 때는…바로 아래
-   재해 복구 (Disaster recovery)
    -   한데이터 센터, 혹은 한 지역센터가 고장났을 때 재해 복구를 처리해야 한다.
-   확장성 (Scalability)
    -   인기 서비스를 갑자기 확장해야 하는 경우 대응
-   민첩성 (Agility)
    -   확장성과 많이 연계되는
    -   배포할 때는 빠르게 할 수 있는 것 이런것도 민첩성에 들어감.
-   탄력성 (Elasticity)
    -   고무줄 생각 - 늘어날때 줄어들때 scale up/down을 할 수 있다는 개념
    -   확장성과 헷갈리지만, 줄여지는 부분에서 크게 다름
-   글로벌 지원 (Global reach)
    -   말 그대로, 해외 여러곳에서 다 지원이 가능
-   응답 속도 (Customer latency)
    -   글로벌 고객들의 지연시간을 줄여준다.
-   예측 비용 (Predictive cost)
    -   사용한 만큼 과금
-   보안 (Security)
    - 암호화, 감사
    - 뿐만 아니라, 지역적인 규제, 정책 준수사항, 산업 준수사항을 만족해야 한다.
    {% include tsad10.html %}

## 규모 경제 (Economies of scale) - 가격/비용 절감의 효과가 있다.

-   대규모로 운영해서 더 저렴하고 효율적으로 작업 수행
-   이 이점을 고객에게 배분
-   서버 구매, 네트워크 비용등이 절감된다.

## 비용

-   자본지출 (CapEx)
    -   물리적인 인프라 지출 - 노트북, 서버 등등
    -   초기 비용 지출, 감가상각…
    -   높은 초기비용, 투자가치 감소
    -   3년째 필요없는 장비는 손해다…
-   운영비용 (OpEx)
    -   필요에 따라 서비스/제품에 지출
    -   선 결제 비용이 없고, 종량제 사용
    -   퍼블릭 클라우드 비용은 여기에 해당된다. 직접 구축하면 자본지출에도 해당된다.

## 클라우드 - 소비 기반 모델

-   선결제 비용 없음
-   필요한 경우에 추가 리소스 비용 지불
-   필요없는 리소스는 비용 지불이 사라진다.
    {% include tsad10.html %}

## 클라우드 모델

-   퍼블릭 클라우드
    -   클라우드 서비스 or 호스팅 공급자가 소유
    -   인터넷을 통해 리소스를 만들고 지우고 처리한다.
    -   여러조직, 여러 사용자들을 위해 리소스와 서비스가 제공된다.
    -   보안 네트워크 연결을 통해 접근 (인터넷, VPN 등등)
    -   민감한 정보에 대한 부담이 있다.
    -   **CapEx 없음, 민첩성, 소비 기반 모델**
-   프라이빗 클라우드
    -   클라우드 리소스를 사용하는 조직이 소유 및 운영
    -   장점 - 자체 환경, 보안, 민감한 정보
    -   운영 책임이 있음
    -   **제어력, 보안**
-   하이브리드 클라우드
    -   두가지 모델이 함께
    -   일시 프로모션 퍼블릭, 민감 프라이빗, 일시 클라우드 확장을 퍼블릭으로 등등 시나리오
    -   고비용 - 비용상승
    -   **유동성, 준수성 (조직 필요에 따라)**

## 클라우드 서비스 유형

![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597728871119_image.png)

{% include tsad10.html %}

-   온프레미스 (On Premises)
    -   프라이빗 클라우드
-   IaaS
    -   VM
    -   온프레미스 마이그레이션, 테스트 환경 구축 쉽게
    -   종량제 IT 인프라
    -   네트워크를 통해 프로비저닝 및 관리되는 컴퓨팅 인스턴스 인프라라
-   PaaS
    -   Web, app
    -   소프트웨어 개발 테스트 배포에 적합한 모델
    -   인프라는 신경끄고, 응용프로그램에 집중 - 개발환경
    -   고가용성 확장성 알아서 제공
-   SaaS
    ![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597729118690_image.png)

-   Email

-   서비스 유형 비교

![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597729228319_image.png)
{% include tsad10.html %}

# 핵심 Azure 아키텍처 구성 요소 이해

## 지리 (지오그라피)

-   데이터 상주 및 규정 준수 경계를 보존하는 개별 시장
-   둘 이상의 지역을 포함
-   아시아, 유럽, 미주, 중동/아프리카 4개의 geography 지오그래피

## 지역 (Regions) (데이터센터 묶음) - 리전을 선택할 수 있다 사용자는

-   하나 이상의 데이터센터로 구성
-   페어링 리전도 있다. 300마일 정도 떨어져 있음
    -   특정 서비스는 자동 복제
    -   애저 업데이트시에는 동시에 하지 않음
    -   그래도 같은 지오그라피에 존재
-   **사용자는 리전까지 선택한다**. 즉, 어떤 데이터 센터인지 알 수 없다.
    - 리전을 끝점으로 두는 이유는
        - 확장성 측면이 크다
        - 가용성 - 데이터센터의 사고시 천재지변 발생시 백업할 수 있도록 리전 설계되어 있음
        - 지역 자체가 문제라 리전 전체가 내려가는 것에 대비해서, **짝궁 리전 (Paired Region)** 이 있다
            - 한국은 중부, 남부가 짝꿍으로 되어 있다. 디지털 리커버리 용도
    ![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597730034543_image.png)
    {% include tsad10.html %}

## 가용성 옵션 (Availability Options)

![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597731368185_image.png)

-   VM1이 물리적 장애 발생
    - 가용성 유지를 위해서는 반드시 연속적 서비스 운영을 위해 처음부터 2개이상의 VM을 배포해야 한다.
    - 물리적으로 같은 DC에 같은 서버에 2개의 vm이 배포되면 마찬가지로 가용성이 안되므로, AvSet 을 두고 따로 다른 물리적 서버에 놓일 수 있도록 서비스를 제공한다.
    - 즉, 분산 배포, AvSet 이 중요하다. Fault Domain 단위로 분리 배포됨..
    ![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597730243308_image.png)

-   긴급 보안 패치 발생시 업데이트 도메인 단위로 물리적 서버가 중지될 수 있다.
    - 하필 업데이트 도메인에 vm이 다 포함되면 한꺼번에 중지될 수 있으므로 이것도 알아서 잘 배포해 준다. 가용성을 위해
    ![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597730358748_image.png)
    {% include tsad10.html %}

-   데이터센터#1 이 전체가 장애가 생기는 경우
    - Fault domain, update domain 잘 배치해서 vm 이 배포되었지만 낭패다…
    - 따라서, Av Zone 이라는 개념이 추가되었다.
    - 데이터 센터도 나눠서 배포해준다.
    ![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597730505238_image.png)

-   그림 참고
    ![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597730763666_image.png)
    ![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597730854428_image.png)
    {% include tsad10.html %}

-   가용성 집합을 이용한 구성에서도 리전이 전체가 망가지면 보장 받기 힘들다
-   즉, 가용성 존 이 필요한 이유가 된다.
    ![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597731197542_image.png)

## 물리적 요소 정리

![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597731448578_image.png)

## Azure 논리적 구성요소 정리

-   구독
    - 비용 - 과금
    - 접근제어 - 아무나 못 들어오게
    - 기술적 제한을 가질 수 있는 단위 - 하나의 구독에 최대 만개 vm 생성 가능, 그 이상을 하려면 구독을 추가해야 한다.
        - 리소스 그룹은 방이다.
    ![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597731974061_image.png)
    ![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597732084384_image.png)
    {% include tsad10.html %}

-   한 사람이 1개 이상의 여러개의 구독 사용 가능
    -   다른 회사에 초대도 가능..
-   관리그룹 (Management Group)
    - 무조건 루트관리그룹이 있어요…
    - 하나의 관리 그룹은 여러개의 구독 포함 가능
    - 구독은 관리그룹에서 적용된 사항을 **상속 가능**
    - 하나의 디렉토리에서 **최대 10,000 개 그룹, 6개의 트리레벨 지원**
    ![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597732234886_image.png)

-   리소스 그룹
    - **모든 애저리소스는 하나의 리소스 그룹에만 존재**
    - 동일 라이프사이클 가진 리소스에 대한 논리적 그룹 (하나의 서비스와 연관된 그룹 개념)
    - 기능별로 관리 그룹을 나눠도 된다.
    - 권한 관리가 용이
    ![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597732331847_image.png)

-   Azure Resource Manager
    ![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597732472375_image.png)

        - ARM 이라고 불린다. 그리고, 리소스는 JSON 형태의 템플릿으로 배포가 가능하다.
        - UI 가 편하면 포털을 이용을 많이 한다.

    {% include tsad10.html %}

-   정리
    ![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597732576389_image.png)

# 핵심 Azure 서비스 및 제품

## 컴퓨팅

-   온디맨드 컴퓨팅 서비스
-   VMs - 가상머신 만들기 데모
    -   데이터 스토리지는 기본으로 임시 저장소로 잡힌다. 거의 휘발성이라고 보면 된다.
    -   vm 자동 종료 옵션을 쓰자. 비용절감
-   VM Scale sets - 자동확장지원
    -   가용성 집합과 유사
    -   가용성 집합과는 다르게 동일한 VM이 배포된다. - 무슨뜻인지? ㅎㅎ
-   App services - 웹앱 서비스 데모
-   Functions
-   컨테이너 서비스
    -   ACI - 애저 컨테이너 인스턴스
    -   AKS - 애저 쿠버네티스 서비스, 컨테이너 오케스트레이션 서비스

## 네트워크서비스

{% include tsad10.html %}

-   Azure virtual network
-   Load Balancer - 여러개 백엔드 서비스 요청 분산
-   VPN G/W
-   Application G/W - 트래픽 로드밸런서
-   CDN - 웹 콘텐츠 효율적 전달

## 스토리지

-   데이터 형태
    ![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597735440083_image.png)

-   저장소 서비스 - (스토리지 어카운트, 스토리지 계정 라고 부르네) **스토리지 계정 예제 시연함**
    - 컨테이너 (블럭 스토리지)
    - 테이블 - 처리량이 적을때는 DB 대신 사용, 빠른 key/value 조회 지원
    - 큐 - “서비스 버스”의 라이트 버전이라고 생각하면 됨
    ![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597735621845_image.png)

-   스토리지 계정 데모에서 보면,
    - 복제 옵션이 LRS 로컬 중복, GRS 지역 중복, RA-GRS 읽기 액세스 지역 중복 3가지 옵션이 있네
    - 계층구조 네임스페이스 - “사용”하면 빅데이터 처리 가능한 Data Lake storage 처럼 사용 가능
    - 스토리지 계정이 생성되면, 그안에서 위에 보여지는 저장소 서비스를 선택할 수 있다. 테이블, 컨테이너 등등등
    - public endpoint 로 접근한다 하더라도, 키를 이용하여 접근 제어를 할 수 있다. 키가 있어야 한다.
    {% include tsad10.html %}

## 데이터베이스 서비스

-   Cosmos DB - NOSQL 서비스, 글로벌 분산 무제한 확장, 정형, 반정형 다 적당
-   SQL Database - MS SQL server RDBMS 지원, 정형 적당
-   Database migration
-   **SQL 데모 시연**
    -   간단한 연결 테스트는 쿼리편집기 라는 메뉴를 활용

## 마켓플레이스

-   솔루션 제공

# Azure 솔루션 & Azure 관리도구

## Azure 솔루션

-   앗!! 시간 놓침 이전 데이터는 먼지 몰라 ㅠㅠ
-   DevOps
    ![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597814170113_image.png)
    {% include tsad10.html %}

## Azure 관리도구

-   Azure 포털 (GUI)
-   파워쉘, CLI
-   Azure Cloud Shell
-   Azure Advisor - 성능, 보안, 가용성 향상
    -   Best practice 기반
    -   비용절감 기회 제공
-   Azure quick start template 시연
    - Simple Windows VM 데모
        - Edit 템플릿, JSON 수정으로 쉽게 배포 가능
        - CLI, 파워쉘 수행도 가능
    ![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597814649417_image.png)

# 보안, 개인 정보 보호, 규정 준수 및 신뢰

## 보안

-   심층방어 (Defense in depth) - 여러수준의 방어, 단계별로 다른 전략, 격리
-   공동 책임 (Shared security)
    ![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597815426855_image.png)

{% include tsad10.html %}

-   방화벽 (Azure Firewall)
    -   IP 주소 기반 액세스 컨트롤 - **PaaS 형태의 방화벽 서비스** (상태저장, 관리)
    -   포털에서 Rule 등을 제어할 수 있다.
    -   아웃바운드에서는 application level protection 도 수행한다.
    -   트래픽 필터링
    -   고가용성 내장, 무제한 클라우드 확장성
    -   Azure 모니터 로깅 사용
    -   **Azure Application Gateway** 또한 WAF (응용프로그램방화벽 기능) 제공한다.
        -   인바운드 보호 기능은 WAF에서만 제공
-   DDoS 보호 - Azure Distributed Denial of Service 보호
    -   서비스 가용성 미치기 전에 트래픽 제거
    -   기본으로 베이직 기능은 제공
    -   스탠다드 버전은 머신러닝 기반의 어댑티브 튜닝등의 서비스를 말한다.
    -   제일 앞에서 해 주는 것이 좋다.
-   네트워크 보안 그룹 (NSG, Network Security Groups)
    -   Azure 가상 네트워크에서 애저 리소스로의 네트워크 트래픽 필터링 (Web, WAS, DB 등등)
    -   1차 방화벽 통과 이후의 동작이라고 보면 된다.
    -   규칙 설정, 필터링
    -   방화벽은 정문지기
        -   여러개의 구독을 커버할 수 있다.
    -   NSG 는 로비 혹은 층별 관리로 보면 된다.
-   Azure 네트워크 보안 솔루션 선택
    - 네트워크 보안 데모 시연
    - 가상 네트워크 만들기 - 경계영역,
        - 서브넷 추가
        - 보안 - DDoS, 방화벽 선택
    - 이제 VM과 같은 서비스에서 네트워킹 메뉴에서 네트워크 선택, 룰 지정등 여러가지 옵션을 선택할 수 있다.
    ![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597816125611_image.png)
    ![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597816295966_image.png)

## AD 인증

-   인증 vs 권한
    -   인증 - 리소스 접근을 원하는 사람 또는 서비스를 식별하는 것
    -   권한보호 - 접근 관리
-   AAD (Azure Active Directory)
    -   클라우드 기반 신원확인 및 접근 관리 서비스
    -   웹인증에 초점, SSO
    -   응용프로그램, 디바이스 관리
    -   B2B - 다른 AD 에 있는 사용자 인증
    -   B2C ID 서비스 - 트위터, 페이스북
-   다단계인증 (Multi-Factor Authentication)
    - 두개이상의 요소를 요구
    - 당신이 알고 있는 것 - 패스워드
    - 당신이 가지고 있는 것 - 휴대폰 앱
    - 당신임을 증명할 수 있는 것 - 생체정보, 홍채, 지문
    {% include tsad10.html %}

## 보안 도구 및 기능

-   보안센터 (Security Center)
    -   Azure, On-premise 워크로드 서비스에 대한 위협 보호 기능 제공 모니터링
    -   포털에 보안센터에서 보면 된다. 보안 점수 등등, 무료/유료 버전 있음
    -   권장사항 제공
-   보안센터 사용 시나리오
    - 감지, 평가, 진단까지만 제공
    ![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597817216665_image.png)

-   키 자격증명 (Key Vault)
    -   비밀번호, 키, 인증서 저장을 안전하게 중앙관리 해라..
    -   중앙 집중식 클라우드에 저장, 접근 권한을 제어
    -   하드웨어 보안 모듈을 지원
-   정보보호 (Azure Information Protection - AIP)
    -   레이블 적용 - 문서,전자메일 분류 보호
    -   AIP Label 적용
        -   관리자가 정의한 규칙 조건을 자동으로 사용 가능
        -   수동도 지원
-   고급위협보호 (Azure Advanced Threat Protection - ATP)
    - 지능형 위협, 손상된 ID 및 악의적인 내부자 식별 탐지 보안 솔루션
    - ATP
        - Portal - 모니터링 대응 위한 전용 포털
        - Sensor - 도메인 컨트롤러에 설치
        - Cloud service
    {% include tsad10.html %}

## Azure 거버넌스 방법론

-   정책 (Policy)
    -   규칙, 표준, 서비스 수준 계약 (SLA)
    -   정책 준수 모니터링
    -   정책 정의 → 리소스에 정책 할당 → 평가 검토
-   정책 이니셔티브 (Policy Initiatives)
    -   정책 할당을 그룹화해서 처리 - 하나하나 하면 관리가 너무 많다.
    -   정의 → 할당
-   정책 만들기 데모 시연…
    -   정책을 선택하고, 제작쪽에 정의, 할당을 하면 된다.
    -   정의에서는 이미 많은 정의와 이니셔티브가 있다. 기본 제공이 많다.
    -   할당>정책할당> 사용가능한 정의 검색..리소스 그룹에 한국리전만 배포 허용등의 정책을 할당할 수 있다.
-   역할 기반 액세스 제어 (RBAC)
    -   리소스에 대한 세분화된 액세스 관리 제어
    -   팀내 책임 분리
    -   포털 및 리소스 접근 관리를 제어할 수 있다.
    -   데모
        -   액세스 제어(IAM)
-   잠금 (Resource Locks)
    - 리소스 보호
    ![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597818192232_image.png)
    {% include tsad10.html %}

-   Azure Blueprints (큰그림)
    -   리소스, 규정, 보안, 정책, 권한 관리등을 즉시 재생성할 수 있도록 재사용 가능한 환경 정의 생성
    -   문서, ARM 템플릿 등도 가능하지만 Blueprints 활용하자
    -   버전 관리 가능하다

## 모니터링 및 리포트

-   태그
    -   메타데이터 지원
    -   키-값 의 쌍으로 구성
    -   논리적 리소스 분류
    -   청구, 관리용으로 데이터 분석에 용이
-   모니터 (Monitor)
    - 클라우드, 온프레미스 환경 포함해서 가용성  성능 극대화 모니터링
    - 매트릭스, 로그 형태로 관리된다. - 스토리지 어카운트
    ![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597818711171_image.png)
    - 시연

-   서비스 건강 (Service Health)
    - Azure Status - 전체 서비스의 대략 상태 확인
    - Service Health - 내가 배포한 리소스에 대한 리전별 확인
    - Azure Resource Health - 개별 리소스에 대한 상태 확인, 앱서비스 등등등
    {% include tsad10.html %}

## 개인정보 보호, 규정준수, 표준

-   규정 준수 약관 및 요구 사항
    -   보안이 중요
    -   규칙 규정 요구사항에 잘 맞추기 위해 노력 - 지역별 산업별
    -   CJIS 미국 형법, HIPAA 건강, CSA STAR, ISO, GDPR 보안, NIST 등등등
    -   90개 이상의 규정 만족
-   개인정보 보호
    -   privacy statement - 어떤 데이터, 어떻게, 어떤 목적인지 등등
-   신뢰 센터 - trustcenter
-   서비스 신뢰 포털 (STP) - servicetrust.microsoft.com
    -   규정 문서, 간행물 제공
-   규정 준수 관리자
    -   평가
-   보안센터 데모
-   Azure Government 서비스
    -   미국 연방 기관, 지방 정부 등이 활용
    -   퍼블릭 영역에 있지만 별도 인스턴스처럼 사용되고 있다.
    -   중국도 있음. 21Vianet 업체를 통해 운영

# Azure 가격 책정 및 지원

{% include tsad10.html %}

## 구독

-   구독
    - 3가지 기능 - 비용, 접근 제어, 기술적 한계
    - 청구, 접근 제어에 대한 기능을 제공
    - 한계정이 한개 이상의 구독을 가질 수 있다.

-   구독 종류
    - 무료
    ![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597820650854_image.png)
    - 종량제 (Pay-as-you-go)
    - 기업계약
    - 학생

## 비용계획 관리

{% include tsad10.html %}

-   Azure 제품 및 서비스 구매
    -   기업 고객 - 일반적으로 연간 협상 금액 지출
    -   웹 직접 구매
    -   클라우드 솔루션 공급자 (CSP) 통해 구매
-   비용 영향 요인
    -   리소스 타입
    -   서비스 - 구매 형태에 따라 다름
    -   로케이션 - 지역에 따라 달라짐
-   청구 목적의 영역
    -   모든 인바운드 데이터는 무료
    -   아웃바운드 데이터 전송은 과금이 된다.
    -   영역으로 나눈다.
        -   영역 1~4로 나눠 진다. 요금이 다를 수 있다.
-   가격 계산기
    -   미리 산정해 본다.
-   총 소유 비용 계산기
    -   온프레미스, 애저 비교도 가능
    -   데모 시연 - 시나리오 기반의 계산도 가능하다.
-   비용 최소화
    ![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597821521106_image.png)

-   비용 관리 (Cost Management)
    -   예산, 경고, 보고서, 권장 등등 제공
    -   포털에서 비용관리 + 청구 선택하면 볼 수 있다.

## 기술 지원 옵션

{% include tsad10.html %}

-   기술지원 옵션
    -   5개 단계 basic, developer, standard, professional direct, premier
    -   기술지원은 개발자 그룹 부터
-   지식 센터
    -   포럼, 티켓

## SLA (Service level agreement)

-   SLA
    - 약속 - 서비스와 제품에 대한 약속 (성능 표준)
    - 예) SQL 99.9% 연결 보장
    - 충족 안되면 서비스 크레딧 제공..
![](https://paper-attachments.dropbox.com/s_50FC24DA1F96385BF7C42E69C6218B7405B37A05EFD7ABBAAD86CFF420F2FA7E_1597822439073_image.png)

-   복합 SLA
    -   서비스별 다른 SLA
    -   웹 디비 포털 운영시 복합적이다.
    -   이럴때는 99.95% \* 99.99% 곱하기로 제공…좀 떨어진다.

## 서비스 수명 주기

{% include tsad10.html %}

-   preview - 평가 목적으로 미리보기 제공, 베타,
    -   비공개 미리 보기 - 특정 고객에게 제공
    -   공개 미리보기 - 모든 고객이 사용가능 평가목적으로
        -   가격이 좀 저렴하다.
        -   기술지원이 어렵다.
-   포탈 미리보기
    -   포탈도 미리보기가 있다. 포털에 대한 새로운 기능
-   GA - General Availability
    -   정식 버전
-   기능 업데이트 모니터링
    -   분류되어 있다. 이용가능, 미리보기, 개발중 등등
