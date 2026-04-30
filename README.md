# EatoMeter

Spring Boot 기반 리뷰 신뢰도·개인화 추천 맛집 플랫폼입니다.  
사용자는 맛집 정보를 검색하고 리뷰를 작성할 수 있으며, 리뷰 신뢰도와 개인화된 정보를 바탕으로 음식점 정보를 확인할 수 있습니다.  
관리자는 가게 승인, 신고 처리, 회원 관리 등 운영 기능을 수행할 수 있습니다.

## Tech Stack

### Backend
- Java 17
- Spring Boot
- Spring Data JPA
- Spring Web
- Spring Validation
- QueryDSL
- Lombok

### Frontend
- Thymeleaf
- HTML
- CSS
- JavaScript

### Database
- MySQL

### Build / Tool
- Maven
- Git / GitHub

## Main Features

### User
- 회원가입 및 로그인
- 맛집 검색 및 필터링
- 리뷰 작성 및 관리
- 맛집 찜 및 방문 기록 관리
- 신고 내역 확인

### Restaurant
- 가게 등록
- 가게 정보 조회
- 메뉴 정보 관리
- 카테고리 및 조건 기반 검색

### Admin
- 회원 관리
- 가게 승인 및 관리
- 신고 내역 조회 및 처리
- 공지사항 및 이벤트 관리
- 문의 관리

## Project Structure

```text
src/main/java/com/dita
├── config        # Spring 설정
├── controller    # 요청 처리 Controller
├── domain        # JPA Entity
├── dto           # 화면 및 계층 간 데이터 전달 객체
├── persistence   # Repository
├── service       # 비즈니스 로직
└── vo            # View Object
```

## How to Run

```bash
git clone https://github.com/ShinWonJin01/eatometer-spring-project.git
cd eatometer-spring-project
```

1. Java 17과 MySQL을 설치합니다.
2. MySQL에서 `eatometer` 데이터베이스를 생성합니다.
3. `src/main/resources/application.properties` 파일에서 MySQL 사용자명과 비밀번호를 본인 환경에 맞게 수정합니다.
4. 아래 명령어로 프로젝트를 실행합니다.

```bash
./mvnw.cmd spring-boot:run
```

5. 브라우저에서 아래 주소로 접속합니다.

```text
http://localhost
```

> 데이터베이스 초기 데이터가 없는 경우, 맛집 목록이나 검색 결과가 비어 있을 수 있습니다.

## View Guide

이 프로젝트는 모바일 화면 기준으로 제작되었습니다.
PC 브라우저에서 확인할 경우 Chrome DevTools의 모바일 화면 모드를 사용하는 것을 권장합니다.

1. Chrome에서 `F12`를 눌러 DevTools를 엽니다.
2. 왼쪽 상단의 Toggle device toolbar 아이콘을 클릭합니다.
3. 화면 크기를 모바일 기준으로 설정한 뒤 확인합니다.

## Note

네이버 지도 API는 별도의 API Key 설정이 필요합니다.
API Key가 설정되지 않은 환경에서는 지도 영역이 정상적으로 표시되지 않을 수 있습니다.

## My Role

- Spring Boot 기반 웹 애플리케이션 구조 설계 및 구현
- Controller, Repository, Service 계층을 활용한 기능 구현
- MySQL 기반 데이터 처리 및 JPA Repository 활용
- 회원, 리뷰, 신고, 가게 관리 관련 기능 구현
- 관리자 페이지의 신고 처리 및 가게 승인 흐름 구현
- Thymeleaf, HTML, CSS, JavaScript 기반 화면 연동

## Troubleshooting

### 1. 신고 횟수에 따른 회원 정지 처리

#### Problem
신고가 접수되었을 때 단순히 신고 내역만 저장하면, 신고 누적 횟수에 따라 회원 상태를 다르게 제어하기 어려웠습니다.

#### Cause
신고 데이터와 회원 상태 데이터가 분리되어 있어, 신고 처리 시 회원의 정지 여부와 정지 기간을 함께 갱신하는 흐름이 필요했습니다.

#### Solution
신고 처리 로직에서 신고 대상 회원의 누적 신고 횟수를 확인하고, 기준에 따라 회원 상태와 정지 기한을 갱신하도록 구현했습니다.

#### Result
관리자가 신고를 처리할 때 회원 제재 흐름을 일관성 있게 관리할 수 있도록 개선했습니다.

### 2. 관리자 기능과 사용자 기능 분리

#### Problem
일반 사용자와 관리자가 사용하는 기능이 다르기 때문에, 접근 가능한 화면과 기능을 구분해야 했습니다.

#### Solution
관리자 관련 요청과 일반 사용자 요청을 Controller 단위로 분리하고, 화면에서도 관리자 메뉴와 사용자 메뉴를 구분하여 처리했습니다.

#### Result
사용자 기능과 관리자 기능의 흐름을 명확히 나누어 유지보수성을 높였습니다.
