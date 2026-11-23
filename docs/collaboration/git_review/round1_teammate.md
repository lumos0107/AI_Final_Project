# 1라운드: 팀원 (초보 가정)

> 가정: "Git은 add, commit, push만 해 봤고 PR 리뷰와 브랜치 전략은 처음이며, 다른 과목 과제도 많은 팀원"을 가정한 시험입니다. 실제 팀원의 숙련도는 모릅니다. 저장소는 읽기만 했습니다(`git log --all`, `git show`, `git diff --stat`).

## 1. 지금까지 한 일 평가

### 잘한 점
- 규칙마다 이유가 적혀 있습니다. 특히 이메일 확인(3장 7장)은 초보가 가장 놓치기 쉬운데 첫날 짚어 줍니다.
- `ai-mistake` 라벨과 "AI가 틀린 커밋은 본문에 한두 줄"(3장 3-2)은 채점 3번 "AI가 틀렸을 때"(2장)로 바로 이어져, 발표 자료를 따로 모을 수고가 줄어듭니다.
- main 보호와 승인 1명(5장)은 초보에게 안전망입니다. 실수로 main에 push해도 막힙니다.

### 문제점
1. **[상] 내가 오기 전에 기록이 한 사람에게 쌓였습니다.** 커밋 8개, 이슈 2개, PR 2개가 모두 lumos0107입니다(5장). 개인 평가는 "이슈와 PR 기록"과 "고른 분포"를 봅니다(2장). 1주차 목표에 "역할 분담"이 있지만(3장 6장) CONTRIBUTING에 일을 나누는 방법(이슈 담당자 지정 등)이 없습니다.
2. **[상] 주제 도출 문서에 "누가"가 없습니다.** 02·05의 판단이 모두 "팀이"이고 05의 "누가 알아챘나" 칸도 "팀" 아니면 "AI"입니다. 내 의견은 내 몫으로 남지 않고, 참여하지 않았다면 "팀"이 내 몫처럼 읽혀 "역할 분담"(2장)과 동료평가에서 곤란합니다. PR #3은 리뷰어에게 "내가 한 말이 다르게 적힌 곳"을 확인하라는데(5장) 표시가 없으면 확인할 수 없습니다. 칸에 이름 머리글자만 넣으면 됩니다.
3. **[중] 첫 리뷰 요청 PR #3이 자기 규칙보다 큽니다.** 9개 파일 1,163줄, 그중 심사위원 원문이 643줄입니다(`git diff --stat`). CONTRIBUTING 4-1은 "10분 안에 읽을 크기"입니다. 이러면 대충 Approve를 눌러 리뷰 기록이 모양만 남습니다. PR 본문에 리뷰 범위(04·05와 공개 여부)를 적으면 풀립니다.
4. **[중] 승인 규칙이 두 사람에게 다르게 작동합니다.** 관리자 예외(5장)라 주인은 리뷰 없이 합칠 수 있고[1], 나는 상대 승인이 있어야 합칩니다(작성자는 자기 PR 승인 불가[2]). 주인이 바쁘면 내 작업이 기본 브랜치에 못 들어가 기여로 잡히지 않고[3], 마감 직전이면 12/20을 넘깁니다. 리뷰 응답 기한과 마지막 코드 PR 기한이 규칙에 없습니다.
5. **[중] 커밋 6개가 같은 시각(11/19 17:00)입니다(5장).** "고른 분포"(2장)에 도움이 안 됩니다. 지난 이력은 고치지 말고(초보에게 force push는 더 위험) "작업한 날 push"를 규칙에 넣으면 됩니다.
6. **[중] 초보가 막힐 곳이 안내에 없습니다.** main push 거부 시 할 일, 이메일 비공개 계정의 GH007 push 거부[4], 충돌 해결, 리뷰하는 법과 PR 브랜치 받는 법(4-2는 "직접 받아 실행"만 적음), 초대 7일 만료[5].
7. **[중] CONTRIBUTING 2-가-3 문구가 부정확합니다.** "main"이 아니라 "기본 브랜치(또는 gh-pages)"의 커밋을 셉니다[3]. Insights의 Contributors 그래프는 merge commit을 세지 않으므로[6] Merge 버튼은 기여 숫자를 늘리지 않는다고 적어 두면 오해가 줄어듭니다.
8. **[하] 그 밖에.** 기본 라벨 `bug`·`documentation`·`enhancement`가 `fix`·`docs`·`feat`와 겹칩니다(5장 라벨 15개). 공개 저장소인데 `.gitignore`가 없어 `.env`(API 키)를 올리기 쉽습니다. 내가 Claude Code 말고 다른 AI 도구를 쓰면 사용 기록을 남길 형식이 없습니다(채점 2번).

