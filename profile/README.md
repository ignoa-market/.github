<div align="center">

## IGNOA

**실시간 경매 기반 LP 중고 거래 플랫폼**

> 중고거래, 더 이상 혼자 흥정하지 마세요. IGNOA가 더 공정한 거래를 만들어드립니다.

<br>

[[웹 바로가기]](https://ignoa-web.vercel.app/app) , 
[[프로젝트 노션]](https://familiar-dragon-4ed.notion.site/Ignoa-336bf88cd0f580b9ae17fc47b088208f?source=copy_link) ,
[[API 명세]](https://familiar-dragon-4ed.notion.site/API-336bf88cd0f58150b007e4fa41649d0e?source=copy_link) ,
[[데이터베이스 설계]](https://familiar-dragon-4ed.notion.site/DB-336bf88cd0f581109574fef029f86e96?source=copy_link) , 
[[ERD]](https://familiar-dragon-4ed.notion.site/ERD-338bf88cd0f580119e8ad86b2f17c1f9?source=copy_link)

<br>
<br>

<img width="800" height="750" alt="image" src="https://github.com/user-attachments/assets/b9d2384d-0dee-4994-b41a-e8a54ac30353" />

<br>
<br>
<br>
<br>


## 프로젝트 소개

LP는 동일한 앨범이라도 발매 연도, 프레싱(pressing), 보관 상태에 따라 가치가 크게 달라지는 수집형 자산입니다.

하지만 기존 중고거래에서는 이러한 특성이 충분히 반영되지 못하고, 판매자의 주관적인 가격 설정에 의존하는 문제가 있습니다.

IGNOA는 이를 해결하기 위해 **경매 기반 거래 구조**를 도입하여 LP의 가치를 시장 참여자가 직접 결정하도록 설계했습니다.

<br>

### 1. 배경

<table>
<tr>
<td width="50%" align="center" valign="middle">
<h3>중고거래 시장 규모</h3>
<p>국내 중고거래 시장 규모 <b>연 30조 원</b> 이상으로 지속 성장 중</p>
</td>
<td width="50%" align="center" valign="middle">
<h3>가격 책정의 어려움</h3>
<p>판매자의 <b>주관적 가격 설정</b>으로<br/>구매자·판매자 모두 불만족</p>
</td>
</tr>
</table>

<br>

### 2. 기존 중고거래의 문제

> 💭 "얼마에 올려야 적당한지 모르겠다"
> 
> 💭 "흥정하는 게 불편하고 피곤하다"  
>
> 💭 "더 좋은 가격에 살 수 있었는데 놓쳤다"  

<br>

### 3. 솔루션

**IGNOA**는 경매를 기본 거래 방식으로 채택해, 가격 책정의 고민과 흥정 피로를 없앱니다.

판매자가 일방적으로 가격을 정하는 구조에서 벗어나, 구매자가 원하는 가격을 직접 제안하고 시장이 적정가를 결정합니다.  
실시간 입찰 경쟁으로 거래 몰입도를 높이고, 즉시 구매 옵션으로 경매가 불편한 사용자도 수용합니다.

</div>

<br>
<br>
<br>
<br>

## 주요 기능

### 1. 실시간 LP 경매 시스템

- WebSocket 기반 실시간 입찰 반영
- 현재 최고가 및 입찰 상태를 즉시 확인 가능
- Redis 기반 경매 상태 관리 및 마감 처리

### 2. 동시성 제어 및 데이터 정합성 보장

- 동일 LP 경매에 대한 다중 사용자 입찰 충돌 방지
- 비관적 락(Pessimistic Lock)을 활용한 동시성 제어
- 트랜잭션 기반 데이터 일관성 유지

### 3. LP 가격 히스토리 기반 시세 분석

- 낙찰 데이터를 기반으로 PriceHistory 테이블 설계
- 평균가 / 최고가 / 최저가 / 가격 변화율 제공
- 거래 빈도를 기반으로 LP 희귀도 간접 판단

### 4. 결제 시스템

- 토스페이먼츠 API 기반 결제 처리
- 에스크로 방식으로 안전한 거래 지원
- 구매 확정 이후 정산 처리

### 5. 1:1 채팅

- LP 거래를 위한 판매자·구매자 간 실시간 채팅
- 상품 상태 및 거래 조율 지원



<br>
<br>
<br>
<br>

<div align="center">


## 기술 스택

### Frontend

  <p>
  <img src="https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react&logoColor=black"/>
  <img src="https://img.shields.io/badge/TypeScript-5.x-3178C6?style=for-the-badge&logo=typescript&logoColor=white"/>
  <img src="https://img.shields.io/badge/Vite-6.x-646CFF?style=for-the-badge&logo=vite&logoColor=white"/>
  <img src="https://img.shields.io/badge/TailwindCSS-4.x-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white"/>
  </p>
  <p>
  <img src="https://img.shields.io/badge/Motion-12.x-FF0055?style=for-the-badge&logo=framer&logoColor=white"/>
  <img src="https://img.shields.io/badge/React_Router-7.x-CA4245?style=for-the-badge&logo=reactrouter&logoColor=white"/>
  <img src="https://img.shields.io/badge/shadcn/ui-Radix-000000?style=for-the-badge&logo=shadcnui&logoColor=white"/>
  <img src="https://img.shields.io/badge/Vercel-배포-000000?style=for-the-badge&logo=vercel&logoColor=white"/>
  </p>

### Backend

  <p>
  <img src="https://img.shields.io/badge/Java-21-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white"/>
  <img src="https://img.shields.io/badge/Spring_Boot-3.x-6DB33F?style=for-the-badge&logo=springboot&logoColor=white"/>
  <img src="https://img.shields.io/badge/Spring_Security-6DB33F?style=for-the-badge&logo=springsecurity&logoColor=white"/>
  </p>

### Database & Cache

  <p>
  <img src="https://img.shields.io/badge/MySQL-8.x-4479A1?style=for-the-badge&logo=mysql&logoColor=white"/>
  <img src="https://img.shields.io/badge/Redis-7.x-FF4438?style=for-the-badge&logo=redis&logoColor=white"/>
  <img src="https://img.shields.io/badge/JPA-Hibernate-59666C?style=for-the-badge&logo=hibernate&logoColor=white"/>
  </p>

### Infrastructure

  <p>
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white"/>
  <img src="https://img.shields.io/badge/Gradle-8.x-02303A?style=for-the-badge&logo=gradle&logoColor=white"/>
  </p>

### External APIs

  <p>
  <img src="https://img.shields.io/badge/OpenAI-API-412991?style=for-the-badge&logo=openai&logoColor=white"/>
  <img src="https://img.shields.io/badge/TossPayments-결제-0052CC?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Kakao-OAuth-FFCD00?style=for-the-badge&logo=kakao&logoColor=black"/>
  </p>

</div>

