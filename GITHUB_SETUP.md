# 🎬 영화/드라마 DB — GitHub Pages 설정 가이드

## ✅ 파일명 영구 고정: `movie_db_final.html`
앱 파일명이 `movie_db_final.html`로 고정되어 업데이트 시 **manifest.json과 index.html을 수정할 필요 없음**

---

## 📁 GitHub 저장소 파일 구조

```
film-humanities_Mobile/ (루트)
├── movie_db_final.html        ← 앱 (업데이트 시 이 파일만 교체)
├── manifest.json              ← PWA 설정 (수정 불필요)
├── icon-192.png               ← 앱 아이콘
├── icon-512.png               ← 앱 아이콘 (고해상도)
├── movie_list_complete.xlsx   ← 영화 데이터 (엑셀 수정 후 재업로드)
├── generate_humnotes.py       ← 인문학 노트 일괄 생성 스크립트
│
└── images/
    ├── movie/          ← NO 1 ~ 1,000.jpg
    ├── movie_2/        ← NO 1,001 ~ 2,000.jpg
    ├── movie_3/        ← NO 2,001 ~ 3,000.jpg
    └── movie_4/        ← NO 3,001 ~ 3,423.jpg
```

> ⚠️ 이미지 파일명은 **순수 번호.jpg** 형식만 지원 (예: `1.jpg`, `1234.jpg`)

---

## 🔄 업데이트 시 수정할 파일

| 상황 | 수정할 파일 |
|------|------------|
| 앱 기능 수정 | `movie_db_final.html` 만 교체 |
| 엑셀 데이터 수정 | `movie_list_complete.xlsx` 교체 → 앱에서 🔄 데이터 동기화 |
| 이미지 추가/수정 | 해당 `images/movie*/` 파일 교체 → 앱에서 🖼️ 이미지 동기화 |
| 인문학 노트 수정 | 엑셀 K열 수정 → xlsx 재업로드 → 🔄 데이터 동기화 |

> `manifest.json`, `icon-*.png`, `GITHUB_SETUP.md`는 특별한 경우 외 수정 불필요

---

## 📱 모바일 앱 설치

### iOS (Safari)
1. `https://casio8000.github.io/film-humanities_Mobile/movie_db_final.html` 접속
2. 공유(□↑) → **홈 화면에 추가**

### Android (Chrome)
1. 위 URL 접속
2. 메뉴(⋮) → **앱 설치**

---

## 🔗 영화 링크 수정 방법 (엑셀 B열)

1. 엑셀 B열에서 해당 제목 셀 우클릭 → 하이퍼링크 편집
2. 올바른 네이버/왓챠/IMDb URL 입력
3. 저장 후 GitHub에 push
4. 앱에서 **🔄 데이터 동기화** 클릭

---

## 🔁 앱 첫 실행 자동 처리 순서

```
1. IndexedDB 초기화
2. 데이터 없으면 → GitHub 엑셀 자동 다운로드
3. 태그 없는 작품 → 감정태그 자동 분류
4. 카드 표시 시 → GitHub images/ 포스터 순차 다운로드 (세마포어 4개 동시 제한)
5. 이후 실행 → IndexedDB에서 즉시 로드 (오프라인 가능)
```
