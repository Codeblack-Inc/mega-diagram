# mega-diagram

Claude Code + Codex + Factory 플러그인. 공용 스킬은 `skills/mega-diagram/` 하나 — 모든 호스트가 같은 파일을 쓴다.

- [diagram-design](https://github.com/cathrynlavery/diagram-design) v2.6.33(`dc1ace4`)의 포크. 원본 구조·검증 스크립트·ADR을 그대로 두고 바꾼 곳만 관리한다. 원본 변경을 가져올 때는 `diagram-design` → `mega-diagram` 이름 변경과 팔레트 매핑(아래)을 다시 적용한다
- 한국형 규칙은 `skills/mega-diagram/references/mega.md`, 색 토큰은 `references/style-guide.md`. 팔레트를 바꾸면 예제 HTML(`assets/`)도 같은 값으로 바꿔야 `lint-skin.py`가 통과한다
- 팔레트 매핑(원본 → mega): paper `#f5f5f5`→`#ffffff`(다크 ink는 `#f6f5fa`), ink `#2d3142`→`#17152b`, muted `#4f5d75`→`#68657b`, soft `#7a8399`→`#8a879c`, rule-solid `#bfc0c0`→`#d4d2de`, paper-2 `#ececec`→`#f6f5fa`, accent `#eb6c36`→`#2f6fdb`, link `#2e5aa8`→`#6043d5`, 다크 accent `#f08a59`→`#6e9bea`
- SVG 안에 전면 배경 `<rect>`를 두지 않는다(투명 내보내기). 배경은 HTML `body`가 칠한다
- 외부 스타일시트는 Google Fonts `/css2`와 고정된 Pretendard jsDelivr URL 하나만 허용(`self_check.py`, `lint-skin.py`의 `PRETENDARD_STYLESHEET`)
- `SKILL.md`는 40,000바이트 상한(ADR 0004, `verify-semantic-motion.py`). 한글은 글자당 3바이트이므로 긴 설명은 `references/`로 보낸다
- 매니페스트 설명은 500자 이하이고 41개 형식 이름을 모두 포함해야 한다(`verify-docs-sync.py`)
- 버전 올릴 때 `.claude-plugin/plugin.json`, `.codex-plugin/plugin.json`, `.factory-plugin/plugin.json`, SKILL.md `metadata.version` 함께 수정 (`scripts/bump-plugin-version.py`)
- 테스트: `for t in scripts/test-*.py; do python3 "$t"; done` + `python3 scripts/verify-docs-sync.py` + `python3 scripts/lint-skin.py --all --baseline`
- 스크린샷: `PLAYWRIGHT_CHANNEL=chrome uv run --with playwright python scripts/render-canonical-screenshots.py` → `uv run --with pillow python scripts/build-readme-thumbs.py`. README용 캡처는 흰 배경을 유지한다(GitHub 다크 모드 가독성)
- 로고는 [mega-bi](https://github.com/Codeblack-Inc/mega-bi)가 원본(`scripts/build-product-logo.py`). `docs/brand/`는 복사본
