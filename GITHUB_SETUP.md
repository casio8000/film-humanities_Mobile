# 🎬 영화DB v24 — GitHub Pages 설정 가이드

## 📁 업로드할 파일 구조

```
📁 film-humanities_Mobile/ (저장소 루트)
│
├── movie_db_v24.html          ← 메인 앱 ✅ 필수
├── manifest.json              ← PWA 설정 ✅ 필수
├── icon-192.png               ← 앱 아이콘 ✅ 필수
├── icon-512.png               ← 앱 아이콘 ✅ 필수
├── movie_list_complete.xlsx   ← 영화 DB 엑셀 ✅ 필수 (루트에!)
├── generate_humnotes.py       ← 인문학 노트 생성 스크립트
│
└── images/
    ├── movie/          ← NO 1 ~ 1,000.jpg
    │   ├── 1.jpg
    │   ├── 2.jpg
    │   └── ...1000.jpg
    ├── movie_2/        ← NO 1,001 ~ 2,000.jpg
    │   ├── 1001.jpg
    │   └── ...2000.jpg
    ├── movie_3/        ← NO 2,001 ~ 3,000.jpg
    │   ├── 2001.jpg
    │   └── ...3000.jpg
    └── movie_4/        ← NO 3,001 ~ 3,423.jpg
        ├── 3001.jpg
        └── ...3423.jpg
```

> ⚠️ 이미지 파일명은 **순수 번호.jpg** 형식만 지원 (예: `1.jpg`, `1234.jpg`)
> 한글 제목이나 특수문자 포함 금지

---

## ⚙️ GitHub Pages 활성화

1. 저장소 → **Settings** → **Pages**
2. Source: **Deploy from a branch** → Branch: **main** / **/ (root)** → **Save**
3. 잠시 후 `https://casio8000.github.io/film-humanities_Mobile/` 생성

---

## 📱 모바일 앱 설치

### iOS (Safari)
1. `https://casio8000.github.io/film-humanities_Mobile/movie_db_v24.html` 접속
2. 하단 공유 버튼(□↑) → **홈 화면에 추가**
3. 전체화면 앱으로 실행

### Android (Chrome)
1. 위 URL 접속
2. 우상단 메뉴(⋮) → **앱 설치**
3. 아이콘으로 실행

---

## 🔄 앱 첫 실행 시 자동 처리 순서

```
1. IndexedDB 초기화
2. 데이터 없으면 → GitHub에서 movie_list_complete.xlsx 자동 다운로드
3. 감정태그 없는 작품 → 자동 분류 실행
4. 카드 표시 시 → GitHub images/ 폴더에서 포스터 자동 다운로드 → IndexedDB 캐싱
5. 이후 실행 → IndexedDB에서 즉시 로드 (오프라인 가능)
```

---

## 📅 관람일 정렬 (엑셀 J열)

엑셀 J열에 감상일 날짜를 입력하면 **관람일 최신순** 정렬이 정확히 동작합니다.

```
J열 형식 예시:
2024-03-15
2024/03/15
2024.03.15
```

---

## 📤 SNS 공유 방식

### 카카오톡으로 공유하기
1. **감정추천 내보내기** 모달 → 📤 SNS 공유 버튼
2. 모바일 공유 시트 → 카카오톡 선택
3. 영화 제목 + 네이버 검색 링크가 함께 전송됨

### GitHub Pages URL 공유 시
- URL을 카카오톡에 붙여넣으면 OG 태그로 미리보기 자동 표시

---

## 🔁 데이터 업데이트 방법

```bash
# 엑셀 수정 후
git add movie_list_complete.xlsx
git commit -m "데이터 업데이트"
git push

# 앱에서: 🔄 GitHub 동기화 클릭 (데스크탑) 또는 재접속 (모바일)
```
