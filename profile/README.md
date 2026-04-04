<div align="center">

## IGNOA

실시간 경매 기반 중고 거래 플랫폼

> 중고거래, 더 이상 혼자 흥정하지 마세요. IGNOA가 더 공정한 거래를 만들어드립니다.

<br>

[[웹 바로가기]](https://ignoa-web.vercel.app/login) , 
[[프로젝트 노션]](https://familiar-dragon-4ed.notion.site/Ignoa-336bf88cd0f580b9ae17fc47b088208f?source=copy_link) ,
[[API 명세]](https://familiar-dragon-4ed.notion.site/API-336bf88cd0f58150b007e4fa41649d0e?source=copy_link) ,
[[데이터베이스 설계]](https://familiar-dragon-4ed.notion.site/DB-336bf88cd0f581109574fef029f86e96?source=copy_link) , 
[[ERD]](https://familiar-dragon-4ed.notion.site/ERD-338bf88cd0f580119e8ad86b2f17c1f9?source=copy_link)

<br>
<br>

<img width="550" height="750" alt="image" src="https://github.com/user-attachments/assets/63200c37-6e27-44a0-aa10-c3f89f2035db" />

<br>
<br>
<br>
<br>


## 프로젝트 소개

Ignoa는 경매를 기본 거래 방식으로 채택한 중고거래 웹 서비스입니다.

판매자가 가격을 고정하는 기존 중고거래 구조에서 벗어나, 구매자가 직접 가격을 제안하고 시장이 적정가를 결정합니다.  
**실시간 입찰, 즉시 구매, AI 기반 취향 큐레이션**을 통해 더 공정하고 몰입감 있는 거래 경험을 제공합니다.

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

<img width="987" height="819" alt="image" src="https://github.com/user-attachments/assets/2da82ff3-64b7-434d-9074-78f5db04073b" />


### 1. 실시간 경매

- 경매 진행 중 입찰이 발생할 때마다 WebSocket으로 즉시 반영됩니다.
- 페이지 새로고침 없이 현재 최고 입찰가와 남은 시간을 실시간으로 확인할 수 있습니다.

<br>

### 2. 즉시 구매

- 판매자가 즉시 구매가를 설정한 경우, 경매 진행 중에도 해당 가격으로 바로 거래를 성립할 수 있습니다.
- 즉시 구매가 성립되면 경매는 즉시 종료됩니다.

<br>

### 3. 안전 결제

- 토스페이먼츠 API를 연동한 에스크로 방식의 결제 흐름을 제공합니다.
- 구매자의 결제 완료 후 판매자에게 즉시 정산하지 않고, 구매 확정 이후 정산이 진행됩니다.

<br>

### 4. 1:1 채팅

- 상품마다 구매자·판매자 전용 채팅방이 생성됩니다.
- 거래 조율, 상품 상태 확인 등 거래 보조 수단으로 활용됩니다.

<br>

### 5. AI 큐레이션

- "빈티지 감성의 카메라 찾아줘" 같은 자연어 입력으로 경매 상품을 추천받습니다.
- OpenAI API가 취향을 분석해 카테고리·가격대·스타일 조건으로 변환하고, 추천 이유와 함께 결과를 제공합니다.

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

