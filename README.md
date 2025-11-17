# Mental Care AI - System Level AGENTS.md

## 1. System Summary
Mental Care AI는 사용자의 정서 상태를 실시간 수집·분석하고 맞춤형 힐링 플랜 및 전문가 상담을 제공하는 AI 기반 멘탈케어 플랫폼입니다.

## 2. AGENTS.md List
| Docs | Path | Responsibility | I/O Summary |
|------|------|----------------|------------|
| frontend/GEMINI.md | /frontend | UI, 입력 검증, 시각화 | In: user input, Out: API requests |
| backend/GEMINI.md | /backend | API, orchestration, persistence | In: HTTP/WS requests, Out: DB writes, events |
| core/domain/conversation/GEMINI.md | /core/domain/conversation | 대화 도메인 모델 | In: messages, Out: Conversation objects, events |
| core/domain/emotion/GEMINI.md | /core/domain/emotion | 감정 라벨링/정규화 | In: LLM/model outputs, Out: standardized labels/scores |
| core/domain/risk/GEMINI.md | /core/domain/risk | 위기 탐지 및 경보 | In: aggregated signals, Out: risk events |
| services/llm/GEMINI.md | /services/llm | LLM provider adapter | In: prompts, Out: raw LLM responses |
| services/recommendation/GEMINI.md | /services/recommendation | 추천 엔진 | In: user history, Out: personalized plans |
| infra/db/GEMINI.md | /infra/db | DB 스키마, 마이그레이션, 백업 | In: schema changes, Out: DB artifacts |

## 3. Architecture Overview
- User → frontend → backend → LLM → domain/emotion → domain/risk → recommendation → frontend
- DB는 backend 및 domain 모듈과 연동
- 이벤트: 위험 경보, 상담 연결

## 4. SDLC & Prototype Review
- 실시간 감정 분석, 위기 탐지, 개인화 추천 요구사항
- 임계값 하드코딩, 계약 문서화 미흡, LLM 포맷 취약
- 리팩터링 필요: 포트·어댑터 문서화, config 외부화, 이벤트 기반 아키텍처

## 5. Next Iteration Recommendations
- 기능: Clinician-in-loop, 추천 평가 루프, 자동 리포트 워크플로우
- 구조: LLM 전략 패턴, 메시지 큐 도입, 공통 데이터 모델 정의
- 테스트: Contract tests, E2E 위험경보 검증, 부하 테스트
- 
# Mental Care AI 프로젝트 지침

## 목적
- 사용자의 정서 건강 관리
- 개인 맞춤형 힐링 플랜 제공
- 전문가 상담 접근성 향상

## 핵심 전략
1. **AI 공감 대화**
   - 감정 기록 기반 실시간 공감
   - 위기 탐지 시 긴급 알림
2. **맞춤형 추천**
   - 감정 패턴과 자가진단 기반 맞춤 콘텐츠
   - 주간/월간 감정 트렌드 제공
3. **전문가 연결**
   - 자동 예약/긴급 연결 기능
   - 기관용 복지 대시보드 제공
4. **데이터 기반 개선**
   - KPI 모니터링: DAU, 잔존율, 상담 연결율
   - 사용자 피드백 기반 추천 알고리즘 고도화

## 기술 가이드
- **플랫폼**: iOS, Android, Web
- **백엔드**: Python (FastAPI), Firebase, PostgreSQL
- **AI 모델**: KoBERT, GPT 기반 감정 분류
- **보안**: AES-256, SSL/TLS
- **클라우드**: Google Cloud / AWS

## 프로젝트 단계
1. MVP 개발 (2025 Q4): 데일리 체크, AI 대화
2. 정식 출시 (2026 Q1): 맞춤형 플랜, 리포트
3. 전문가 네트워크 확대 (2026 Q2~Q3)
4. 생체 데이터 기반 감정 예측 및 AR/VR 힐링 (2026 Q4~)

## 운영 지침
- 감정 색상 기반 UI/UX
- SNS 공감 챌린지 마케팅
- 상담사 자문 데이터셋 구축
- 데이터 기반 추천 알고리즘 지속 개선
