
# 🐾 Animalloo - 반려동물 편의시설 검색 서비스

**서울시 반려동물 동반 가능 시설 정보를 제공하는 지도 기반 검색 플랫폼**

## 📖 프로젝트 소개

**Animalloo**는 반려동물과 함께 갈 수 있는 서울시 내 시설 정보를 쉽게 찾을 수 있도록 도와주는 웹 서비스입니다.

### 🎯 주요 목표

- 🗺️ **지도 기반 검색**: 카카오맵 API를 활용한 직관적인 시설 위치 확인
- 🤖 **AI 기반 검색**: LLM(Gemini)을 활용한 자연어 검색
- 📱 **반응형 디자인**: 모바일/데스크톱 환경 모두 지원
- ⏰ **실시간 운영시간**: 오늘 요일 기준 운영시간 표시

***

## ✨ 주요 기능

### 1. 🔍 통합 검색 시스템

#### **지역 기반 필터링**

- 서울시 25개 구 선택
- 카테고리별 필터링 (동물병원, 약국, 카페, 공원 등)
- 실시간 마커 업데이트


#### **AI 자연어 검색**

- "강아지 데리고 갈 수 있는 카페"
- "반려견 동반 가능한 공원"
- LLM이 의도를 분석하여 적절한 카테고리 매칭


### 2. 🗺️ 인터랙티브 지도

#### **카카오맵 통합**

- 실시간 시설 위치 마커 표시
- 클러스터링을 통한 성능 최적화
- 마커 클릭 시 상세 정보 모달


#### **시설 정보 모달**

- 시설명, 카테고리, 주소
- 전화번호, 운영시간
- 오늘 요일 기준 실시간 운영 상태
- 길찾기 (카카오맵 연동)


### 3. 👤 사용자 관리

#### **JWT 기반 인증**

- 회원가입/로그인
- 비밀번호 암호화 (bcrypt)
- 토큰 기반 세션 관리


#### **마이페이지**

- 프로필 정보 관리
- 즐겨찾기 시설 관리 (예정)


### 4. 📊 데이터 관리

#### **정규화된 DB 구조**

- `facilities`: 시설 기본 정보
- `OpeningHours`: 요일별 운영시간 (7개 행)
- `HolidayInfo`: 휴일 정보
- `districts`: 서울시 구 정보

***

## 🛠 기술 스택

### **Frontend**

```
React 18.3.1
TypeScript 5.5.3
Vite 5.4.2
React Router 6.26.2
TailwindCSS 3.4.13
Lucide React (아이콘)
```


### **Backend**

```
Python 3.x
Flask 3.0.3
Flask-CORS
Flask-JWT-Extended 4.6.0
Flask-SQLAlchemy 3.1.1
Flask-Bcrypt 1.0.1
SQLite3
Google Gemini API (LLM)
```


### **외부 API**

- **카카오맵 API**: 지도 표시 및 길찾기
- **Google Gemini API**: 자연어 검색 의도 분석

***

## 📁 프로젝트 구조

```
Animalloo_Project/
├── frontend/
│   ├── src/
│   │   ├── components/       # 재사용 컴포넌트
│   │   │   ├── Header.tsx
│   │   │   ├── Footer.tsx
│   │   │   ├── HeroSection.tsx
│   │   │   ├── MapSection.tsx
│   │   │   ├── DistrictSection.tsx
│   │   │   └── FacilityModal.tsx
│   │   ├── pages/            # 페이지 컴포넌트
│   │   │   ├── HomePage.tsx
│   │   │   ├── SearchPage.tsx
│   │   │   ├── FacilityDetail.tsx
│   │   │   ├── Login.tsx
│   │   │   ├── Signup.tsx
│   │   │   └── MyPage.tsx
│   │   ├── context/          # 전역 상태
│   │   │   └── AuthContext.tsx
│   │   ├── types/            # TypeScript 타입
│   │   │   └── index.ts
│   │   ├── App.tsx
│   │   ├── router.tsx
│   │   └── main.tsx
│   ├── public/
│   ├── package.json
│   └── vite.config.ts
│
├── backend/
│   ├── app.py                # 메인 Flask 앱
│   ├── auth.py               # 인증 관련 라우트
│   ├── models.py             # SQLAlchemy 모델
│   ├── LLM_part/
│   │   └── LLM.py            # Gemini LLM 처리
│   ├── requirements.txt
│   └── .env                  # 환경 변수
│
├── animalloo_en_db.sqlite    # SQLite 데이터베이스
└── README.md
```


***

## 🚀 설치 및 실행

### **사전 요구사항**

- Node.js 18+
- Python 3.8+
- 카카오맵 API 키
- Google Gemini API 키

***

### **1. 프로젝트 클론**

```bash
git clone https://github.com/yourusername/Animalloo_Project.git
cd Animalloo_Project
```


***

### **2. 백엔드 설정**

#### **가상환경 생성 및 활성화**

