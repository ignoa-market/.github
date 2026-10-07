# 애플리케이션 로깅 컨벤션

## 목차

1. [목적과 적용 범위](#1-목적과-적용-범위)
2. [현재 로깅 구성](#2-현재-로깅-구성)
3. [기록 대상과 로그 레벨](#3-기록-대상과-로그-레벨)
4. [메시지와 필드](#4-메시지와-필드)
5. [반복 작업과 장애 기록](#5-반복-작업과-장애-기록)
6. [민감정보와 접근 통제](#6-민감정보와-접근-통제)
7. [메시지 예시](#7-메시지-예시)
8. [참고 자료](#8-참고-자료)

## 1. 목적과 적용 범위

이 문서는 `ignoa-api`와 `ignoa-payment`의 애플리케이션 로그 작성 기준을 정의한다. 로그는 장애 원인과 후속 조치 대상을 찾는 수단이다. 신규 로그와 기존 로그를 수정할 때 이 기준을 적용한다.

이 문서는 **무엇을 어떤 레벨로 기록할지**를 정한다. 로그 수집 인프라의 설치 절차나 현재 코드의 모든 로그 목록을 기술하지 않는다.

## 2. 현재 로깅 구성

| 항목 | 확인된 구성 |
|---|---|
| 애플리케이션 | 두 서버 모두 기본 로그 레벨 `INFO`, 요청 로그의 MDC에 Trace ID·Span ID 출력 패턴 설정 |
| 오류 추적 | 운영 프로필에서 Sentry의 `ERROR` 이벤트 수집 설정 |
| 로그 수집·조회 | Docker 컨테이너 로그를 Alloy가 수집해 Grafana Cloud Loki로 전송하고 Grafana에서 조회 |
| 저장 위치 | Docker 원본 로그는 EC2에 저장하고, 전송된 로그는 Grafana Cloud Loki에 저장 |
| 보관 기간 | Grafana Cloud 무료 플랜의 로그 보관 기간은 14일. EC2의 Docker 원본 로그는 회전 설정 없이 누적될 수 있음 |

현재는 텍스트 로그에 검색할 값을 `key=value` 형식으로 남긴다. 필드별 검색·집계가 많아지면 JSON 구조화 로그 도입을 검토한다.

## 3. 기록 대상과 로그 레벨

다음 중 하나에 해당하는 사건을 기록한다.

- 장애나 정합성 위험 때문에 후속 조치가 필요한 결과
- 자동 복구·대체 처리 또는 재시도 적체처럼 운영 중 추이를 확인해야 하는 상황
- 대상이 있는 배치·스케줄러의 실행 결과
- 원인 분석에 필요한 개별 처리·분기. 단, 반복 빈도가 높으면 기본적으로 생략하거나 `DEBUG`로 제한

메서드 진입·종료, `처리 중` 같은 단계별 메시지와 DB에서 확인 가능한 정상 거래 결과를 관성적으로 기록하지 않는다.

| 레벨 | 사용 기준 | 예시 |
|---|---|---|
| `INFO` | 운영 중 상시 확인할 필요가 있는 실행 결과. 반복 작업은 개별 성공 대신 실행 단위로 요약 | 대상이 있는 자동 마감 실행 결과 |
| `WARN` | 복구·대체 처리가 가능하지만 운영자가 발생 사실이나 추이를 확인해야 하는 상황 | 중복을 제한한 Redis 장애 감지, 재시도 적체 |
| `ERROR` | 자동 복구가 끝내 실패했거나 정합성 위험으로 조치가 필요한 상황 | 콜백 재시도 기한 초과, 보상 Outbox 적재 실패 |
| `DEBUG` | 장애 분석에만 필요한 개별 처리와 예상된 분기 | 결제 승인 완료, 경매별 마감 완료, 중복 콜백 무시 |

로그 레벨은 HTTP 상태 코드나 도메인의 중요도만으로 정하지 않는다. **운영 대응 필요성과 발생 빈도**를 함께 고려한다. 개별 결제 승인처럼 중요한 사건도 건수가 많고 DB에서 결과를 조회할 수 있다면 `INFO`로 매번 기록하지 않는다. 예상된 비즈니스 거절과 개별 `503` 응답 역시 기본적으로 `WARN`·`ERROR`로 기록하지 않는다.

## 4. 메시지와 필드

메시지는 한국어로 **사건과 결과**를 적는다. 검색·집계할 필드명은 영어 camelCase로 쓰고, 같은 개념에는 두 서버에서 같은 이름을 사용한다. 값은 한 줄에서 구분할 수 있도록 `필드명=값` 형태로 남긴다. 예외 원문이나 사용자 입력을 필드값으로 그대로 넣지 않는다.

- 시각·레벨·서비스명은 로깅 설정으로 출력한다. 요청 로그의 Trace ID·Span ID는 제공되는 경우 MDC를 통해 함께 출력한다.
- 대상이 있는 사건에는 확인 가능한 ID를 남긴다. 경매는 `itemId`, 거래·결제는 확보된 `tradeId`·`orderId`, Outbox는 `outboxId`를 우선 사용한다. 서로 다른 값을 같은 필드명에 넣지 않는다.
- 실패에는 일정한 오류 코드 또는 `reason`을 남긴다. 재시도에는 시도 횟수와 다음 처리, 수동 조치가 필요하면 `action`을 추가한다. 외부 서비스의 예외·응답 원문을 `reason`으로 사용하지 않는다.
- 스케줄러는 처리 대상이 있을 때 대상·성공·실패 건수와 소요 시간(`target`, `success`, `failed`, `elapsedMs`)을 요약한다. 요청에서 시작하지 않은 작업에 Trace ID를 강제하지 않고 대상 ID나 실행 ID로 추적한다.

## 5. 반복 작업과 장애 기록

- 결제 서버의 승인과 메인 서버의 거래 상태 반영은 서로 다른 사건이다. 각 서버는 자신이 책임지는 결과만 기록한다.
- 스케줄러는 대상이 없을 때마다 `INFO`를 남기지 않는다. 대상이 있다면 실행 단위로 요약하고, 개별 성공은 `DEBUG`로 기록하거나 생략한다. 실패 대상은 저장 상태나 별도 기록으로 식별·재처리할 수 있어야 한다.
- 정상적인 개별 재시도는 `DEBUG`로 기록하거나 생략한다. 재시도 적체나 최종 실패처럼 운영 대응이 필요한 시점에는 `WARN`·`ERROR`를 사용한다.
- 동일한 인프라 장애가 여러 요청에 반복되면 요청마다 `WARN`·`ERROR`와 스택 트레이스를 출력하지 않는다. 장애 발생·지속은 메트릭이나 중복을 제한한 로그로 관찰한다. 기존 로그를 줄이기 전 대체 관측 수단이 실제로 있는지 확인한다.
- 같은 예외의 스택 트레이스를 여러 계층에서 반복 출력하지 않는다. 하위 계층에서 복구·대체 처리를 했다면 그 결정만 기록하고, 최종 실패는 책임지는 경계에서 기록한다.

## 6. 민감정보와 접근 통제

비밀번호, JWT·Refresh Token, API 키, 인증 코드, 결제 키, 카드·계좌 정보, 요청·응답 본문 전체는 기록하지 않는다. 이메일·전화번호는 필요한 경우에만 마스킹해 기록한다. 외부 서비스의 응답 원문 대신 내부 식별자와 안전한 오류 코드를 사용한다. 예외 객체를 전달할 때는 메시지와 스택 트레이스에 민감정보가 포함되지 않는지 확인한다.

Docker 원본 로그와 Grafana Cloud Loki 로그의 접근 권한·보관 기간은 별도로 관리한다. 현재 `ignoa-api` 컨테이너는 `json-file` 로깅 드라이버를 사용하며 로그 회전 옵션이 없어, 원본 로그가 EC2 디스크에 계속 누적될 수 있다. 운영 환경의 Docker 로그 크기를 확인하고 회전 정책을 설정한다. Grafana Cloud 로그에는 계정 권한과 사용 중인 플랜의 보관 정책을 적용한다.

## 7. 메시지 예시

아래는 규약의 예시이며 현재 코드의 로그와 일치한다는 뜻은 아니다.

```text
INFO  자동 마감 실행 결과 target=1000 success=998 failed=2 elapsedMs=6150
DEBUG 결제 승인 완료 tradeId=42 orderId=order-123
DEBUG 경매 마감 완료 itemId=17 result=낙찰
DEBUG 결제 결과 콜백 재시도 예약 callbackId=31 tradeId=42 attempts=2
WARN  Redis 장애 감지 operation=BLACKLIST_LOOKUP
ERROR 결제 결과 콜백 재시도 기한 초과 callbackId=31 tradeId=42 action=MANUAL_PAYMENT_RECONCILIATION
```

`Redis 장애 감지`는 요청마다 출력하는 예시가 아니라 장애 발생을 중복 제한해 기록하는 예시다.

## 8. 참고 자료

- [daily.dev — Logging Best Practices for Developers](https://daily.dev/blog/logging-best-practices-for-developers/)
- [OWASP Logging Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html)
- [OpenTelemetry Logging](https://opentelemetry.io/docs/specs/otel/logs/)
- [Spring Boot Logging](https://docs.spring.io/spring-boot/reference/features/logging.html)
- [Docker — JSON File logging driver](https://docs.docker.com/engine/logging/drivers/json-file/)
- [Grafana Cloud — Logs pricing and retention](https://grafana.com/docs/grafana-cloud/platform/pricing-and-usage/logs/)