## 2. 브랜치 구성 권고

**후보 A를 유지하고, C의 좋은 점 셋만 브랜치 없이 가져오기를 권합니다.**

1) A는 "main에서 갈라 main으로 PR" 하나만 외우면 되고, CONTRIBUTING 1장 명령 예시가 그대로 맞습니다.
2) C가 팀원에게 무거운 이유
   - 기본 브랜치가 develop이면 1장 예시(`git switch main`)를 다 바꿔야 하고, main에서 갈라 PR에 엉뚱한 변경이 섞이기 쉽습니다.
   - 주마다 develop → main PR과 release 이중 병합이 생기고, 그때마다 내가 승인해야 합니다. 코드 없는 PR이라 "커밋된 코드의 내용"(2장)에 보탬이 적습니다.
   - 가장 바쁜 마감 주에 "버그를 release에 고치나 develop에 고치나"를 판단해야 합니다.
   - `Closes #번호`는 PR이 기본 브랜치를 향할 때만 작동합니다[7]. release → main PR이나 기본 브랜치를 되돌린 뒤에는 이슈가 자동으로 닫히지 않습니다.
3) B는 hotfix까지 있어 C보다 무겁습니다.
4) C에서 가져올 것: ① 주 끝에 main에 태그 `v0.1`~`v1.0`(주인이 붙이면 됨) ② 종류 표에 `spike/` 한 줄, 코드는 `experiments/` 안에만, 버린 시험도 PR로 남김 ③ release 브랜치 대신 "12/17부터 feat PR 안 받음, 마지막 코드 PR은 12/19까지" 규칙.

## 3. 확장성

| 장치 (6장 다) | 팀원에게 | 권고 |
|---|---|---|
| 기능 = 이슈 = 브랜치 하나 | 도움. 내 몫이 이슈 단위로 보임 | 유지 |
| `spike/` | 도움. 1주차에 내 몫이 생김 | 1주차 |
| PR 양식 1개 | 가장 도움. 빈칸만 채우면 됨(무엇을, 확인 방법, AI 사용과 틀린 점) | 내 첫 PR 전 |
| 이슈 양식 4종 | 고르는 것부터 부담 | 기능, 사전 시험 2개만 |
| 영역 라벨, 커밋 범위 | 짐. 라벨이 이미 15개, 2명이라 이득 적음 | 나중, 필요하면 |
| release 브랜치 | 짐 | 규칙으로 대신 |
| Actions | 지금은 불필요. 테스트가 생기면 "테스트 방법과 결과"(2장) 근거 | 3주차 검토 |
| CODEOWNERS | 2명이라 의미 없음 | 안 함 |

## 4. 우선순위 (지금 당장 / 1주차 안 / 나중)

