# beodd 디자인 소싱 DB — v5

## 이번 변경

**1. 끊긴 링크 교정**

| 항목 | 이전 | 지금 |
|---|---|---|
| 미메시스 | mimesisart.co.kr (403) | mimesisartmuseum.co.kr |
| 더 북 소사이어티 | thebooksociety.org (403) | mediabus.org |
| 땡스북스 | thanksbooks.com (서버 중단) | instagram.com/thanksbooks |
| 효시 (고재효) | hyosi.kr | www.hyosi.kr |
| Smile Materials | smile-plastics.com (503) | smile-materials.com (사명 변경) |

858곳 **전부 링크 연결 완료** (링크 없는 항목 0).

**2. 검색 버튼(⌕) 추가 — 링크가 죽어도 막히지 않도록**

모든 항목 오른쪽에 돋보기 버튼이 생겼습니다. 누르면 그 브랜드·작가 이름으로 웹 검색이 열립니다.
- 한글 이름 → 네이버
- 영문 이름 → 구글

공식 사이트가 닫혔거나 주소가 바뀌어도 한 번에 찾을 수 있고,
이미지를 빠르게 훑어볼 때도 유용합니다.
링크가 없는 항목은 이 버튼이 진하게 표시됩니다.

**3. 헤더 로고**

흰 배경 이미지 대신 배경이 없는 마크로 교체했습니다. 페이지 배경색과 미세하게 어긋나던 사각형이
사라졌고, 다크 모드에서는 로고가 자동으로 밝게 반전됩니다.

## 파일 (전부 최상단, 폴더 없음)

```
index.html                  ← 앱 전체 (858곳 데이터 내장)
manifest.webmanifest / sw.js
beodd.otf / PretendardVariable.woff2
mark.png / apple-touch-icon.png
icon-192.png / icon-512.png / icon-maskable-512.png / favicon-32.png
.nojekyll                   ← 숨김 파일, 반드시 포함
```

## 배포

기존 레포 파일을 전부 지우고 위 파일을 올립니다.
GitHub → Add file → Upload files → 전체 드래그 → Commit
`.nojekyll` 은 파인더에서 `Cmd + Shift + .` 로 표시됩니다.

배포 후 상단에 **858곳 · 15 카테고리** 가 보이면 정상입니다.

## 아이폰

사파리로 접속 → 공유 `□↑` → **홈 화면에 추가**
이미 설치한 분은 앱을 완전히 종료 후 다시 열면 갱신됩니다.

## 사용법

- **검색창** — 브랜드·작가·지역·설명·도메인 동시 검색
- **카테고리 칩** — 상단 고정. 스크롤하면 현재 위치가 자동 표시
- **⌕** — 그 이름으로 웹 검색 (링크가 안 열릴 때)
- **★** — 프로젝트 후보 모아두기. 칩의 `★ 즐겨찾기` 로 모아 보기
- **≡** — 정렬(기본순/이름순), 설명 표시, 즐겨찾기 비우기
- 검색 결과는 주소에 남아 공유 가능 (`?q=덴마크`)

## 데이터 수정

`index.html` 안의 `window.__SOURCING_DB=[...]` 가 데이터입니다.
수정 후 배포할 때 **`sw.js` 첫 줄 버전을 반드시 올리세요.**

```js
const VERSION = 'beodd-db-v5';   →   'beodd-db-v6';
```
