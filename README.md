# JAEHAN JANG

**Backend & Full-Stack Developer**  
서비스의 구조와 흐름을 이해하고,  
**단순 구현을 넘어 실제 운영 가능한 웹 서비스를 설계하고 개발하는 것**을 지향합니다.

Java/Spring Boot와 Spring Legacy, Node.js 기반 백엔드부터  
React · Vue 프론트엔드, 실시간 통신과 성능 측정, 그리고 AI 프로젝트까지 직접 구현해왔습니다.

---

## 🛠 Tech Stack

### Backend
- Java
- Spring Boot / JPA
- Spring Framework (Legacy) / MyBatis
- SSE (SseEmitter) / Spring Event
- WebSocket / STOMP
- Node.js
- Express
- JSON Server

### Frontend
- React
- Vite
- Vue 3 / Pinia
- JavaScript
- HTML/CSS
- Tailwind CSS

### Database
- MySQL
- Redis

### DevOps / Infra
- Nginx
- Docker / Docker Compose
- AWS EC2
- GitHub Actions
- PM2
- Railway
- Vercel

### Testing / Performance
- k6
- JUnit
- JaCoCo
- Swagger (Springfox)

### AI / Data
- Python
- TensorFlow
- U-Net
- BERT

### Tools
- Git
- GitHub
- VS Code
- Figma

---

## 📂 Projects

### ⚖️ 탕탕 · 지갑재판소 (TangTang)
> 고정지출을 자동으로 탐지하고, 절약 시뮬레이션과 챌린지로 행동을 유도한 뒤, 월간 리포트로 실제 절감액까지 검증하는 자산관리 서비스

- KB IT's Your Life 7기 종합실무 프로젝트 · **6인 팀 팀장** · 7주
- Spring Framework 5.3(Legacy) + MyBatis 기반 모듈러 모놀리스, **API 54개 · 테이블 34개 · 라인 커버리지 84.0%**
- **실시간 알림 계층 설계·구현**: Spring Event 발행/구독 + SSE 푸시 + DLQ 재시도 배치
  - 초기 설계의 Kafka를 걷어내면서, 브로커가 해주던 **재처리 보장을 DLQ 테이블과 60초 재시도 배치로 직접 구현**
  - 실제로 이 DLQ가 알림 문구 렌더 결함을 붙잡아냈고, 회귀 테스트를 추가해 재발을 막음
- **그룹 재판 채팅 구현**: STOMP over WebSocket + Redis
  - 번호 발급(`INCR`)과 저장(`RPUSH`)이 따로 나가 발생하던 **메시지 순서 역전을 Lua 스크립트 원자화로 해결** (실 Redis 60건 동시 전송 검증)
- **전 업권 금융기관 연동**: 은행 · 카드 · 대출 · 페이머니, 20분 주기 자동 동기화
  - 호출 한도와 시연 리스크를 고려해 **CODEF 응답 규격과 동일한 목 서버를 자체 구축**
- **k6 부하테스트로 성능을 숫자로 검증**
  - 배포 환경(EC2 2 vCPU) 기준 **70 VU까지 효율 95% 선형 · 120 VU 무릎 · 140 VU까지 요청 실패 0%**
  - 응답시간의 97.7%가 서버 처리 시간임을 확인하고, **병목을 MySQL CPU로 특정**
  - 커넥션풀 개선안은 실험 후 기준 미달로 **근거를 남기고 기각** (튜닝이 아니라 "재보고 유지")
- 팀장으로 기술·기능 결정 **198건을 기록**하고, 되돌린 결정도 삭제하지 않음

🔗 **Repository & Demo**  
https://github.com/KB-TangTang/Monorepo

**Deploy**  
https://monorepo-three-ruby-81.vercel.app

---

### 🏢 WellBridge Homepage
> 실무 환경에서 진행한 기업 홈페이지 및 관리자 시스템 개발

- React + Spring Boot 기반 서비스 개발
- 관리자 인증, 파일 업로드, 콘텐츠 관리 기능 구현
- 실제 운영을 고려한 유지보수 구조와 개발 흐름 경험
- 실무 환경에서 서비스 구조를 설계하고 반영한 프로젝트
- 회사 코드 비공개

🔗 **Repository & Demo**  
https://github.com/JAEHAN-JANG/wellbridge-homepage

---

### 💸 Lucky Bank & Unlucky Bank
> 소비 기록을 넘어 피드백을 통해 소비 습관 변화를 유도하는 가계부 웹 앱

- 수입 / 지출 기록 및 캘린더 기반 거래 내역 관리 기능 구현
- **Lucky / Unlucky 모드**를 통한 차별화된 소비 피드백 UX 설계
- 기간별 필터링, 빠른 거래 등록, 소비 통계 시각화 기능 구현
- Vue, Tailwind CSS, Chart.js 기반 프론트엔드 개발
- JSON Server + Railway 기반 백엔드 및 배포 구조 경험
- 팀 프로젝트에서 **메인 페이지 달력 기능 및 JSON Server 배포 담당**

🔗 **Repository & Demo**  
Main Repository: https://github.com/kb7-blackpink/Blackpink_AccountBook  
Deploy Repository: https://github.com/kb7-blackpink/Blackpink_AccountBook_json-server

