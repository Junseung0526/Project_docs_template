# 템플릿 사용법

캡스톤·해커톤·사이드 프로젝트용 GitHub 조직 `.github` 레포 템플릿입니다.
조직 첫 화면, 아키텍처·기능·로드맵 문서, 협업 규칙, 이슈/PR 양식이 들어 있습니다.

> 세팅이 끝나면 이 파일은 지워도 됩니다.

## 1. 올리기 (5분)

1. GitHub에서 조직을 만들고, 조직 안에 이름이 정확히 **`.github`** 인 **Public** 레포를 만듭니다.
2. 이 폴더(`template/`)의 **안의 내용 전체**를 그 레포 루트에 올립니다. 숨김 폴더 `.github/` 도 꼭 포함하세요.

```bash
cd template
git init -b main && git add . && git commit -m "docs: 조직 템플릿 초기화"
git remote add origin https://github.com/<조직ID>/.github.git
git push -u origin main
```

3. push가 끝나면 Actions의 `template-setup` 이 `{{ORG}}`·`{{PROJECT_NAME}}` 을 조직 ID로 바꿔 자동 커밋합니다 (약 30초).
4. `https://github.com/<조직ID>` 에 접속하면 조직 프로필이 바로 보입니다.

> Action이 실패하면 (조직 설정에서 Actions 쓰기 권한이 막힌 경우) 로컬에서 직접 바꾸고 다시 push 하세요.
>
> ```bash
> grep -rlE '\{\{(ORG|PROJECT_NAME)\}\}' . --exclude-dir=.git --exclude-dir=workflows --exclude=TEMPLATE_GUIDE.md | xargs sed -i '' -e 's/{{ORG}}/조직ID/g' -e 's/{{PROJECT_NAME}}/프로젝트명/g'
> ```
>
> Linux에서는 `sed -i ''` 대신 `sed -i` 입니다.

## 2. 채우기

- 프로젝트 이름은 처음엔 조직 ID로 들어갑니다. `profile/README.md` 첫 줄과 `docs/images/overview.svg` 제목을 원하는 이름으로 고치세요.
- `<!-- -->` 주석은 작성 가이드입니다. GitHub 화면에는 보이지 않으니 채운 뒤 지우면 됩니다.
- `기능 A`, `팀원 1` 같은 예시 값은 그대로 둬도 화면이 깨지지 않습니다. 하나씩 바꿔 나가면 됩니다.

## 3. 자동으로 적용되는 것

| 파일 | 효과 |
| :--- | :--- |
| `profile/README.md` | 조직 첫 화면에 표시 |
| `.github/ISSUE_TEMPLATE/*` | 조직의 **모든 레포**에서 새 이슈 양식으로 사용 (레포에 자체 양식이 없을 때) |
| `.github/PULL_REQUEST_TEMPLATE.md` | 조직의 모든 레포에서 PR 본문 기본값 |
| `CONTRIBUTING.md` | 모든 레포의 이슈/PR 화면에 협업 가이드 링크 표시 |

## 4. 규모별 사용법

| 상황 | 쓸 문서 | 줄여도 되는 것 |
| :--- | :--- | :--- |
| **해커톤 (1~3일)** | `profile/README.md`, `FEATURES.md`(MVP만), `CONTRIBUTING.md` 1·2장 | `ARCHITECTURE.md`는 1·5·7장만, `ROADMAP.md`는 시간 단위 표로 |
| **캡스톤 / 학기 프로젝트** | 전부 | — |
| **사이드 프로젝트** | README, ARCHITECTURE, CONTRIBUTING | 역할 표, 검증 시나리오 |

해커톤이면 `develop` 없이 `main` 하나에 PR만 받아도 충분합니다 (CONTRIBUTING 1장).

## 5. 다이어그램

- 문서 속 다이어그램은 **Mermaid** 라 GitHub에서 바로 그려집니다. 수정은 [mermaid.live](https://mermaid.live)에서 미리 보며 하세요.
- `docs/images/overview.svg` 는 텍스트만 바꾸면 되는 입력 → 처리 → 출력 그림입니다. 칸을 늘리려면 `<rect>`·`<text>` 묶음을 복사해 `y` 값을 68씩 내리세요.
