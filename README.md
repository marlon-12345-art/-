# 대신금속 구매관리

구매요청 → 발주 → 입고 → 마감 → 마감관리(매입 집계·대금지불·구매 계획/실적) → 협력업체 SCM까지 한 화면에서 처리하는 웹앱입니다.

## 폴더 구성

| 경로 | 내용 |
|---|---|
| `index.html` | 바로 실행되는 단독 버전 (브라우저 IndexedDB에 저장, 1인용). GitHub Pages로 그대로 배포 가능 |
| `src/purchasing_artifact.html` | 원본 소스 (claude.ai Artifact 런타임 `window.claude` 사용) |
| `src/claude-shim.js` | `window.claude`(db·user·downloads·assets·sample) 대체 모듈. 서버로 옮길 때 이 파일만 교체 |
| `templates/` | 품목 일괄등록·구매요청 품목 엑셀 서식 |
| `docs/이식가이드.md` | 기능 명세·데이터 구조·업무 규칙·이식 방법 |

## 실행

`index.html`을 브라우저로 열면 됩니다. 오른쪽 아래 [데이터 가져오기]로 `db_export.json`을 불러올 수 있어요.
**실제 데이터 파일(`data/`, `db_export*.json`)은 거래처·계정 정보가 들어 있어 저장소에 올리지 않습니다** (`.gitignore`).

## 수정 흐름

1. `src/purchasing_artifact.html`을 고친다 (앱 본문)
2. `index.html`을 다시 만든다: `<title>` 다음에 `src/claude-shim.js`를 `<script>`로 넣고 나머지를 `<body>`에 넣음
3. 커밋·푸시
