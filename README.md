# 이중원 | Backend Developer

[![Email](https://img.shields.io/badge/Email-dlwnddnjs96%40gmail.com-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:dlwnddnjs96@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-shoeone96-181717?style=flat-square&logo=github)](https://github.com/shoeone96)
[![Blog](https://img.shields.io/badge/Blog-shoenoe.tistory.com-FF5722?style=flat-square&logo=tistory&logoColor=white)](https://shoenoe.tistory.com)

## About Me

글로벌 9개 리전 B2B SaaS에서 인증·결제·크레딧 시스템을 설계하고 운영해온 백엔드 개발자입니다.

- 사용자의 편안한 경험을 최우선으로 생각해서, 파트너 연동 Open API 로그인을 **2회에서 1회로** 줄이는 서버 사이드 인증 체계를 설계했습니다.
- 안정적이고 빠른 개발을 위해 테스트 작성 체계를 통일하고 병렬 실행으로 **테스트 시간을 44% 단축**했습니다.
- AI도 적극 활용해서, Jira 진행상황을 자동 분석·공유하는 봇을 직접 기획하며 팀 전체가 빠르게 조율할 수 있도록 했습니다.

---

## Work Experience

### 이마고웍스 (Imagoworks) | Backend Developer

> 2025.01 ~ 2026.04 (1년 4개월, 인원감축으로 퇴사)

글로벌 9개 리전에서 치과 보철물을 AI로 설계하는 B2B SaaS의 플랫폼팀에서 회원/인증, 구독/결제, 크레딧 시스템, API Gateway, 파트너 연동용 Open API를 담당했습니다.

`Kotlin` `Spring` `Spring Security` `Spring Gateway MVC` `MongoDB` `Redis` `Azure Service Bus` `Datadog` `Grafana` `ArgoCD` `App Service` `EKS`

#### Open API 인증 시스템 구축

- Open API 유저를 위한 **API Key + OTT(One-Time Token)** 기반 인증 체계 도입
- 기존에 제공 중이던 세 가지 다른 인증 체계와 충돌 없이 확장에 용이한 방식으로 구현
- 파트너 앱과 자사 서비스에 각각 로그인해야 하는 UX 문제를 서버 사이드 인증 체계 전환으로 **2회 → 1회**로 개선
- 신규 인증 추가 후 기존 인증 경로에서 의도치 않은 필터가 실행되는 격리 실패 문제를 경로별 필터 분리 설계로 해결

#### JWT → Redis 세션 전환

- JWT 토큰 기반의 인증 체계를 **Spring Session** 기반의 인증 체계로 전환
- 인증 체계 전환 과정에서 기존 다중 로그인 방지 체계를 그대로 유지할 수 있게 구현
- JWT 토큰의 DB 과누적과 토큰 파싱 후 DB 재조회·검증하는 stateless 오용 문제를 세션 방식으로 전환하여 해소
- 세션 만료 후 잔존하는 인덱스 데이터가 만료된 세션을 참조하여 조회 에러가 발생하는 문제를 조회 전 인덱스 사전 정리 로직으로 해결

#### 구독 · 크레딧 설계 및 개선

- 여러 웹훅을 통해 분산 저장되며 발생하던 크레딧 데이터 누락과 불일치 문제를 결제 플랫폼(**Stripe**)을 단일 데이터 소스로 통합하여 해결
- 데이터 팀의 구독 추적 대시보드 구축을 위해 유저 액션 히스토리 데이터 설계 및 저장 체계 구현

#### 서버 아키텍처 개선

- 높은 응집성으로 인해 서버 간 통신이 빈번하고 장애가 반복되던 두 서버를 단일 서버로 통합하여 안정성 확보
- 통합 과정에서 같은 서버 내에서 외부 메시지 큐를 경유하는 불필요 구조, 설정 분산, 응답 형식 불일치 등 레거시 과제를 정리

#### 개발 인프라 개선

- Base Image 최적화와 Multi-stage Build 도입으로 Docker 이미지 **54% 경량화** (445MB → 204MB)
- 테스트 DB 격리를 통해 안전한 병렬 실행 환경을 구성하여 빌드 시간 **44% 단축**
- 테스트 병렬화 시 설정 파일의 DB 이름이 실제 사용되는 DB와 다른 근본 원인을 프레임워크 소스 추적으로 발견하여 해결

#### AI 활용 팀 생산성 개선

- 데일리 스탠드업에서 장기 체류 이슈가 반복적으로 누락되는 문제를 해결하기 위해 Jira 스프린트 현황을 **AWS Bedrock Claude**로 자동 분석하여 매일 오전 Teams로 발송하는 봇을 단독 설계·구현
- 인원별 이슈 현황, 30일+ 장기 체류 이슈 자동 플래깅, 권장 액션을 포함한 리포트를 팀 전체가 매일 활용
- 기존 1주일 이상 체류하던 이슈가 **3일 이내**로 처리

---

### 티맥스 메타에이아이 | Backend Developer

> 2024.08 ~ 2024.12 (5개월, 경영악화로 퇴사)

AI 기반 게임 서버 개발팀에서 웹 기반 제품의 백엔드를 담당했습니다.

`Java` `Spring` `Spring Security` `MySQL` `Redis`

#### 전국 12개 국립 암센터 대상 메타버스 체험 플랫폼

- 메타버스 게임 내 캐릭터 제어권을 **DB 락**으로 관리하여 동시 접속 환경에서 하나의 캐릭터를 한 명만 조작할 수 있도록 배타적 제어 보장
- 토큰 기반 인증 시스템을 구축하여 플랫폼 사용자 인증 체계 구현

---

## Side Projects

### chinguDachi (친구다치) | 솔로 프로젝트 (Backend / Frontend / 기획)

> 2026.02 ~ 진행중

한국과 일본 간 언어 장벽을 허물고, 관심사가 맞는 사람끼리 자연스럽게 소통할 수 있는 AI 번역 채팅 네트워킹 플랫폼

🌐 [Dev Site](https://dev.chingu-dachi.com) · 🏠 [소개 사이트](https://chingu-dachi.github.io/.github/) · 🐙 [GitHub Org](https://github.com/chingu-dachi)

`Kotlin` `Spring Boot` `PostgreSQL` `WebSocket STOMP` `OpenAI GPT-4.1-mini` `React` `Expo` `AWS`

- 메시지 전송 시 **2초 이내** AI 자동 번역, 번역문과 원문을 동시 표시하여 언어 학습에도 활용 가능
- **15개 관심사 태그** 기반으로 유저 카드를 탐색하고 바로 대화를 시작할 수 있는 매칭 시스템
- 사용자 언어 설정에 따라 한국어/일본어 UI를 자동 전환하는 이중 언어 인터페이스
- Google OAuth 기반 간편 로그인으로 복잡한 회원가입 없이 즉시 이용 가능

---

### 빵그리의 오븐 | 팀 17명 (BE 5명) · 300+ 유저

> 2024.01 ~ 2025.08

저당/글루텐프리 베이커리 판매처 추천 플랫폼

`Java` `Spring Boot` `Redis` `MariaDB` `QueryDSL`

- BE 팀장으로 5명의 업무 분배·코드 리뷰·MySQL 스터디 운영
- 게시판 설계·구현, 게시글 랭킹 시스템, 위시리스트 기능 담당
- 서버 메모리 초과로 다운되는 현상을 부하 테스트와 메모리 분석 도구로 원인을 특정하여 해결, 메모리 사용량 **30% 감축**
- Redis Sorted Set의 랭킹 데이터로 다시 RDB에서 필터 조건을 반영해 조회해야 하는 이중 조회 구조를 랭킹 테이블을 RDB로 이관하고 **JOIN 기반 정렬+필터링을 단일 쿼리로 통합**하여 해결
- 1:N 관계에서 fetch join + limit 사용 시 JPA가 전체 데이터를 메모리에 로드하는 문제를 **쿼리 2회 분할 전략**(ID 조회 → IN절 상세 조회)으로 해결

---

## Activity & Certifications

| 구분 | 내용 | 시기 |
|------|------|------|
| 활동 | [Spring DIY 스터디](https://github.com/shoeone96/spring-diy-1) - Spring MVC 직접 구현 | 2026.04 ~ 진행중 |
| 교육 | 프로그래머스 데브코스 5기 - 클라우드 기반 백엔드 엔지니어링 | 2023.09 ~ 2024.03 |
| 자격증 | 정보처리기사 필기 | 2024 |
| 어학 | OPIc 일본어 IH · OPIc 영어 IM3 | 2026 |
| 수상 | 캡스톤디자인 밸류업 장려상-총장상 — 헌옷 수거함 키오스크 (3인, Full Stack 개발 담당) | 2023 |
| 수상 | LG CNS DX 아이디어 공모전 입선 — 1인가구 레시피 공유 플랫폼 (3인, 기획 담당) | 2022 |

---

## Education

**동국대학교** - 사회학 전공 / 융합소프트웨어 연계전공 (학점 4.05/4.5, 우등 졸업)
