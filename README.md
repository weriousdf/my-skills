# my-skills

Claude Code 에서 매번 반복해 지시하던 작업을 스킬 파일로 굳혀 둔 모음입니다.
이 폴더를 열면 Claude Code 가 `.claude/skills` 아래의 `SKILL.md` 를 자동으로 인식합니다.

## 스킬 목록

| 스킬 | 하는 일 | 폴더 |
| --- | --- | --- |
| `blog-article-structurer` | 키워드 3개와 요약 메모로 SEO 메타 정보와 계층형 목차를 갖춘 블로그 초안을 생성 | `.claude/skills/blog-article-structurer/` |
| `todo-summary` | 오늘 완료한 할 일을 커밋 메시지 형식으로 요약 | `.claude/skills/todo-summary/` |

스킬은 하나당 폴더 하나이고, 그 안의 `SKILL.md` 파일이 전부입니다.
새 스킬을 추가할 때도 폴더를 새로 만듭니다.

## blog-article-structurer

### 기존의 불편함

- 메모 수준의 아이디어를 글로 바꿀 때마다 도입부 후킹, 본문 목차 깊이(H2, H3),
  SEO 메타 설명 포맷을 AI 에게 매번 반복해서 지시해야 했습니다.
- 지시를 빠뜨리면 글 구조가 제각각이 되거나 검색 노출에 필요한 요소가 누락되는
  문제가 발생했습니다.

### 해결 방식

핵심 키워드 3개와 요약 텍스트만 전달하면 정해진 템플릿에 맞춘 초안을 즉시 출력합니다.

- 최상단에 SEO Description (키워드를 포함한 120~150자)
- 제목(`#`) → 후킹 도입부 → 대주제(`##`) 2~3개 → 세부 단계(`###`)
- 마무리에 핵심 요점 3줄 정리
- 키워드 3개는 본문 전반에 2회 이상 분산 배치

### 쓰는 법

핵심 키워드 3개와 요약 메모를 함께 전달하면 됩니다.

```
/blog-article-structurer
키워드: 아포스티유, 번역공증, 해외제출서류
메모: 아포스티유와 번역공증을 혼동해 서류를 반송당하는 사례가 많다. 둘의 차이와
      제출국별 선택 기준을 정리하고 싶다.
```

## todo-summary

`npm run todo -- summary` 를 실행하고 그 출력을 그대로 보여줍니다.
`todo_list` 앱([github.com/weriousdf/todo_list](https://github.com/weriousdf/todo_list))의
스크립트를 쓰기 때문에, 그 프로젝트 폴더에서 실행해야 동작합니다.

## 다른 프로젝트에서 쓰기

여기 있는 스킬은 이 폴더를 열었을 때만 잡힙니다.
어느 프로젝트에서나 쓰려면 스킬 폴더를 사용자 스킬 경로로 복사합니다.

```
Copy-Item -Recurse .claude\skills\blog-article-structurer $env:USERPROFILE\.claude\skills\
```
