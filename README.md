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
