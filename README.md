# Frontend (Vue 3 + Vite)

부동산 서비스의 프론트엔드 SPA입니다.  
**Vue 3 + Vite + Pinia + Vue Router + Axios** 기반이며, 알림(FCM), 지도(Kakao Map), 리뷰/매물/채팅 등 화면을 제공합니다.

## 🧱 Tech Stack
- Framework: Vue 3
- Build: Vite
- State: Pinia
- Router: Vue Router 4
- HTTP: Axios (기본 baseURL = `/api`)
- (선택) Push: Firebase Cloud Messaging (Web Push)
- (선택) UI: Tailwind CSS / Font Awesome 등

## 📂 프로젝트 구조
```
.
├─ src/
│ ├─ api/ # axios 인스턴스 + 도메인별 API
│ ├─ components/ # 공용 컴포넌트
│ ├─ pages/ # 라우팅 단위 화면
│ ├─ router/ # Vue Router 설정
│ ├─ stores/ # Pinia 스토어
│ ├─ utils/ # 유틸(FCM 등)
│ └─ firebase.js # Firebase 초기화(사용 시)
└─ public/
└─ firebase-messaging-sw.js # FCM 서비스워커(사용 시)
```

## 🚀 시작하기
```bash
# Node.js 18+ (권장: 20+)
npm install
npm run dev        # http://localhost:5173
npm run build      # dist/
npm run preview
```

## 개발 프록시 (백엔드 ↔ 프론트 로컬 연동)
백엔드가 http://localhost:8080 에서 동작한다면 vite.config.js에 프록시를 설정하세요.
```
// vite.config.js
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'

export default defineConfig({
  plugins: [vue()],
  server: {
    proxy: {
      '/api': { target: 'http://localhost:8080', changeOrigin: true }
    }
  }
})
```

## 🔐 환경 변수 (.env)
필요한 키만 사용하세요. 민감 정보는 레포에 커밋하지 않습니다.
```
# 외부 API
VITE_KAKAO_MAP_API_KEY=...

# FCM (사용 시)
VITE_FIREBASE_VAPID_KEY=...

# 기타 플래그
VITE_USE_MOCK_API=false
```

## 🔔 FCM(Web Push, 선택)
src/firebase.js 에 Firebase 설정 추가

public/firebase-messaging-sw.js 에 동일 설정(메시징) 반영

브라우저 알림 권한 요청 → 발급받은 토큰을 백엔드에 등록(예: /api/fcm/register)

firebase.js 예시
```
// src/firebase.js
import { initializeApp } from 'firebase/app'
import { getMessaging, getToken, onMessage } from 'firebase/messaging'

const firebaseConfig = {
  apiKey: '...',
  authDomain: '...',
  projectId: '...',
  storageBucket: '...',
  messagingSenderId: '...',
  appId: '...'
}

const app = initializeApp(firebaseConfig)
export const messaging = getMessaging(app)

export async function requestFcmToken () {
  return getToken(messaging, { vapidKey: import.meta.env.VITE_FIREBASE_VAPID_KEY })
}

onMessage(messaging, (payload) => {
  console.log('[FCM] foreground message:', payload)
})
```

서비스워커 예시
```
// public/firebase-messaging-sw.js
/* global importScripts, firebase */
importScripts('https://www.gstatic.com/firebasejs/10.12.2/firebase-app-compat.js')
importScripts('https://www.gstatic.com/firebasejs/10.12.2/firebase-messaging-compat.js')

firebase.initializeApp({
  apiKey: '...',
  authDomain: '...',
  projectId: '...',
  storageBucket: '...',
  messagingSenderId: '...',
  appId: '...'
})

const messaging = firebase.messaging()
```

## 🧪 스크립트
```
npm run dev
npm run build
npm run preview
```
