# 🏋️‍♂️ FitAgent  
## OpenAI Function Calling 기반 AI 퍼스널 트레이너

FitAgent는 **OpenAI Function Calling** 기술을 활용하여  
사용자의 **식단 및 운동 데이터를 실시간 분석**하고,  
외부 API 정보를 기반으로 **맞춤형 건강 피드백과 식단 추천**을 제공하는  
지능형 AI 에이전트 시스템입니다.

---

## 🚀 프로젝트 개요

| 항목 | 내용 |
|---|---|
| **프로젝트 주제** | OpenAI API Function Calling 기반 외부 도구 연동 AI Agent |
| **AI 모델** | GPT-4.1-mini |
| **Backend** | Python, FastAPI |
| **Frontend** | HTML5, CSS3, JavaScript |
| **핵심 기술** | Function Calling, Multi-turn Context, Guardrails |
| **외부 API** | FatSecret, Wger |
| **시각화** | Chart.js Dashboard |

---

## ✨ 주요 기능 및 구현 사항 (루브릭 기준)

---

## ✅ 1. 핵심 요구사항

### A. Function Calling 구현

FitAgent는 OpenAI Function Calling 구조를 기반으로 다음 도구들을 호출합니다.

#### 🔹 `get_nutrition_data`
- 사용자가 입력한 음식의 영양 성분 조회
- 칼로리 / 탄수화물 / 단백질 / 지방 분석

#### 🔹 `analyze_workout_impact`
- 운동 이름 분석
- 타겟 근육 부위 식별
- 운동 효과 평가

#### 🔹 Developer-in-the-Loop 프로세스

AI 에이전트 실행 흐름:

User Input
↓
LLM Function Call Recommendation
↓
Backend Function Execution
↓
External API Response
↓
LLM Final Response Generation


AI가 직접 실행하지 않고  
**개발자가 항상 실행 루프에 개입하는 구조**를 준수합니다.

---

### B. 외부 데이터 소스 연동

#### 🥗 FatSecret API
- OAuth 2.0 인증 사용
- 실제 음식 영양 데이터 활용
- 신뢰성 높은 식단 분석 제공

#### 🏋️ Wger API
- 오픈소스 운동 데이터베이스
- 운동별 자극 근육 정보 조회
- 운동 영향 분석 지원

---

### C. 안전장치 (Guardrails)

#### ✔ 입력 검증
- 500자 이상 비정상 입력 차단
- 의미 없는 단문 입력 방어

#### ✔ 프롬프트 주입 방어
- 시스템 페르소나 변경 시도 차단
- 도메인 외 질문 제한

#### ✔ 출력 안전성
- 극단적 다이어트/위험한 건강 요청 거절
- 안전한 대안 제시

---

## ⭐ 2. 확장 기능

### ⚡ 병렬 함수 호출 (Parallel Function Calling)
식단 + 운동 입력 시:

- 여러 Function을 **동시에 호출**
- 응답 속도 개선
- 분석 정확도 향상

---

### 🧠 Multi-turn 대화 맥락 유지
- 이전 대화 Context 저장
- 연속적인 코칭 가능
- 개인화된 트레이닝 경험 제공

---

### 🧩 비정형 데이터 구조화
자연어 입력 → AI 분석 → JSON 구조 변환 → Chart Rendering


차트 시각화를 위한 데이터 자동 생성.

---

### 📊 실시간 웹 대시보드

Chart.js 기반 UI 제공:

- 영양소 도넛 차트
- 운동 레이더 차트
- 추천 식단 테이블
- 실시간 피드백 표시

---

### 🛡 에러 핸들링 (Fallback Strategy)

외부 API 장애 발생 시:

- AI 내부 지식 기반 **추정 분석(Fallback)**
- 서비스 중단 없는 안정적 운영

---

## 🛠 기술 스택

### Backend
- Python
- FastAPI
- OpenAI SDK
- Requests
- Uvicorn
- python-dotenv

### Frontend
- HTML5
- CSS3 (Flexbox / Grid)
- Vanilla JavaScript
- Chart.js
- FontAwesome

### AI
- OpenAI GPT-4.1-mini
- Function Calling Agent Architecture

---

## ⚙️ 실행 방법

---

### 1️⃣ 환경 변수 설정

프로젝트 루트에 `.env` 파일 생성:

```env
OPENAI_API_KEY=your_openai_api_key
FATSECRET_CLIENT_ID=your_fatsecret_client_id
FATSECRET_CLIENT_SECRET=your_fatsecret_client_secret
