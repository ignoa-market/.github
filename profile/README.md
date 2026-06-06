<div align="center">

# IGNOA (이그노아)

[![Java](https://img.shields.io/badge/Java-21-ED8B00?style=flat-square&logo=openjdk&logoColor=white)](https://docs.oracle.com/en/java/javase/21/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.5.7-6DB33F?style=flat-square&logo=springboot&logoColor=white)](https://spring.io/projects/spring-boot)
[![MySQL](https://img.shields.io/badge/MySQL-8.0-4479A1?style=flat-square&logo=mysql&logoColor=white)](https://www.mysql.com/)
[![Redis](https://img.shields.io/badge/Redis-7-DC382D?style=flat-square&logo=redis&logoColor=white)](https://redis.io/)
[![Docker](https://img.shields.io/badge/Docker-29.5.2-2496ED?style=flat-square&logo=docker&logoColor=white)](https://www.docker.com/)

**"실시간 경매를 통해 내 손안에서 거래하는 중고 마켓플레이스"**

> Ignoa는 사용자가 원하는 중고 상품을 경매와 즉시구매로 거래하고, 입찰 현황을 실시간으로 확인할 수 있는 경매 기반 중고거래 플랫폼입니다.

<br>

[[웹 바로가기]](https://ignoa.wisoft.dev/app) , 
[[프로젝트 노션]](https://familiar-dragon-4ed.notion.site/Ignoa-336bf88cd0f580b9ae17fc47b088208f?source=copy_link) ,
[[API 명세]](https://familiar-dragon-4ed.notion.site/API-336bf88cd0f58150b007e4fa41649d0e?source=copy_link) ,
[[데이터베이스 설계]](https://familiar-dragon-4ed.notion.site/DB-336bf88cd0f581109574fef029f86e96?source=copy_link), 
[[트러블 슈팅]](https://www.notion.so/338bf88cd0f580629722d14f99044f8e?v=338bf88cd0f580d09cdd000c48f1a301&source=copy_link)

<br>

<img width="3248" height="2122" alt="image" src="https://github.com/user-attachments/assets/08bfba67-73b9-4f8f-86c8-9806684f26ca" />

<br>
<br>

## 프로젝트 소개 (Introduction)

Ignoa는 경매를 기본 거래 방식으로 채택한 중고거래 웹 서비스입니다.  

판매자가 가격을 고정하는 기존 중고거래 구조에서 벗어나, 구매자가 직접 가격을 제안하고 시장이 적정가를 결정합니다.  

**실시간 입찰, 즉시 구매**을 통해 더 공정하고 몰입감 있는 거래 경험을 제공합니다.

<br>

### 1. 배경 (Background)

<br>

<table>
<tr>
<td width="50%" align="center" valign="middle">
<h3>📈 중고거래 시장 규모</h3>
<p>국내 중고거래 시장 규모 <b>연 30조 원</b>, 2030년 <b>43조 원</b> 돌파 전망</p>
</td>
<td width="50%" align="center" valign="middle">
<h3>😤 가격 책정의 어려움</h3>
<p>판매자의 <b>주관적 가격 설정</b>으로 구매자·판매자 모두 불만족</p>
</td>
</tr>
</table>

<br>

### 2. 기존 중고거래의 문제 (Problem)

<br>

>  🛒 **구매자** → *"더 좋은 가격에 살 수 있었는데, 얼마가 적당한지 모르겠다."*  
> 
> 🛍 **판매자** → *"얼마에 올려야 할지 모르겠고, 가격 흥정이 피곤하다."*  
>
> 🤝 **거래 전반** → *"묻고 기다리는 구조라 거래 진행이 느리고 답답하다."*

<br>

### 3. 솔루션 (Solution)

**IGNOA**는 경매를 기본 거래 방식으로 채택해 세 가지 문제를 해결합니다.

<br>

| 해결 | 방법 |
|------|------|
| 1. 가격 고민 제거 | 구매자가 직접 가격을 제안 → 시장이 적정가를 결정 |
| 2. 흥정 피로 제거 | 입찰 경쟁 구조로 자연스러운 가격 수렴 |
| 3. 거래 몰입도 향상 | 실시간 입찰 + 즉시 구매로 모든 사용자 수용 |

<br>
<br>
<br>

</div>

