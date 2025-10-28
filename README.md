# 🏡 안전한 부동산 거래 정보 도우미 (Frontend)

> Vue 3 + Vite + Tailwind 기반의 부동산 직거래 서비스 프론트엔드
> **실시간 알림 · 리뷰 · 지도 기반 매물 탐색** 지원

---

## 📘 프로젝트 개요

**“안전한 부동산 거래 도우미”**는 부동산 직거래 시장의 **정보 비대칭 문제**를 해결하기 위해
AI 기반 등기부 리포트, 실거주자 리뷰, 실시간 채팅·알림 기능을 제공하는 **신뢰 중심 부동산 서비스**입니다.

본 저장소는 해당 서비스의 **프론트엔드 클라이언트**로,
`Vue 3`, `Pinia`, `TailwindCSS`, `Axios`를 기반으로 제작되었습니다.

> 🔗 백엔드 저장소: [zangbu_back_individual](https://github.com/kgm7642/zangbu_back_individual)

---

## ⚙️ Tech Stack

| 구분                   | 기술                                   |
| -------------------- | ------------------------------------ |
| **Framework**        | Vue 3 (Composition API)              |
| **Build Tool**       | Vite                                 |
| **State Management** | Pinia                                |
| **Style**            | Tailwind CSS 3.x                     |
| **Network**          | Axios                                |
| **UI/Chart**         | Chart.js, Font Awesome               |
| **Push**             | Firebase Cloud Messaging (FCM)       |
| **Deploy**           | Vercel / NCP Object Storage (정적 호스팅) |

---

## 🧩 주요 기능

| 기능                    | 설명                           |
| --------------------- | ---------------------------- |
| 🗺 **지도 기반 매물 탐색**    | Kakao Map API 기반 필터링 / 시각화   |
| 💬 **실시간 채팅**         | STOMP WebSocket 연결 및 메시지 송수신 |
| 🔔 **실시간 알림 (FCM)**   | FCM을 이용한 브라우저 푸시 알림          |
| 🧾 **AI 등기부 리포트 뷰어**  | 백엔드 분석 결과를 시각화하여 표시          |
| 🧍 **사용자 인증 / 마이페이지** | 회원가입, 로그인, 정보 수정, 탈퇴         |
| 💳 **결제 페이지**         | Toss Payments 연동 결제 UI       |
| 💬 **리뷰 작성 및 표시**     | 실거주자 인증 후 리뷰 작성 / 열람         |

---

## 📁 프로젝트 구조

```
src/
├─ api/                 # Axios 기반 API 관리
├─ assets/              # 정적 리소스 (이미지, 아이콘 등)
├─ components/
│  ├─ system/           # 알림 등 공용 시스템 컴포넌트
│  ├─ layout/           # Header, Footer 등 레이아웃
│  ├─ ui/               # 버튼, 카드 등 재사용 UI
├─ pages/
│  ├─ system/           # 알림 / 설정 페이지
│  ├─ building/         # 매물 관련 페이지
│  ├─ user/             # 로그인 / 회원 / 마이페이지
│  ├─ deal/             # 거래 / 결제 페이지
│  └─ review/           # 리뷰 관련 페이지
├─ router/              # Vue Router 설정
├─ stores/              # Pinia 상태 관리 (notification 등)
├─ styles/              # Tailwind / 공통 스타일
├─ utils/               # 공용 유틸 함수
└─ main.js              # 진입 파일
```

---

## ⚙️ 환경 설정

`.env` 파일 예시

```env
VITE_API_BASE_URL=http://localhost:8080
VITE_FIREBASE_API_KEY=your_api_key
VITE_FIREBASE_PROJECT_ID=your_project_id
VITE_FIREBASE_SENDER_ID=your_sender_id
VITE_FIREBASE_APP_ID=your_app_id
VITE_FIREBASE_VAPID_KEY=your_vapid_key
```
---

## 🚀 실행 방법

### 1️⃣ 의존성 설치

```bash
npm install
```

### 2️⃣ 개발 서버 실행

```bash
npm run dev
```

### 3️⃣ 프로덕션 빌드

```bash
npm run build
```

### 4️⃣ 배포

Vercel 또는 NCP Object Storage를 이용해 `dist/` 폴더 업로드

---

## 🔔 FCM 알림 테스트

1. Firebase 프로젝트에서 `firebase-messaging-sw.js` 등록
2. 백엔드에서 `/api/fcm/register` 호출 시 토큰 자동 저장
3. 백엔드 이벤트 발생 시 브라우저 알림 수신 확인

> 실제 구현에서는 로그인 시 FCM 토큰 자동 등록,
> 알림 클릭 시 관련 페이지로 이동하도록 처리되어 있습니다.

---

## 🧠 협업 및 문서화

* **GitHub** – 이슈 및 PR 기반 협업
* **Notion / Jira** – 기획 및 일정 관리
* **Swagger** – API 명세 확인
* **Figma** – UI 프로토타입 설계

---

## 👥 팀 정보

| 이름      | 역할         | 주요 담당          |
| ------- | ---------- | -------------- |
| **백현빈** | 팀장 / 프론트엔드 | 메인 / 매물 등록 페이지 |
| **강경민** | 프론트엔드      | 알림 페이지, FCM 연동 |
| **김영오** | 프론트엔드      | 지도 / 리뷰 페이지    |
| **박소정** | 프론트엔드      | 사용자 / 로그인 페이지  |
| **안수연** | 프론트엔드      | 채팅 페이지         |
| **이해인** | 프론트엔드      | 거래 페이지         |
| **전경환** | 프론트엔드      | 결제 / 리포트 페이지   |

---

## 📜 License

이 프로젝트는 **교육 및 포트폴리오용 비상업적 프로젝트**입니다.
무단 복제 및 배포를 금합니다.

---
