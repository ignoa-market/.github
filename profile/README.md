<div align="center">

# IGNOA (이그노아)

> ### "실시간 경매 기반 중고거래 플랫폼"
>
> Ignoa는 사용자가 원하는 중고 상품을 경매와 즉시구매로 거래하고, 입찰 현황을 실시간으로 확인할 수 있는 경매 기반 중고거래 플랫폼입니다.

<br>

<img width="2948" height="1788" alt="image" src="https://github.com/user-attachments/assets/69de73c3-42f4-4f33-93db-ee28ca17e42f" />

</div>

---

<br>

### 📝 Contents

1. [🔗 Links](#-links)
2. [🛠️ Tech Stack](#️-tech-stack)
3. [✨ Key Features](#-key-features)
4. [📐 System Architecture](#-system-architecture)

<br>

---

<br>

### 🔗 Links

- **Service** : [ignoa.woomin.dev](https://ignoa.woomin.dev/app)
- **Overview** : [IGNOA를 소개합니다.](https://familiar-dragon-4ed.notion.site/IGNOA-342bf88cd0f580cc8eadf69b6a4752ae?source=copy_link)
- **API Docs** : [API 명세](https://familiar-dragon-4ed.notion.site/API-336bf88cd0f58150b007e4fa41649d0e?source=copy_link)
- **Dev Notes** : [Project Notion](https://familiar-dragon-4ed.notion.site/Project-IGNOA-336bf88cd0f580b9ae17fc47b088208f?source=copy_link)
- **Logging Conventions** : [로깅 규약](https://familiar-dragon-4ed.notion.site/Logging-Convention-3d0bf88cd0f580bdb1adcd782918146f?source=copy_link) 


<br/>

---

<br>

### 🛠️ Tech Stack

| 구분 | 상세 기술 |
| --- | --- |
| **언어/프레임워크** | Java 21, Spring Boot 3.5.7, Spring Data JPA |
| **프론트엔드** | React, Vite, Tailwind CSS, Radix UI |
| **데이터 저장소** | MySQL 8.4, Redis 7 |
| **인프라(AWS)** | EC2, CloudFront, S3, RDS, ElastiCache |
| **배포/CI-CD** | Docker, GitHub Actions |
| **외부 연동** | Kakao OAuth, Toss Payments |
| **관측성** | Grafana Cloud(Mimir·Loki·Tempo), Alloy, OpenTelemetry, Sentry |


<br>

---

<br>

### ✨ Key Features

| 기능 | 설명 |
|------|------|
| 경매 입찰 | 실시간 입찰, 마감 시 최고가 자동 낙찰. 판매자 마감 연장 지원 |
| 즉시 구매 | 경매 중 즉시 구매가로 구매. 먼저 결제를 마친 구매자만 체결되고, 결제 중에도 입찰은 계속 받음 |
| 안전결제 | Toss Payments 연동(별도 결제 서버). 낙찰·즉시구매 모두 결제 완료 시 거래 확정, 결과 콜백과 상태 조회로 누락 없이 반영 |
| 실시간 입찰 현황 | WebSocket(STOMP) 기반 현재가·입찰 내역 실시간 반영 |
| 1:1 채팅 | 상품 문의와 낙찰 후 거래 채팅. 낙찰자 결제하기, 판매자 결제 요청 |
| 찜 | 관심 상품 저장과 찜 수 표시 |
| 🔐 회원 / 인증 | 이메일 인증, 카카오 소셜 로그인, JWT + RTR. 진행 중인 거래가 있으면 탈퇴 제한, 30일 유예 후 개인정보 삭제 |

<br>

---

<br>

### 📐 System Architecture 

<img width="8956" height="4514" alt="Untitled-2026-04-26-1257" src="https://github.com/user-attachments/assets/48bbd62d-37e6-4f67-a258-59732e1bad97" />

---

