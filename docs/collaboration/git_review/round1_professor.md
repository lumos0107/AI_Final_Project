# 1라운드: 수업 담당 교수

- 기준: 2026-11-19. 자료(00_자료.md)에 더해 저장소를 읽기 전용으로 조회한 결과(`git log --all`, `gh api .../commits/<해시>`, `gh pr view 3 --json commits`, `gh issue list`)를 넣었습니다.
- 채점할 때 브랜치 모델 자체에는 점수를 주지 않습니다. 공지 개인 평가 2번의 세 가지, 즉 커밋된 코드의 내용, 기간 전체 분포, 이슈·PR 기록만 봅니다. 아래 평가도 이 기준입니다.

## 1. 지금까지 한 일 평가

### 가. 잘한 점

1) 코드 전에 기록부터 남겼습니다. `docs/ideation/README.md` 5장 표가 채점 기준 2·3번과 문서를 짝지어 두었고(자료 4장 나.), `ai-mistake` 라벨(자료 3장 5절)은 발표 필수 요소 "AI 활용 과정"의 재료를 4주 동안 모으는 장치로 쓸모가 있습니다.
2) 합치기를 merge commit 하나로 둔 판단이 맞습니다(자료 3장 4절 3). squash면 PR 하나가 커밋 하나로 뭉쳐 분포를 볼 수 없습니다. merge commit이면 작업 브랜치의 커밋이 자기 날짜를 지닌 채 기본 브랜치에 들어옵니다. 프로필은 author date, 저장소 화면은 commit date로 날짜를 잡습니다[1].
3) 일정이 공지 제출 규정과 맞습니다. 마감 주는 버그만, 마감 직전 `v1.0` 태그, 12/21부터 문서만(자료 3장 6절, 마일스톤 #5).
4) AI가 쓴 글에 AI 표시를 남겼습니다(`Co-Authored-By`, PR 본문 끝 표시). 이 수업은 AI 사용이 전제이므로 감점 사유가 아니고, 숨긴 기록보다 낫습니다.
5) 공개 저장소 점검을 이슈 #1 '주의'에 적었고, 도출 문서에서 개인 PC 경로나 학번 같은 내용은 찾지 못했습니다(`git grep`).

### 나. 문제점

| 번호 | 문제 | 근거 | 심각도 |
|---|---|---|---|
| 1 | 학생 커밋이 깃허브 계정에 연결되지 않음 | 93c3fbe~aaa8792, bafa728 모두 커밋 API의 `author`·`committer`가 `null`. 같은 커밋을 `gh pr view 3 --json commits`로 보면 공동 작성자 Claude는 `claude` 계정으로 연결되고 lumos0107은 login이 비어 있음. 웹에서 만든 c81c2b3만 noreply 주소라 연결됨. 이대로 합치면 기여 그래프와 Contributors 그래프에 학생이 잡히지 않음[1][3]. CONTRIBUTING 7장이 경고한 바로 그 문제 | 상 |
| 2 | 팀원 기록이 0 | 참여자 lumos0107 하나, 초대 대기도 없음(invitations 조회 결과 빈 목록). `04_team_ideas.md`는 "아이디어를 낸 팀원이 2026년 10월에 개인적으로 정리해 둔 분야 지도"를 싣는데 커밋은 lumos0107 이름. 또 main 보호(승인 1명) 때문에 PR #3·#4는 팀원이 들어오기 전엔 합칠 수 없음. 작성자는 자기 PR을 승인할 수 없고[4], 관리자 예외로 혼자 합치면 '리뷰 없이 합침'이 PR에 그대로 남음 | 상 |
| 3 | 기록을 한꺼번에 만든 흔적 | 이슈 #1·#2 16:59:52·55, 커밋 6개 17:00:19~20(2초 안), PR #3 17:00:38, bafa728 17:01:16, PR #4 17:01:21. 89초 안에 이슈→커밋→PR이 끝났고, 이슈의 '할 일' 칸은 모두 빈 채 `Closes`로 닫히게 되어 있음. 11/17~19 사흘 일을 문서별 6개로 나눈 것은 내 눈에 커밋 1건 분량. 도출 문서 약 122KB 중 AI 심사위원 원문 3개(약 77KB)는 AI 출력 그대로라 기여량으로 세지 않음. 한 번은 괜찮지만 이 패턴이 반복되면 '도구로 꾸민 기록'으로 봄 | 중 |
| 4 | `05_ai_corrections.md`의 증거력이 약함 | AI가 쓴 'AI가 틀린 기록'이고 대화 원문 근거가 없음. 7건 중 1·2·5번은 팀의 취향 판단("참신하지 않다", "뭔가 부족하다")이라 AI 오류라기보다 선택. 사실이 틀렸고 무엇으로 확인했는지가 분명한 것은 3·4·6번. 또 `03_blind_review.md`의 '수업 담당 교수' 역할 AI 점수는 실제 채점과 관계없으니 발표 근거로 쓰지 말 것 | 중 |
| 5 | 합치기 마감이 없음 | 자료 3장 6절은 '커밋' 마감만 있음. 12/20 23:50에 연 기능 PR을 12/21 00:10에 합치면 그 merge commit의 날짜가 마감 뒤(저장소 화면은 commit date 기준[1]). 마감 뒤 기능 코드 반영으로 볼 수 있음 | 중 |
| 6 | CONTRIBUTING 2장 가.3) 문구가 부정확 | "main에 들어간 커밋만 셉니다"가 아니라 '기본 브랜치 또는 gh-pages'[1]. 합친 뒤에는 원래 날짜로 잡히므로 위험은 '늦게 합침'보다 '마감까지 못 합침' | 하 |
| 7 | 라벨 중복 | 기본 라벨 bug·enhancement·documentation과 새 라벨 fix·feat·docs가 겹침(자료 5장 라벨) | 하 |
| 8 | 개인 이메일 공개 | 공개 저장소에 올린 브랜치 커밋에 개인 메일 주소가 그대로 보임. 본인이 정할 일 | 하 |

