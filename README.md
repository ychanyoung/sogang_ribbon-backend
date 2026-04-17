# 서강 리본 - Backend

서강 리본 서비스의 백엔드 API 서버입니다.
Notion API로 관리되는 가게 정보를 제공하고, 인증·투표·프로모션 기능을 처리합니다.

## 기능

- 가게 정보 조회 API (Notion DB 연동)
- 카테고리 / 가격대 / 리본 지수 기반 필터링
- 할인·협업 프로모션 관리
- 학생 참여 실시간 투표 (WebSocket / STOMP)
- 소셜 로그인 (카카오 / 네이버 OAuth2)

## 기술 스택

| 항목 | 기술 |
|------|------|
| 프레임워크 | Spring Boot 3.4 |
| 언어 | Java 21 |
| 인증 | Spring Security + JWT + OAuth2 |
| ORM | Spring Data JPA |
| DB | MySQL 8 |
| 캐싱 | Redis |
| 빌드 | Gradle |
| 컨테이너 | Docker |
| CI/CD | Jenkins |

## 시작하기

### 요구 사항

- Java 21
- MySQL 8
- Notion API Key & Database ID

### 환경 변수 설정

`.env.example`을 복사해 `.env`를 생성합니다.

```bash
cp .env.example .env
```

```env
DB_USERNAME=root
DB_PASSWORD=your_password
NOTION_API_KEY=your_notion_api_key
NOTION_DATABASE_ID=your_notion_database_id
```

### DB 생성

```sql
CREATE DATABASE sogang_ribbon CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

### 실행

```bash
# Gradle wrapper로 실행
./gradlew bootRun
```

[http://localhost:8080](http://localhost:8080) 에서 동작합니다.

### 빌드

```bash
./gradlew build
java -jar build/libs/ribbon-0.0.1-SNAPSHOT.jar
```

## 프로젝트 구조

```
src/main/java/com/sogang/ribbon/
├── RibbonApplication.java
├── controller/    # REST API 엔드포인트
├── service/       # 비즈니스 로직
├── repository/    # JPA Repository
├── domain/        # 엔티티
├── dto/           # 요청/응답 객체
└── config/        # Security, CORS 등 설정
```

## 관련 레포지토리

- Frontend: [sogang_ribbon-frontend](https://github.com/ychanyoung/sogang_ribbon-frontend)
