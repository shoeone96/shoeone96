# 이중원 | Backend Developer

[![Email](https://img.shields.io/badge/Email-dlwnddnjs96%40gmail.com-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:dlwnddnjs96@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-shoeone96-181717?style=flat-square&logo=github)](https://github.com/shoeone96)
[![Blog](https://img.shields.io/badge/Blog-shoenoe.tistory.com-FF5722?style=flat-square&logo=tistory&logoColor=white)](https://shoenoe.tistory.com)

## About Me

글로벌 9개 리전 B2B SaaS에서 인증·결제·크레딧 시스템을 설계하고 운영해온 백엔드 개발자입니다.

- 사용자의 편안한 경험을 최우선으로 생각해서, 파트너 연동 Open API 로그인을 **2회에서 1회로** 줄이는 서버 사이드 인증 체계를 설계했습니다.
- 안정적이고 빠른 개발을 위해 테스트를 쉽게 작성할 수 있어야 한다고 생각해서, 작성 체계를 통일하고 병렬 실행으로 **테스트 시간을 44% 단축**하면서 **1,453개 테스트 성공률 100%** 를 유지하고 있습니다.
- AI도 적극 활용해서, Jira 진행상황을 자동 분석·공유하는 봇을 직접 기획하며 팀 전체가 빠르게 조율할 수 있도록 하고 있습니다.

---

## Work Experience

### 이마고웍스 (Imagoworks) | Backend Developer

> 2025.01 ~ 재직 중 (1년 2개월)

글로벌 9개 리전에서 치과 보철물을 AI로 설계하는 B2B SaaS의 플랫폼팀에서 회원/인증, 구독/결제, 크레딧 시스템, API Gateway, 파트너 연동용 Open API를 담당했습니다.

`Kotlin` `Spring` `Spring Security` `Spring Gateway MVC` `MongoDB` `Redis` `Azure Service Bus` `Datadog` `Grafana` `ArgoCD` `App Service` `EKS`

#### 인증 체계 설계 및 개선

> 파트너 인증 체계 구축과 JWT 기반 인증의 성능·구조적 한계 개선

- **Open API 인증 시스템 구축**
  - 기존 3가지 인증 체계와 독립적으로 공존하도록 다중 SecurityFilterChain을 설계하고, API Key + Redis OTT(One-Time Token)으로 서버 사이드 인증을 구현하여 사용자 로그인을 **2회에서 1회로** 단순화
- **JWT Token 캐싱**
  - 세션 전환 전 DB 부하를 즉시 완화하기 위해 API Gateway와 Account Server 양쪽에 **Caffeine 캐시 레이어**를 적용하여 인증 서버 DB 호출을 감소
- **JWT → Redis 세션 인증 전환**
  - 세션을 우선하되 JWT fallback을 유지하는 점진 전환을 설계하고, **accountId + clientId 복합 키**로 클라이언트 유형별 세션을 구분하여 브라우저와 Electron 앱은 독립 세션을 유지하면서 동일 클라이언트의 중복 로그인을 차단하는 **다중 로그인 방지**를 구현

#### 구독 · 크레딧 설계 및 개선

> 결제 데이터 정합성 확보와 이력 시스템 구축

- **크레딧 데이터 정합성**
  - Stripe를 SSOT(Single Source of Truth)으로 전환하는 방향을 설계하고, V2 API 7개를 기존과 **병렬 운영**하며 정합성을 검증하는 점진 전환 전략으로 무중단 마이그레이션을 완료. Export 한도도 Stripe metadata 기반으로 이관하여 SSOT를 확대
- **구독 이력 시스템 설계**
  - 이벤트 타입별로 상이한 필드를 **단일 컬렉션**에 수용하고, 트리거·사용자·구독 정보를 도큐먼트에 내장하여 **JOIN 없이 단일 Read**로 완결되는 append-only 이력 스키마를 설계. 데이터팀과 협업하여 이탈 예측 모델링 자료로 활용

#### 서버 아키텍처 개선

> 강결합된 서버 통합 과정에서 불필요한 복잡도를 제거

- **마이크로서비스 통합**
  - 24개 Internal API + 7종 Azure ServiceBus로 강결합되어 timeout이 반복되던 두 서버를, 복잡도를 늘려 해결하기보다 **근본 원인인 서버 분리 자체를 제거**하는 방향으로 단일 서버에 통합하여 응답 속도와 안정성을 개선하고, Spring Context를 **3개 이상에서 2개로 축소**, 응답 표준화로 코드 일관성을 확보

#### 개발 인프라 개선

- **테스트 병렬 실행 최적화**
  - 프레임워크 소스를 추적하여 `database-name` 속성이 실제 DB명을 결정한다는 점을 파악하고, 9개 MongoDB + Redis 모두에 UUID suffix로 fork별 DB를 격리하여 병렬화. **1,453개 0 failures**, 테스트 시간 **44% 단축** (3m49s → 2m08s)
- **Docker 이미지 54% 경량화**
  - Jlink 커스텀 런타임과 JRE 이미지를 비교 검토하여, 필수 패키지를 기본 포함하는 **JRE 기반 Multi-stage 빌드**를 선택하고 레거시 스크립트를 정리하여 **445MB → 204MB** (54% 경량화)

#### AI 활용 팀 생산성 개선

- **Jira 스프린트 리뷰 자동화 봇**
  - Jira REST API로 진행 중 이슈를 수집하고 영업일 기준 경과 시간을 자동 계산한 뒤, **AWS Bedrock Claude**로 인원별 MECE 분석과 30일 이상 장기 체류 이슈 플래깅 및 권장 액션을 생성하여 **Teams Adaptive Card로 매일 오전 자동 발송**하는 봇을 직접 기획·설계·운영. Lambda + EventBridge 서버리스로 운영

---

### 티맥스 메타에이아이 | Backend Developer

> 2024.08 ~ 2024.12 (5개월)

AI 기반 게임 서버 개발팀에서 웹 기반 제품의 백엔드를 담당했습니다.

`Java` `Spring` `Spring Security` `MySQL` `Redis`

#### 전국 12개 국립 암센터 대상 메타버스 체험 플랫폼

- 60명 규모에서 Redis 분산락은 인프라 복잡도가 이점 대비 과하다고 판단하여, DB 레벨 **비관적 락**(SELECT FOR UPDATE)을 선택. 동시 요청 시 **정합성 100%**를 보장하면서 단일 DB로 운영 복잡도를 최소화

---

## Activity & Certifications

| 구분 | 내용 | 시기 |
|------|------|------|
| 교육 | 프로그래머스 데브코스 5기 - 클라우드 기반 백엔드 엔지니어링 | 2023.09 ~ 2024.03 |
| 자격증 | 정보처리기사 필기 | 2024 |
| 어학 | OPIC IH | 2024 |
| 수상 | 캡스톤디자인 밸류업 장려상-총장상 — 헌옷 수거함 키오스크 기획·개발 (3인, 서버·화면 개발 담당) | 2023 |
| 수상 | LG CNS DX 아이디어 공모전 입선 — 1인가구 레시피 공유 플랫폼 기획 (3인) | 2022 |

---

## Education

**동국대학교** - 사회학 전공 / 융합소프트웨어 연계전공 (학점 4.05/4.5, 우등 졸업)