## 2. 브랜치 구성 권고

결론은 후보 A 유지입니다. C에서 `spike/`와 주 끝 태그 두 가지만 가져오고, develop·release는 두지 않습니다. B는 권하지 않습니다.

### 가. 이유

1) 채점에 쓰는 것은 기본 브랜치의 커밋 내용·날짜와 이슈·PR입니다. A에서도 merge commit이면 작업 브랜치 커밋이 원래 날짜로 들어오므로, develop을 두어 얻는 점수는 없습니다.
2) C는 develop을 기본 브랜치로 두므로 기여 집계에서 손해는 없습니다[1]. 문제는 비용입니다. 주마다 develop→main PR 5개, release를 main과 develop 두 곳에 합치기, v1.0 뒤 기본 브랜치 되돌리기가 생깁니다. 이 PR들은 내용 없는 '판 옮기기'라 한 사람 이름으로 PR 수만 늘고, 나는 기여로 세지 않습니다.
3) 팀원 Git 숙련도를 모릅니다(자료 1장). PR 대상 브랜치가 둘이면 첫 주에 잘못된 곳으로 PR을 여는 실수가 나옵니다. 다른 과목을 같이 듣는 2명에게 규칙이 무거우면 지켜지지 않는다는 점도 자료 1장에 있습니다.
4) release/1.0이 하려는 일(기능 동결, 버그만)은 마일스톤 #5와 규칙 한 줄로 됩니다. 배포 중인 사용자가 없어 hotfix와 release를 나눌 이유도 없습니다. B는 여러 판을 동시에 유지하는 제품을 위한 방식입니다.

### 나. A에 더할 것

1) `spike/` 종류. 코드는 `experiments/` 안에만 두고, 버린 후보도 합칩니다. 사전 시험 기록이 '도전과 해결' 재료가 됩니다.
2) 주 끝에 main에 태그 `v0.1`~`v0.4`(선택). GitHub Release 페이지까지는 만들지 않습니다. 발표에서 주차별 진척을 보여 줄 때 씁니다.
3) 합치기 마감. 예: 기능 PR 12/20 18:00, 버그 PR 22:00, `v1.0` 태그 23:00.
4) 브랜치 하나는 1~3일, 날마다 push. 이틀을 넘기면 draft PR로 먼저 열어 진행 기록이 날짜별로 남게 합니다.

## 3. 확장성

### 가. 충분한 것

기능 하나 = 이슈 하나 = 브랜치 하나 = PR 하나, 주차 마일스톤. 2명이 4주 동안 기능 20개 안쪽을 다루기엔 이것으로 충분합니다.

### 나. 더할 가치가 있는 것

1) PR 양식 1개, 칸은 세 개(무엇을 했나 / 어떻게 시험했나 / AI가 틀린 점이 있었나). 발표 필수 요소 '테스트 방법과 결과', 'AI 활용 과정'과 바로 이어집니다.
2) 첫 테스트가 생기면 GitHub Actions로 PR마다 테스트를 돌리는 워크플로 1개. 테스트 결과가 PR에 남습니다.
3) Skill이나 MCP를 쓰면 그 설정 파일을 저장소에 커밋합니다. 채점 기준 2번 "AI 표준과 관련된 기술을 사용했는지"를 저장소에서 바로 확인할 수 있어야 합니다.

### 다. 지나친 것

1) 이슈 양식 4종: 2명에게 관리 부담이고, 모든 이슈가 같은 AI 문체로 보이게 만듭니다.
2) CODEOWNERS: 2명 팀에는 필요 없습니다.
3) 영역 라벨(`area:*`)과 커밋 범위(`feat(ui):`): 주제가 정해지지 않았습니다. 기능이 10개를 넘으면 그때 생각합니다.
4) 주마다 GitHub Release, Projects 보드, 위키: 마일스톤과 태그로 충분합니다.

