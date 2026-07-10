<div align="center">

# IGNOA (이그노아)

> ### **"실시간 경매를 통해 내 손안에서 거래하는 중고 마켓플레이스"**
>
> Ignoa는 사용자가 원하는 중고 상품을 경매와 즉시구매로 거래하고, 입찰 현황을 실시간으로 확인할 수 있는 경매 기반 중고거래 플랫폼입니다.

<br>

<img width="3248" height="2122" alt="image" src="https://github.com/user-attachments/assets/08bfba67-73b9-4f8f-86c8-9806684f26ca" />

</div>

---

<br>

## 📝 Contents

1. [🔗 Links](#-links)
2. [🛠️ Tech Stack](#️-tech-stack)
3. [✨ Key Features](#-key-features)
4. [📐 System Architecture & ERD](#-system-architecture--erd)

<br>

---

<br>

## 🔗 Links

- **Service** : [ignoa.wisoft.dev](https://ignoa.wisoft.dev/app)
- **API Docs** : [Swagger]()
- **Overview** : [IGNOA를 소개합니다.](https://familiar-dragon-4ed.notion.site/IGNOA-342bf88cd0f580cc8eadf69b6a4752ae?source=copy_link)
- **Dev Notes** : [Project Notion](https://familiar-dragon-4ed.notion.site/Project-IGNOA-336bf88cd0f580b9ae17fc47b088208f?source=copy_link)

<br/>

---

<br>

## 🛠️ Tech Stack

| 구분 | 기술 |
|------|------|
| **Frontend** | TypeScript, React 18, Vite, Tailwind CSS |
| **Backend** | Java 21, Spring Boot 3.5.7, Spring Security, WebSocket |
| **Database** | MySQL 8.0, Redis 7 |
| **Infra** | Docker, GitHub Actions, AWS S3, RustFS |
| **Auth** | JWT, Kakao OAuth2 |

<br>

---

<br>

## ✨ Key Features

| 기능 | 설명 |
|------|------|
| 🔨 경매 입찰 | 경매 등록된 상품에 실시간으로 입찰, 마감 시 최고가 낙찰 |
| ⚡ 즉시 구매 | 경매 진행 중 즉시 구매가로 바로 거래 체결 |
| 🔔 실시간 입찰 현황 | WebSocket 기반 입찰 내역 실시간 반영 |
| 🔐 회원 / 인증 | 이메일 인증, 카카오 소셜 로그인, JWT + RTR |

<br>

---

<br>

## 📐 System Architecture & ERD

<details>
<summary><b>👉 시스템 아키텍처 이미지 보기</b></summary>

<br/>

<img width="5866" height="3944" alt="시스템 아키텍쳐" src="https://github.com/user-attachments/assets/0465f8d2-0309-48ad-a69e-eee3fa199592" />

</details>

<br/>

<details>
<summary><b>👉 ERD 이미지 보기</b></summary>

<br/>

![IGNOA ERD](IGNOA_ERD.png)

</details>

---

