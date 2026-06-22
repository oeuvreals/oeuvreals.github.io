# oeuvreals.github.io

개인 웹사이트 — 포트폴리오 · 개인적인 글 · 음악 · 포커 공부 노트.

- 주소: https://oeuvreals.github.io
- 테마: [minimal-mistakes](https://github.com/mmistakes/minimal-mistakes) (remote_theme, dark skin)
- 빌드: GitHub Pages 자동 빌드

## 콘텐츠를 추가하는 법

| 무엇을 | 어디에 | 파일 형식 |
|---|---|---|
| 블로그 글 | `_posts/` | `YYYY-MM-DD-제목.md` |
| 프로젝트 | `_portfolio/` | `이름.md` |
| 음악 | `_music/` | `이름.md` |
| 포커 노트 | `_poker/` | `이름.md` |

각 파일 맨 위 `--- ... ---`(front matter)에 `title`, `excerpt`, `date` 등을 적고,
그 아래 본문을 마크다운으로 작성하면 됩니다. 기존 샘플 파일을 복사해서 시작하세요.

## 설정 바꾸기

- 사이트 제목·소개·프로필 링크: `_config.yml`
- 상단 메뉴: `_data/navigation.yml`
- 테마 색(skin): `_config.yml`의 `minimal_mistakes_skin` (dark/dirt/contrast/...)

## 반영하기

```bash
git add .
git commit -m "변경 내용 요약"
git push
```
