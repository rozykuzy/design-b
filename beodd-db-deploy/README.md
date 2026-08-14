# beodd 디자인 소싱 DB — 배포 패키지 (v2)

## ⚠️ 지난 배포에서 화면이 깨진 이유

이전 패키지는 `assets/` 폴더 안에 자바스크립트·폰트가 들어 있었는데, **그 폴더가 업로드되지 않아**
`{{ tally }}`, `{{ c.name }}` 같은 코드가 그대로 보였습니다.

이번 v2는 **하위 폴더를 아예 없앴습니다.** 화면·데이터·기능이 전부 `index.html` 한 파일 안에
들어 있어, 나머지 파일이 빠져도 페이지는 정상 동작합니다.

---

## 1) 업로드

아래 **9개 파일을 전부** 레포 최상단에 올립니다. 폴더는 없습니다.

```
index.html                  ← 페이지 전체 (데이터·디자인·기능 전부 내장)
manifest.webmanifest        ← 홈 화면 앱 정보
sw.js                       ← 오프라인 캐시
PretendardVariable.woff2    ← 본문 서체
apple-touch-icon.png        ← 아이폰 홈 화면 아이콘
icon-192.png / icon-512.png / icon-maskable-512.png
favicon-32.png
.nojekyll                   ← 숨김 파일. 반드시 포함
```

> `.nojekyll` 은 점으로 시작해 파인더에서 안 보입니다. `Cmd + Shift + .` 로 숨김 파일을 표시하세요.

**GitHub 웹에서:** 레포 → Add file → Upload files → 위 파일 전부 드래그 → Commit changes
→ Settings → Pages → Branch `main` / `/ (root)` → Save → 1~2분 뒤 접속

**터미널에서:**
```bash
cd dist
git init -b main && git add -A && git commit -m "beodd sourcing db v2"
git remote add origin https://github.com/<계정>/<레포>.git
git push -u origin main
```

### 업로드 후 자가 점검
접속했을 때 상단에 **858곳 · 15 카테고리** 가 보이면 정상입니다.
`{{ }}` 가 보이면 `index.html` 이 옛 버전입니다. 새 파일로 덮어쓰세요.

---

## 2) 아이폰 홈 화면 앱 (직원 안내)

1. **사파리**로 배포 주소 접속 (크롬 아님)
2. 하단 공유 버튼 `□↑` → **홈 화면에 추가**
3. 이름 `beodd DB` 확인 → **추가**

검은 beodd 마크 아이콘으로 실행되고, 주소창 없는 전체 화면으로 열립니다.
**한 번 연 뒤에는 인터넷이 없어도 열립니다** (지하철·해외 출장·현장).

---

## 3) 데이터 수정

`index.html` 안의 `window.__SOURCING_DB = [...]` 가 데이터입니다.
원본 엑셀(`디자인 소싱 DB.xlsx`)을 고친 뒤 Claude에게 주면 새 `index.html` 을 만들어 줍니다.

**수정본을 올릴 때는 `sw.js` 첫 줄 버전도 올리세요.**

```js
const VERSION = 'beodd-db-v2';   →   'beodd-db-v3'
```

이걸 올려야 이미 설치한 직원 기기의 캐시가 새 내용으로 교체됩니다.
두 파일(`index.html`, `sw.js`)을 함께 커밋하면 다음 실행 때 자동 반영됩니다.

---

## 검증 완료 항목

아이폰 사파리 환경에서 실제 렌더링을 확인했습니다.

- 858곳 전체 표시 · 15개 카테고리
- 검색: 브랜드명·설명·지역·도메인 동시 검색, 일치 부분 하이라이트
- 모바일에서 설명 표시 (이전 버전은 숨김 처리돼 있었음)
- 검색창 터치 시 화면 확대되지 않음 (iOS 줌 방지)
- 노치·홈 인디케이터 영역 침범 없음
- 비행기 모드에서 전체 목록 정상 표시
- 브랜드명 탭 → 공식 사이트 새 탭
- 인쇄 시 검색·네비 자동 숨김