```bash
cd backend
python -m venv venv

# Windows
venv\Scripts\activate

# macOS/Linux
source venv/bin/activate
```


#### **패키지 설치**

```bash
pip install -r requirements.txt
```


#### **환경 변수 설정**

`.env` 파일 생성:

```env
GEMINI_API_KEY=your_gemini_api_key_here
JWT_SECRET_KEY=your_jwt_secret_key_here
FLASK_SECRET_KEY=your_flask_secret_key_here
```


#### **백엔드 실행**

```bash
python app.py
```

서버가 `http://127.0.0.1:5001`에서 실행됩니다.

***

### **3. 프론트엔드 설정**

#### **새 터미널 열기**

```bash
cd frontend
```


#### **패키지 설치**

```bash
npm install
```


#### **환경 변수 설정**

`.env` 파일 생성:

```env
VITE_KAKAO_MAP_API_KEY=your_kakao_map_api_key_here
VITE_API_BASE_URL=http://127.0.0.1:5001
```


#### **프론트엔드 실행**

```bash
npm run dev
```

프론트엔드가 `http://localhost:3000`에서 실행됩니다.

## 🗄️ 데이터베이스 구조

### **facilities (시설 정보)**

| 컬럼명 | 타입 | 설명 |
| :-- | :-- | :-- |
| Facility_ID | INTEGER | 시설 고유 ID (PK) |
| Name | TEXT | 시설명 |
| Category | TEXT | 카테고리 |
| District | TEXT | 자치구 |
| LotAddress | TEXT | 지번 주소 |
| RoadAddress | TEXT | 도로명 주소 |
| Latitude | REAL | 위도 |
| Longitude | REAL | 경도 |
| PhoneNumber | TEXT | 전화번호 |
| Website | TEXT | 웹사이트 |
| Description | TEXT | 시설 설명 |
| ParkingAvailable | INTEGER | 주차 가능 여부 |
| PetFriendly | INTEGER | 반려동물 동반 가능 |


***

### **OpeningHours (운영시간)**

| 컬럼명 | 타입 | 설명 |
| :-- | :-- | :-- |
| Hour_ID | INTEGER | 운영시간 ID (PK) |
| Facility_ID | INTEGER | 시설 ID (FK) |
| DayOfWeek | TEXT | 요일 (Monday~Sunday) |
| Opens | TEXT | 오픈 시간 (HH:MM) |
| Closes | TEXT | 마감 시간 (HH:MM) |


***

### **HolidayInfo (휴일 정보)**

| 컬럼명 | 타입 | 설명 |
| :-- | :-- | :-- |
| Holiday_ID | INTEGER | 휴일 ID (PK) |
| Facility_ID | INTEGER | 시설 ID (FK) |
| HolidayInfo | TEXT | 휴일 정보 |


***

### **users (사용자)**

| 컬럼명 | 타입 | 설명 |
| :-- | :-- | :-- |
| id | INTEGER | 사용자 ID (PK) |
| username | VARCHAR(80) | 사용자명 (UNIQUE) |
| email | VARCHAR(120) | 이메일 (UNIQUE) |
| password_hash | VARCHAR(255) | 암호화된 비밀번호 |


***

## 🧩 주요 컴포넌트

### **MapSection.tsx**

카카오맵 API를 활용한 지도 컴포넌트

**주요 기능:**

- 시설 마커 표시
- 클러스터링
- 마커 클릭 시 모달 표시
- 지도 이동 시 중심 좌표 업데이트

***

### **FacilityModal.tsx**

시설 상세 정보 모달

**표시 정보:**

- 시설명, 카테고리
- 주소, 전화번호
- **오늘 요일 기준 운영시간**
- 휴일 정보 (있는 경우)
- 길찾기 버튼 (카카오맵 연동)
- 자세히 보기 버튼

***

### **DistrictSection.tsx**

서울시 25개 구 필터링 컴포넌트

**주요 기능:**

- 구 버튼 클릭 시 필터링
- 카테고리 다중 선택
- 실시간 마커 업데이트

***

### **HeroSection.tsx**

AI 자연어 검색 컴포넌트

**주요 기능:**

- LLM 기반 검색 의도 분석
- 현재 위치 기반 검색
- 반경 내 시설 검색

***

## 📌 개발 히스토리

### **v1.0 - 초기 개발**

- ✅ React + TypeScript 프로젝트 구조 설정
- ✅ Flask 백엔드 API 구현
- ✅ 카카오맵 API 통합
- ✅ SQLite 데이터베이스 설계


### **v1.1 - 인증 시스템**

- ✅ Supabase → Flask JWT 전환
- ✅ 회원가입/로그인/마이페이지
- ✅ bcrypt 비밀번호 암호화


### **v1.2 - 지도 기능 개선**

- ✅ 마커 클러스터링
- ✅ 시설 모달 개선
- ✅ 실시간 필터링

### **v1.4 - LLM 검색**

- ✅ Google Gemini API 통합
- ✅ 자연어 검색 의도 분석
- ✅ 위치 기반 검색