### 지금 당장
- 주인: ① 팀원 초대 ② C는 적용하지 않기로 결정(적용하면 PR #3·#4 대상 변경과 문서 수정이 먼저 생김) ③ PR #3에 리뷰 범위 적기, 05 "누가" 칸에 이름 넣을지 결정.
- **팀원 첫날 할 일 (1시간 안쪽)**
  1. 초대 수락(7일 안).
  2. `git clone` 뒤 `git config user.email`이 GitHub Settings > Emails 주소와 같은지 확인. 명령줄 push 차단이 켜져 있으면 noreply 주소로.
  3. PR #4부터 리뷰. 줄 코멘트 1~3개(지키기 어려운 규칙, 리뷰 기한, 일 나누는 법)를 남기고 Approve. 리뷰 제출은 프로필 기여에 들어갈 수 있습니다[8].
  4. PR #3은 04·05와 공개 여부만 보고 리뷰.
  5. 내 이름으로 이슈 하나(예: 사전 시험 B), 1주차 마일스톤, 담당자 나.

### 1주차 안 (~11/25)
1. CONTRIBUTING 보완: 리뷰 응답 24시간, 마지막 코드 PR 12/19, 담당자로 일 나누기, 2-가-3 문구, 라벨 5개만, 오류 대처. 오류 대처는 내가 막힌 곳을 직접 적어 PR로 내면 첫 커밋 연습도 됩니다.
2. PR 양식 1개, 이슈 양식 2개.
3. 사전 시험 2개를 한 명씩 맡아 이슈 → `spike/` → PR. 결과는 `06_pretest.md`에 각자 절로.
4. 주제가 정해지면 기능 목록을 이슈로 쪼개 담당자를 반씩.
5. 코드 시작 전 `.gitignore`와 `.env.example`. 11/25에 `v0.1` 태그.

### 나중
Actions(3주차, 테스트가 생기면), 영역 라벨(필요해지면), 12/20 `v1.0` 태그, `ai-mistake` 모아 발표 자료.

## 5. 확인 필요
1. 교수가 기여도를 무엇으로 보는지(Contributors 그래프, 프로필 잔디, 커밋 목록). Contributors 그래프는 merge commit을 빼고[6], 리뷰는 프로필 기여에 "경우에 따라" 들어갑니다[8].
2. "12/21 0시부터 기능 코드 커밋 금지"가 커밋 시각 기준인지 합친 시각 기준인지. 12/20 밤 승인 대기 PR이 12/21에 합쳐지면 위반인지 교수에게 물어볼 일입니다.
3. `Co-Authored-By: Claude` 때문에 기여자 목록에 Claude 계정이 보이는지. 공식 문서를 못 찾았고, 엉뚱한 계정에 연결된다는 비공식 보고만 있습니다[9].
4. 주제 도출에 팀원이 실제로 참여했는지, 04의 "아이디어를 낸 팀원"이 누구인지는 자료에 없습니다.

### 출처
- [1] GitHub Docs, About protected branches https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches
- [2] GitHub Docs, Approving a pull request with required reviews https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/approving-a-pull-request-with-required-reviews
- [3] GitHub Docs, Why are my contributions not showing up on my profile? https://docs.github.com/en/account-and-profile/reference/why-are-my-contributions-not-showing-up-on-my-profile
- [4] GitHub Docs, Blocking command line pushes that expose your personal email address https://docs.github.com/en/account-and-profile/how-tos/email-preferences/blocking-command-line-pushes-that-expose-your-personal-email-address
- [5] GitHub Changelog 2020-02-05, 초대 7일 만료 https://github.blog/changelog/2020-02-05-self-expiring-repository-and-organization-invitations/
- [6] GitHub Docs, Viewing a project's contributors https://docs.github.com/en/repositories/viewing-activity-and-data-for-your-repository/viewing-a-projects-contributors
- [7] GitHub Docs, Linking a pull request to an issue https://docs.github.com/en/issues/tracking-your-work-with-issues/using-issues/linking-a-pull-request-to-an-issue
- [8] GitHub Docs, Profile contributions reference https://docs.github.com/en/account-and-profile/reference/profile-contributions-reference
- [9] 비공식 사용자 보고, Incorrect Co-Author Attribution for Claude Code Commits https://claudeissues.com/issue/1653-incorrect-co-author-attribution-for-claude-code-commits-to-github
