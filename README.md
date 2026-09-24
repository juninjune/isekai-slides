# isekai-slides

isekai VRChat 월드의 프레젠테이션 슬라이드 호스팅 저장소. PDF를 넣고 푸시하면 GitHub Actions가
1920×1080 JPG로 변환해 GitHub Pages로 배포하고, 월드는 재업로드 없이 새 슬라이드를 받는다.

## 슬라이드 교체

1. `input/` 에 PDF를 넣는다 (기존 PDF는 지운다 — **PDF는 1개만**).
2. 커밋·푸시한다. GitHub 웹에서 `input/` 폴더에 드래그 앤 드롭 업로드해도 된다.
3. Actions 탭에서 `PDF to Slides` 가 초록색이 되면 끝 (2~3분).
4. 확인: https://juninjune.github.io/isekai-slides/meta.json 의 `total_pages`.

강제 재변환은 Actions → `PDF to Slides` → Run workflow.

## URL

- `https://juninjune.github.io/isekai-slides/meta.json`
- `https://juninjune.github.io/isekai-slides/slides/slide_001.jpg` … `slide_NNN.jpg`

월드 쪽 `SlideLoader` 인스펙터의 URL 생성기에 Base URL `https://juninjune.github.io/isekai-slides` 를 넣으면 위 규약대로 채워진다.

## 구조

```
input/            ← PDF 원본 (1개). 이력은 git에 남는다.
scripts/convert_pdf.py
Web/meta.json     ← {"total_pages": N, ...}
Web/slides/       ← slide_001.jpg …  (Actions가 생성·커밋)
.github/workflows/slides.yml
```

슬라이드는 공개 URL이다. 링크를 아는 사람은 누구나 볼 수 있다.
