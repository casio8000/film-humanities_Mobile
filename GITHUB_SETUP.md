# 📱 영화DB — GitHub Pages 모바일 앱 설정 가이드

## 업로드할 파일 목록

```
📁 GitHub 저장소 루트
├── movie_db_v29.html          ← 메인 앱
├── manifest.json              ← PWA 설정
├── icon-192.png               ← 앱 아이콘
├── icon-512.png               ← 앱 아이콘 (고해상도)
├── movie_list_complete.xlsx   ← 영화 DB 엑셀 (업데이트 시 덮어쓰기)
└── generate_humnotes.py       ← 인문학 노트 생성 스크립트 (선택)
```

---

## 1단계 — GitHub Pages 활성화

1. GitHub 저장소 → **Settings** 탭
2. 왼쪽 메뉴 **Pages** 클릭
3. Source: **Deploy from a branch**
4. Branch: **main** / **/ (root)** 선택 → **Save**
5. 잠시 후 `https://casio8000.github.io/film-humanities_Mobile/` 주소 생성

---

## 2단계 — 모바일 홈 화면에 앱 추가

### iOS (Safari)
1. Safari에서 위 GitHub Pages URL 접속
2. 하단 공유 버튼(□↑) 탭
3. **"홈 화면에 추가"** 선택
4. 이름 확인 후 **추가** → 앱 아이콘 생성 완료

### Android (Chrome)
1. Chrome에서 URL 접속
2. 주소창 오른쪽 메뉴(⋮) 탭
3. **"앱 설치"** 또는 **"홈 화면에 추가"** 선택
4. 설치 → 앱처럼 실행 가능

---

## 3단계 — 엑셀 업데이트 방법

엑셀 파일을 수정하고 GitHub에 push하면 앱에서 🔄 동기화 버튼으로 즉시 반영됩니다.

```bash
# 로컬에서 수정 후
git add movie_list_complete.xlsx
git commit -m "영화 데이터 업데이트"
git push
```

앱에서: **🔄 GitHub 동기화** 버튼 클릭

---

## 4단계 — 인문학 노트 생성 후 반영

```bash
# 스크립트 실행 (엑셀 K열에 노트 자동 생성)
python generate_humnotes.py

# GitHub에 업로드
git add movie_list_complete.xlsx
git commit -m "인문학 노트 추가"
git push

# 앱에서 🔄 동기화 클릭
```

---

## 주요 URL 구조

| 파일 | 역할 |
|------|------|
| `movie_db_v29.html` | 메인 앱 |
| `manifest.json` | PWA (홈 화면 앱) 설정 |
| `movie_list_complete.xlsx` | 영화 데이터 (앱이 자동 로드) |

---

## 특징

- **IndexedDB 로컬 저장**: 이미지를 한 번 로드하면 기기에 저장되어 이후 오프라인에서도 포스터 표시
- **PWA**: 홈 화면 추가 시 전체화면 앱처럼 실행, 주소창 없음
- **GitHub Raw URL**: 엑셀 파일은 GitHub에서 직접 fetch → 항상 최신 데이터
