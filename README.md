# esp32-temperature-dashboard
# ESP32 Temperature Dashboard

IoT 기반 온도 측정 시스템입니다.  
ESP32 센서에서 측정한 온도 데이터를 FastAPI 서버로 전송하고,  
MCP 서버에서 통계/이상 감지를 수행한 후, Streamlit 대시보드에서 시각화합니다.

---

## 📐 시스템 구성

- **ESP32**: 온도 측정 및 백엔드로 데이터 전송 (HTTP POST)
- **FastAPI**: 데이터 수신 및 DB 저장, MCP 연동
- **MCP 서버**: 온도 데이터 분석 및 이상 감지 처리
- **Streamlit**: 웹 대시보드 (온도 그래프, 통계, 이상 탐지 등)
- **DB**: SQLite (개발용), MySQL (배포용)

---

## 📁 디렉토리 구조

```
esp32-temperature-dashboard/
├── backend/           # FastAPI 백엔드
│   └── app/
├── mcp/               # MCP 서버 (데이터 처리)
├── dashboard/         # Streamlit 대시보드
├── shared/            # 공통 설정, 상수
├── test_data/         # 테스트용 JSON 데이터
└── README.md
```

---

## 🚀 실행 방법

### 1. FastAPI 서버 실행

```bash
cd backend
uvicorn app.main:app --reload
```

### 2. MCP 서버 실행

```bash
cd mcp
python app.py
```

### 3. Streamlit 실행

```bash
cd dashboard
streamlit run app.py
```

---

## 📦 의존성 설치

각 디렉토리마다 `requirements.txt` 있음:

```bash
cd backend
pip install -r requirements.txt

cd ../mcp
pip install -r requirements.txt

cd ../dashboard
pip install -r requirements.txt
```

---

## 🧪 테스트용 데이터 입력

```bash
curl -X POST http://localhost:8000/temperature \
  -H "Content-Type: application/json" \
  -d '{"device_id": "ESP32-001", "temperature": 28.4, "recorded_at": "2025-07-09T14:00:00"}'
```

---

## ✨ 주요 기능

- 현재 온도 실시간 표시
- 날짜별/시간대별 온도 추이 그래프
- 이상 탐지 (급격한 온도 상승 등)
- 통계 요약 (평균/최대/최소/표준편차)

---

## 🛠 TODO

- [ ] ESP32 실제 펌웨어 연동
- [ ] MCP 서버에 이상 탐지 알고리즘 고도화
- [ ] Streamlit UI 개선

---

## 📃 라이선스

MIT License
