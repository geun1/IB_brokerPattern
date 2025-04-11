# 브로커 패턴 (Broker Pattern)

## 개요

브로커 패턴은 분산 소프트웨어 시스템을 구조화하는 아키텍처 패턴으로, 분리된 컴포넌트들이 원격 서비스를 호출하여 상호작용하는 시스템에서 유용합니다. 브로커 컴포넌트가 통신을 관할하고, 결과와 예외 전송 역할을 담당합니다.

## 주요 구성요소

-   **클라이언트(Client)**: 사용자 기능을 구현하고 서버의 서비스에 접근
-   **서버(Server)**: 서비스를 구현하고 로컬 브로커에 자신을 등록
-   **브로커(Broker)**: 클라이언트와 서버 간의 중개자 역할, 서버 등록 및 요청 전달
-   **클라이언트측 프록시(Client-side Proxy)**: 클라이언트와 브로커 사이의 중재 역할
-   **서버측 프록시(Server-side Proxy)**: 서버와 브로커 사이의 중재 역할
-   **브리지(Bridge)**: 서로 다른 브로커 시스템 간 통신을 담당

## 폴더 구조

brokerPattern/
├── client/
│ ├── client_app.py # 클라이언트 애플리케이션
│ └── client_proxy.py # 클라이언트측 프록시 구현
├── server/
│ ├── server_app.py # 서버 애플리케이션
│ └── server_proxy.py # 서버측 프록시 구현
├── broker/
│ ├── broker_server.py # 브로커 서버 구현
│ └── service_registry.py # 서비스 등록 및 관리
├── bridge/
│ └── bridge.py # 브리지 구현
├── common/
│ ├── interfaces.py # 공통 인터페이스 정의
│ └── marshaling.py # 데이터 마샬링/언마샬링 기능
├── examples/
│ ├── basic_example.py # 기본 사용 예제
│ └── distributed_example.py # 분산 시스템 예제
└── README.md # 프로젝트 설명 문서

## 구현 방법

1. **객체 모델 정의**: 시스템의 객체 모델을 정의하거나 기존 모델 활용
2. **상호운용성 결정**: IDL 또는 바이너리 표준을 통한 컴포넌트 간 상호작용 방식 결정
3. **API 정의**: 브로커가 제공하는 API 설계
4. **프록시 구현**: 세부 구현을 숨기는 프록시 객체 구현
5. **브로커 설계**: 핵심 브로커 컴포넌트 구현
6. **메시지 형식 정의**: 컴포넌트 간 통신을 위한 메시지 형식 정의

## 장점

-   위치 투명성 제공 (Location Transparency)
-   컴포넌트의 가변성과 확장성 보장
-   플랫폼 간 이식 가능성 제공
-   다양한 브로커 시스템 간 상호운용성 지원
-   컴포넌트 재사용성 확보

## 단점

-   직접 통신에 비해 효율성 저하
-   브로커 장애 시 전체 시스템 영향 (단일 장애점)
-   테스트와 디버깅의 복잡성