**Deploy**
https://blackpink-account-book.vercel.app/

---

### 🌱 Carbon Neutral Platform (P-Project)
> 탄소 배출량 계산 및 중립화 지원 웹 서비스

- 사용자 입력 기반 탄소 배출량 계산 로직 구현
- 월별 · 평균 · 전월 대비 데이터 비교 및 시각화
- OpenWeather API, OpenAI API 연동
- 외부 API 실패 시 초과 배출량 기반 **사전 정의 가이드로 전환하는 폴백 로직** 구성
- 팀 프로젝트에서 **프론트엔드 · 백엔드 · DB 설계 전반 담당**
- 서비스 기획부터 기능 구현까지 폭넓게 참여한 프로젝트

🔗 **Repository & Demo**  
https://github.com/JAEHAN-JANG/p-carbon-neutral

---

### 🐶🐱 멍냥케어 (졸업 프로젝트)
> 반려동물 피부 질환 예측 및 케어 지원 AI 서비스

- AI Hub 대용량 이미지 데이터 기반 피부 질환 분류
- CNN / U-Net 모델 학습 및 성능 개선
- 예측 모델을 실제 서비스 기능으로 연동
- **데이터 수집 → 모델 학습 → 서비스 적용 전 과정 경험**
- AI 모델을 실제 사용자 서비스와 연결한 프로젝트

🔗 **Repository & Demo**  
https://github.com/JAEHAN-JANG/MeongNyang-Care

---

### 🛒 GCShop (가천샵)
> 대학 수업 프로젝트로 제작한 쇼핑몰 웹 서비스

- 상품 조회, 회원 관리, 장바구니, 구매 기능 구현
- 웹과 데이터베이스 연동 구조 이해
- MVC 기반 서버 로직 설계 경험
- 웹 서비스의 기본적인 백엔드 구조를 학습하고 구현한 프로젝트

🔗 **Repository & Demo**  
https://github.com/JAEHAN-JANG/gcshop

---

### ⚔️ Quiz Battle
> Socket.io 기반 실시간 1대1 퀴즈 배틀 웹 서비스

- Node.js(server) + Vanilla JavaScript 기반 서비스 개발
- socket.io를 활용한 **Room 번호 기반 실시간 1 vs 1 대전 기능 구현**
- JSON 기반 문제 데이터(정적 DB)를 활용해 서버에서 랜덤 문제 출제
- 실시간 이벤트 처리, 대기 / 입장 / 대결 흐름 설계 경험
- 사용자 간 상호작용이 중요한 실시간 웹 서비스 구현 경험

🔗 **Repository & Demo**  
https://github.com/JAEHAN-JANG/Quiz-Battle

---

### 🤖 Habit Check / Codex AI MCP

> Codex Agent와 함께 개발 흐름을 설계하고 검증한 AI Pair Programming 실험 프로젝트

* 하루 단위 습관을 기록하고 관리하는 Habit Check 웹 앱 개발
* Vanilla JavaScript 기반으로 습관 추가 / 수정 / 삭제 / 완료 처리 기능 구현
* 날짜별 습관 기록을 `localStorage`에 저장하고 조회하는 구조 설계
* Codex Agent와 협업하기 위한 `AGENTS.md`, Issue, PR, 리뷰 흐름 정리
* Core Test / Smoke Test를 통해 핵심 로직과 앱 실행 흐름 검증
* GitHub Actions 기반 테스트 자동화 및 Docker Build 검증 환경 구성
* 단순 앱 구현을 넘어 **AI와 협업 가능한 개발 프로세스와 검증 루프를 설계한 프로젝트**

🔗 **Repository & Demo**
https://github.com/JAEHAN-JANG/codex-ai-mcp

---

## 🏆 Highlights

* **6인 팀 팀장으로 KB IT's Your Life 종합실무 프로젝트(탕탕) 수행** · 실시간 알림·채팅 인프라와 전 업권 금융기관 연동 담당
* **브로커 없이 알림 전달을 보장하는 구조 설계** · Kafka를 걷어내고 DLQ 테이블과 재시도 배치를 직접 구현
* **k6 부하테스트로 병목을 MySQL CPU로 특정**, 개선안은 실험 후 근거를 남기고 기각
* Redis Lua 스크립트로 채팅 메시지 순서 역전(동시성 경합) 해결
* 실무 기업 홈페이지 및 관리자 시스템 개발 경험
* AI 기반 졸업 프로젝트 수행 (약 1.3TB 데이터)
* 탄소 중립화 플랫폼 프로젝트 수행 (교내 1등)
* 가계부 웹 앱 팀 프로젝트에서 캘린더 기능 및 배포 담당
* WebSocket 기반 실시간 1대1 퀴즈 배틀 서비스 구현
* Codex Agent와 함께 Habit Check 앱을 개발하며 AI Pair Programming, 테스트 자동화, CI/CD 검증 흐름 경험
* 백엔드 · 프론트엔드 · 실시간 통신 · 성능 측정 · AI 협업 개발을 모두 경험한 개발자

---

## 📌 Contact
- GitHub: https://github.com/JAEHAN-JANG
- Email: twinsjh01@naver.com
