# 이 레포에서 작업할 때

- 작업 전에 `CONVENTIONS.md`를 읽고 따른다.
- 기준 소스는 레포 밖에 받아서 읽는다:
  `git clone --depth 1 --branch 0.34.1 https://github.com/crawl/crawl /home/claude/dcss-src`
  (주요 위치: `crawl-ref/source/` — `dat/`는 YAML·설명문 데이터, `*.cc`/`*.h`는 로직과 표)
- 작업 단위(카테고리 하나 등)가 끝날 때마다 커밋하고 push한다.
- `README.md` 목차의 상태 칸을 갱신한다.
