<h1>🏋️‍♂️ FitAgent: OpenAI Function Calling 기반 AI 퍼스널 트레이너</h1>
FitAgent는 OpenAI의 Function Calling 기술을 활용하여 사용자의 식단과 운동 기록을 실시간으로 분석하고, 외부 API 데이터를 바탕으로 최적의 피드백과 맞춤형 식단을 제공하는 지능형 에이전트 시스템입니다.

🚀 프로젝트 개요
주제: OpenAI API의 Function Calling을 활용한 외부 도구 연동 AI 에이전트 구축

핵심 기술: OpenAI API (GPT-4.1-mini), FastAPI, Function Calling, 외부 API 연동 (FatSecret, Wger), Chart.js 대시보드

주요 특징: 실시간 데이터 시각화, 멀티턴 대화 맥락 유지, 3중 안전장치(Guardrails) 적용

✨ 주요 기능 및 구현 사항 (루브릭 준수)
1. 핵심 요구사항 (필수)
A. Function Calling 구현:

get_nutrition_data: 사용자가 입력한 음식의 영양 성분을 검색합니다.

analyze_workout_impact: 수행한 운동 명칭을 분석하여 타겟 근육 부위를 파악합니다.

Developer-in-the-Loop: AI의 함수 호출 추천 → 백엔드 실행 → 결과 피드백 → 최종 응답 생성 프로세스를 완벽히 준수합니다.

B. 외부 데이터 소스 연동:

FatSecret API: OAuth 2.0 인증을 통해 실제 음식 영양 데이터베이스와 연동합니다.

Wger API: 오픈소스 운동 데이터베이스를 호출하여 근육 자극 데이터를 가져옵니다.

C. 안전장치 (Guardrails) 구현:

입력 검증: 500자 이상의 비정상적 입력 및 단문 입력 방어 로직을 적용했습니다.

프롬프트 주입 방어: 시스템 페르소나 변경 시도 및 도메인 이탈 질문을 원천 차단합니다.

출력 안전성: 건강을 해칠 수 있는 극단적인 식단 요구 시 거절 후 대안을 제시하도록 설계되었습니다.

2. 확장 기능
병렬 함수 호출 (Parallel Function Calling): 식단과 운동을 동시에 입력 시 여러 도구를 한 번에 호출하여 처리합니다.

대화 기록 관리 (Multi-turn): 대화 내역(Context)을 유지하여 이전 대화 내용에 기반한 추가 질문 처리가 가능합니다.

비정형 데이터 구조화: 자연어 텍스트를 분석하여 차트 렌더링을 위한 JSON 태그 데이터로 자동 변환합니다.

웹 UI 구현: Chart.js 기반의 실시간 대시보드(영양소 도넛 차트, 운동 레이더 차트, 추천 식단 상세 테이블)를 제공합니다.

에러 핸들링: API 장애 시 AI의 자체 지식을 활용한 '추정 분석(Fallback)' 로직으로 시스템 가용성을 확보했습니다.

🛠 기술 스택
Backend: Python, FastAPI, OpenAI SDK, Requests, Uvicorn

Frontend: HTML5, CSS3 (Flexbox/Grid), Vanilla JavaScript, Chart.js, FontAwesome

AI Model: gpt-4.1-mini

⚙️ 실행 방법
1. 환경 변수 설정
프로젝트 루트에 .env 파일을 생성하고 아래 키를 입력합니다.

코드 스니펫
OPENAI_API_KEY=your_openai_api_key
FATSECRET_CLIENT_ID=your_fatsecret_client_id
FATSECRET_CLIENT_SECRET=your_fatsecret_client_secret
2. 라이브러리 설치
Bash
pip install fastapi uvicorn openai requests python-dotenv
3. 서버 실행
Bash
python main.py
4. 접속
브라우저에서 index.html 파일을 열거나 로컬 서버를 통해 접속합니다.

📁 프로젝트 구조
main.py: FastAPI 서버 및 에이전트 로직 (Function Calling 처리)

index.html: 대시보드 UI 및 채팅 인터페이스

.env: API 키 및 인증 정보 관리
