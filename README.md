# 🏰 Eureka Server for Reservation Service

본 프로젝트는 Spring Cloud Netflix Eureka를 사용한 **Discovery Server**입니다. 예약 시스템 내의 모든 마이크로서비스를 위한 중앙 레지스트리 역할을 하며, 호스트 이름과 포트를 하드코딩하지 않고도 서비스들이 서로를 찾고 통신할 수 있도록 지원합니다.

---

## ✨ 주요 기능

- **🌐 서비스 디스커버리:** 서비스 등록 및 검색을 위한 Eureka 서버 제공
- **🚀 Spring Boot 3.5.3:** 최신 Spring Boot 버전을 기반으로 구축
- **☕ Java 17:** Java 17 LTS 사용
- **🛠️ Gradle:** Gradle 빌드 도구로 관리

---

## 🚀 시작하기

### ✅ 요구 사항

- Java 17 이상
- Gradle 8.14.3 또는 호환 버전

### ⚙️ 설치 및 실행

1.  **저장소 복제:**
    ```bash
    git clone <repository-url>
    cd eureka-server
    ```

2.  **애플리케이션 실행:**
    프로젝트에 포함된 Gradle wrapper를 사용하여 서버를 실행할 수 있습니다.

    - **macOS/Linux:**
      ```bash
      ./gradlew bootRun
      ```
    - **Windows:**
      ```bash
      .\gradlew.bat bootRun
      ```

    서버는 기본적으로 `8761` 포트에서 시작됩니다.

---

## 🔧 설정

주요 설정은 `src/main/resources/application.yml` 파일에 있습니다.

- **포트:** 서버는 `8761` 포트에서 실행됩니다.
- **애플리케이션 이름:** 애플리케이션은 `eureka-server`로 등록됩니다.
- **Eureka 설정:**
  - `eureka.client.register-with-eureka: false`
  - `eureka.client.fetch-registry: false`

  > 💡 위 설정은 현재 인스턴스가 독립 실행형 Eureka 서버이며 스스로에게 등록을 시도하지 않음을 나타냅니다.

---

## 🔒 보안

보안 설정은 `src/main/java/com/reservation/eureka/security/SecurityConfig.java` 파일에 있습니다.

현재 설정은 모든 요청을 허용하고(`authorizeHttpRequests( auth -> auth.anyRequest().permitAll())`) CSRF, HTTP Basic 인증 및 폼 기반 로그인을 비활성화합니다. 이를 통해 모든 서비스가 별도의 인증 없이 등록할 수 있습니다.

---

## 🔗 엔드포인트

- **Eureka 대시보드:** [http://localhost:8761](http://localhost:8761)
- **Actuator 엔드포인트:** 관리 엔드포인트는 `/actuator` 경로 아래에 노출됩니다 (예: `/actuator/health`).