## 4. 우선순위 (지금 당장 / 1주차 안 / 나중)

### 가. 지금 당장 (11/19~20)

1) 커밋 이메일 연결. 깃허브 Settings > Emails에 커밋에 쓴 메일을 추가·인증하거나, `user.email`을 noreply 주소로 바꾸고 PR #3·#4 커밋을 다시 만듭니다(아직 합치기 전이라 가능). 확인: `gh api repos/lumos0107/AI_Final_Project/commits/<해시> --jq .author.login`이 `lumos0107`로 나오는지.
2) 팀원 초대, 팀원 쪽 git 이메일 확인(CONTRIBUTING 7장).
3) 팀원이 PR #3·#4를 직접 리뷰. 특히 `04_team_ideas.md`가 자기 뜻과 맞는지 자기 말로 코멘트하고, 고칠 점은 리뷰 반영 커밋으로 남깁니다.
4) 후보 C는 적용하지 않기로 정하고, PR #4 안에서 CONTRIBUTING을 고칩니다. 2장 가.3) 문구, `spike/` 종류, 합치기 마감 시각.
5) PR #3 본문에 "11/17~19 작업을 11/19에 한꺼번에 올림" 한 줄을 넣습니다. 커밋 날짜를 바꾸거나 날짜를 나눠 다시 올리지 마세요. push 시각, PR 기록과 어긋나면 바로 보입니다.

### 나. 1주차 안 (~11/25)

1) 주제 결정 날짜를 못 박습니다(예: 11/22). 이슈 하나에 두 사람이 각자 '본 적 없는 것' 한 문장 정의를 댓글로 남기고 결정합니다.
2) 팀원이 자기 분야 지도(17개)를 자기 커밋으로 올립니다.
3) 사전 시험 `spike/` 2개를 한 명씩 맡고, 결과를 `06_pretest.md`에 정리합니다.
4) 역할 분담을 이슈로 정하고, 팀원도 이슈를 직접 엽니다.
5) PR 양식 1개, 라벨 중복 정리, `05_ai_corrections.md`를 사실 오류(3·4·6번) 중심으로 다시 묶고 대화 발췌를 근거로 붙입니다.

### 다. 나중

1) 첫 테스트와 함께 Actions(2~3주차).
2) Skill·MCP 설정 파일 커밋(쓰기 시작할 때).
3) 주 끝 태그(선택), 기능이 10개를 넘으면 영역 라벨.
4) 12/20: 합치기 마감을 지키고 23:59 전에 `v1.0`. 12/21부터는 README·발표 자료 `docs/` PR만.

## 5. 확인 필요

1) 커밋에 쓴 메일이 계정에 등록되어 있는지는 조회하지 못했습니다(`gh api user/emails`는 user 권한 필요). 커밋 API의 `author`가 `null`이라 등록되지 않은 것으로 추정합니다.
2) 메일을 나중에 추가하면 이미 올린 커밋도 연결되는지: 문서에는 메일 추가 뒤 그래프 반영까지 최대 24시간이라고만 있습니다[2]. 추가한 뒤 4장 가.1)의 명령으로 확인하세요.
3) Contributors 그래프가 공동 작성자를 세는지는 문서[3]에 없습니다. 프로필 기여는 공동 작성자 메일이 계정과 연결되어 있으면 기여로 센다고 되어 있습니다[5].
4) PR 리뷰가 프로필 기여로 잡히는 조건은 문서에 'sometimes count'로만 나옵니다[1].
5) 이 글은 역할을 맡은 검토입니다. 마감 뒤 merge commit을 '기능 코드 커밋'으로 볼지, 기본 브랜치만 보는지 모든 브랜치를 보는지는 공지에 없으니 실제 담당 교수에게 물어보세요.

### 출처

- [1] What counts as a contribution: https://docs.github.com/en/account-and-profile/reference/profile-contributions-reference (기본 브랜치·gh-pages 조건, 메일 연결 조건, 프로필은 author date·저장소 화면은 commit date, PR 리뷰는 sometimes count)
- [2] Why are my contributions not showing up on my profile: https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-github-profile/managing-contribution-settings-on-your-profile/why-are-my-contributions-not-showing-up-on-my-profile (메일 추가 뒤 최대 24시간)
- [3] Viewing a project's contributors: https://docs.github.com/en/repositories/viewing-activity-and-data-for-your-repository/viewing-a-projects-contributors (기본 브랜치만, merge commit 제외, 연결 안 된 메일은 표시 안 됨)
- [4] Approving a pull request with required reviews: https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/approving-a-pull-request-with-required-reviews ("Pull request authors cannot approve their own pull requests.")
- [5] Creating a commit with multiple authors: https://docs.github.com/en/pull-requests/committing-changes-to-your-project/creating-and-editing-commits/creating-a-commit-with-multiple-authors (공동 작성자 메일이 계정과 연결되어야 기여로 셈)
