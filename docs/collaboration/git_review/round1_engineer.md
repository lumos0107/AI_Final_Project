# 1라운드: 현업 엔지니어

기준일 2026-11-19. 자료 전체를 읽고 저장소는 읽기 전용 명령으로만 확인했습니다. 대괄호 번호는 6장 출처입니다.

## 1. 지금까지 한 일 평가

### 가. 잘한 점

1) merge commit만 허용: 작업 브랜치 커밋이 같은 SHA로 main에 들어가 작성자와 날짜가 그대로 남고[4], 프로필 그래프는 author date로 셉니다[1]. 기간 분포 기준에 맞습니다.
2) `ai-mistake` 라벨과 `05_ai_corrections.md`: 채점 기준 3 "AI가 틀렸을 때"의 증거를 작업 중에 모읍니다. 끝난 뒤 기억으로 만드는 것보다 싸고 정확합니다.
3) 영구 브랜치 하나, 짧은 작업 브랜치, 자동 삭제: 2명 규모에 맞고, `Closes #n`이 작동하는 조건(기본 브랜치 대상 PR)[6]도 맞습니다.

### 나. 문제점

1) **(상) 지금까지 커밋 7개가 누구의 기여로도 잡히지 않습니다.** `gh api .../commits/aaa8792 --jq .author.login` 결과가 null입니다(bafa728도 null, 웹에서 만든 Initial commit만 lumos0107). 이 PC 전역 `user.email`이 개인 gmail이고, 같은 주소의 다른 저장소 커밋 43개도 모두 null입니다. 기여 그래프와 Insights는 계정에 연결된 이메일의 커밋만 셉니다[1][5]. main은 관리자에게도 force push 금지이므로[9] PR #3·#4를 **합치기 전에** 고쳐야 합니다.
2) **(상) 팀원이 저장소에 없습니다.** 기록(이슈 2, PR 2, 커밋 7)이 모두 한 사람 것이고 초대 대기도 없습니다. PR 작성자는 자기 PR을 승인할 수 없어[7] 지금 PR #3·#4는 주인이 보호를 건너뛰어야만 합칠 수 있습니다. PR 리뷰도 기여로 셈하므로[1] 두 PR 리뷰를 팀원의 첫 기여로 쓰면 됩니다.
3) **(중) 보호 규칙이 두 사람에게 다르게 작동합니다.** enforce_admins가 꺼져 있으면 규칙이 관리자에게 적용되지 않고[8], 승인 없이 보호 브랜치에 합치는 것은 주인만 할 수 있으며 협업자를 관리자로 올릴 방법도 없습니다[10]. 주인(과 주인 계정으로 도는 Claude Code)은 승인 없이 합칠 수 있고, 팀원은 늘 주인 승인을 기다립니다. 마감 주 밤에 주인이 없으면 막힙니다.
4) **(중) CONTRIBUTING.md 설명 일부가 부정확합니다.**
   - 2장 가.3) "main에 들어간 커밋만 센다": 이름과 상관없이 기본 브랜치(또는 gh-pages)이고, 이슈·PR 열기와 PR 리뷰도 셈하며, 연결된 이메일이어야 합니다[1]. 묵힌 브랜치 커밋도 합치면 원래 날짜로 나타나므로[1] "분포가 사라진다"는 근거는 약합니다. 짧게 쓰는 이유는 충돌과 리뷰 크기입니다.
   - 7장: 깃허브는 이메일만으로 계정에 연결합니다[3]. `user.name`의 "깃허브 아이디" 주석은 오해를 부르고, `git config` 출력만으로는 등록 여부를 알 수 없습니다(주인 본인이 통과 못 함). 커밋 화면의 작성자 링크나 위 API로 확인해야 합니다.
   - 6장 1) "23:59까지만 커밋": 웹에서 합치면 합친 시각에 merge commit이 생깁니다. 23:50 커밋을 0:10에 합치면 main에 12/21 커밋이 남습니다. 기준은 "합치기 완료"여야 합니다. 병합 기록은 Activity 화면에 남습니다[11].
5) **(중) 커밋 6개가 1초 안(17:00:19~20)에 찍혔습니다.** 분포 기준에 보탬이 없고 기계적으로 쪼갠 흔적으로 읽힙니다. 하루치라 피해는 작지만, AI가 몰아 만들고 한 번에 커밋하는 습관이 기능 개발로 이어지면 직접 손해입니다. 날짜를 고쳐 쓰는 방법은 Activity의 실제 push 기록[11]과 어긋나니 쓰지 마십시오.
6) **(중, 예방) 작성자가 Claude인 커밋은 학생 기여가 아닙니다.** 다른 저장소 커밋 100개 중 57개가 작성자 `Claude <noreply@anthropic.com>`이고 깃허브 계정 `claude`로 연결됩니다. 이 저장소는 사람이 작성자, Claude는 `Co-Authored-By`에만 있어 괜찮습니다. 이 방식을 규칙에 적어야 합니다.
7) **(하)** PR #3(9파일 1,163줄)은 CONTRIBUTING 4장 1) "10분 안에 읽을 크기"를 스스로 어깁니다. 기본 라벨(bug, enhancement, documentation)이 새 라벨(fix, feat, docs)과 겹칩니다.

## 2. 브랜치 구성 권고

### 가. 결론

**후보 A(GitHub Flow)를 유지**하고 작은 것 셋만 붙입니다. C는 적용하지 않고, B는 검토할 이유가 없습니다.

### 나. 이유

1) Git Flow는 여러 판을 동시에 유지·지원할 때의 방식입니다. 원저자도 2020년에 그런 필요가 없는 웹 앱이면 GitHub Flow 같은 단순한 방식을 권했습니다[13]. 이 과제는 마감 판 하나만 평가받습니다.
2) 채점 항목(커밋 내용, 분포, 이슈·PR 기록)은 브랜치 모델과 무관합니다. C의 주간 develop→main PR은 merge commit만 만들고, merge commit은 Insights 기여자 그래프에서 빠집니다[5]. 승인 대기만 주마다 늘어납니다.
3) C의 숨은 함정
   - 기본 브랜치를 develop으로 했다가 12/20 뒤 main으로 되돌리기: 기여 집계, `Closes` 키워드, 새 PR 대상이 모두 기본 브랜치를 따라 움직이고[1][6], 깃허브도 변경이 모든 협업자에게 영향을 준다고 경고합니다[2]. 마감 직전에 건드릴 설정이 아닙니다.
   - release/1.0을 두 곳에 합칠 때 자동 삭제가 켜져 있으면 main 쪽을 먼저 합친 순간 브랜치가 지워질 수 있고, 지워진 브랜치를 쓰는 열린 PR은 닫힙니다[12](실제 동작은 5장).
   - develop 보호를 따로 걸어야 하고, 팀원이 "어디서 갈라 어디로 합치나"를 헷갈립니다. 숙련도를 모르는 팀원에게 가장 큰 비용입니다.
4) C의 목적은 A에서도 거의 공짜로 됩니다. 주차별 판은 마일스톤이 이미 대신하고, 기능 동결은 "12/17부터 fix/·docs/만" 한 줄, 사전 시험은 `spike/` 브랜치와 `experiments/` 폴더를 main에 PR로 합치면 됩니다(기본 브랜치에 들어가야 기여로 셈[1]). 제출판은 12/20 main에 주석 태그 `v1.0`과 Release 하나면 됩니다.

### 다. A에 붙일 것

1) 브랜치 종류에 `spike/` 추가(코드는 `experiments/` 안에만)
2) 마감 규칙을 합친 시각 기준으로: 예) 12/20 21:00 기능 PR 합치기 끝, 이후 fix만, 23:30 `v1.0` 태그
3) PR 양식 하나(3장)

### 라. 리뷰 규칙

승인 1명은 유지를 권합니다. 팀원 참여를 강제하고 리뷰 자체가 기여 기록이 됩니다. 1장 나.3)의 비대칭은 CONTRIBUTING에 적어 둡니다. 팀원이 활동을 시작하면 enforce_admins를 켜서 주인 계정의 실수 push를 막는 것도 고려할 만합니다. 급할 때는 주인이 바로 끌 수 있습니다.

## 3. 확장성

1) 2명·4주에서 막히는 곳은 브랜치 수가 아니라 기여 귀속(이메일, 작성자), 리뷰 대기, 마감 직전 합치기입니다. 브랜치 구조는 A로 충분합니다.
2) C의 확장성 항목
   - 기능 = 이슈 = 브랜치: 유지. 오타나 한 줄 수정은 이슈 없이 PR만 허용합니다. 매번 강제하면 다른 과목과 겹치는 주에 안 지켜집니다.
   - PR 양식: 하나만 둡니다. 칸은 "무엇을 / AI를 어떻게 썼나 / AI가 틀린 곳 / 어떻게 시험했나". 발표 필수 요소(AI 활용, 테스트 방법과 결과, 어려웠던 문제)가 PR마다 쌓입니다.
   - Actions: 테스트가 생기는 3주차에 "테스트 실행" 하나만.
3) 지나친 것: develop, release 브랜치, 주차별 v0.x 판과 Release, 기본 브랜치 바꾸기, 이슈 양식 4종, CODEOWNERS(2명에게 의미 없음), 영역 라벨과 커밋 범위(구조가 생긴 뒤에도 필요할 때만), 문서 PR까지 "브랜치를 받아 실행" 규칙.

## 4. 우선순위

### 가. 지금 당장 (PR #3·#4를 합치기 전)

1) 이메일 연결: 깃허브 Settings > Emails에 지금 쓰는 gmail을 추가·인증하거나, noreply 주소로 바꾸고 아직 안 합친 두 작업 브랜치의 커밋 작성자를 고쳐 force push(작업 브랜치는 보호 대상 아님). 전역 설정이라 다른 저장소도 같습니다. `.author.login`이 `lumos0107`로 나오는지 확인합니다.
2) 팀원 초대 → 팀원 이메일 확인 → 팀원이 PR #3·#4 리뷰·승인. 주인 혼자 건너뛰어 합치지 않습니다.
3) PR #4를 합치기 전에 CONTRIBUTING 수정: 2장 가.3), 7장 확인 방법, 6장 마감 기준, "작성자는 사람, Claude는 Co-Authored-By로만", `spike/`, 보호 규칙 비대칭.
4) 후보 C는 적용하지 않기로 결정.

### 나. 1주차 안 (~11/25)

1) PR 양식 하나, 겹치는 기본 라벨 정리
2) 두 사람이 작은 문서 하나로 이슈→브랜치→PR→리뷰→합치기를 한 번 같이 돌리고, 팀원 커밋이 팀원 계정에 연결되는지 확인
3) 사전 시험은 `spike/`와 `experiments/`로
4) (선택) enforce_admins 켜기

### 다. 나중

1) 3주차: 테스트가 생기면 Actions 하나
2) 12/17 기능 동결 → 12/20 21:00 합치기 마감, `v1.0` 주석 태그와 Release → 12/21부터 README·발표 자료 PR만

## 5. 확인 필요

1) gmail이 계정에 없는지, 추가됐지만 미인증인지 모릅니다(gh 토큰에 user 범위가 없어 조회 실패). 주소를 추가하면 기존 커밋이 다시 연결되는지도 문서가 엇갈립니다("그래프가 자동으로 다시 만들어진다"[2], "예전 커밋은 연결되지 않을 수 있다"[3]). 추가 후 API로 확인하고, 안 되면 합치기 전에 작성자를 고쳐 씁니다.
2) 자동 삭제가 다른 열린 PR의 head 브랜치도 지우는지 문서에서 찾지 못했습니다(C의 release 함정).
3) enforce_admins가 꺼졌을 때 주인이 main에 바로 push할 수 있는지는 [8]로 추정했고, 쓰기 금지라 시험하지 않았습니다.
4) 교수가 기여도를 무엇(프로필 그래프, Insights, 커밋 목록, Activity)으로 보는지 모릅니다. 권고는 넷 모두에서 안전한 쪽으로 잡았습니다.
5) 다른 저장소의 Claude 작성 커밋이 어떤 도구에서 생겼는지 확인하지 않았습니다.

## 6. 출처

### 가. 명령 결과 (11/19, 읽기 전용)

- `git log --all --graph`: 문서 커밋 6개 17:00:19~20, 작성자 이메일 개인 gmail(Initial commit만 noreply)
- `gh api repos/lumos0107/AI_Final_Project/commits/{aaa8792,bafa728,c81c2b3}`: author.login null, null, lumos0107
- `git config --show-origin user.email`: 전역 `~/.gitconfig`에 개인 gmail
- `gh api repos/lumos0107/<다른 저장소>/commits?per_page=100`: null(gmail) 43개, claude 57개
- `gh api .../branches/main/protection`: enforce_admins false, 승인 1명, force push·삭제 금지. rulesets 없음, 초대 없음, 협업자 lumos0107만
- `gh pr view 3`: 9파일 1,163줄, 리뷰 0

### 나. 문서

1. 기여로 세는 것(기본 브랜치, 연결된 이메일, PR 리뷰, author date): https://docs.github.com/en/account-and-profile/reference/profile-contributions-reference
2. 기여가 안 보이는 이유(기본 브랜치 변경 경고, 주소 추가 시 그래프 재생성): https://docs.github.com/en/account-and-profile/reference/why-are-my-contributions-not-showing-up-on-my-profile
3. 커밋-계정 연결은 이메일로, 예전 커밋은 연결 안 될 수 있음: https://docs.github.com/en/pull-requests/committing-changes-to-your-project/troubleshooting-commits/why-are-my-commits-linked-to-the-wrong-user
4. 병합 방식(merge commit은 전체 역사 보존, rebase는 커미터·SHA 새로): https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/incorporating-changes-from-a-pull-request/about-pull-request-merges
5. Insights 기여자 그래프(merge commit 제외, 기본 브랜치, 연결 이메일): https://docs.github.com/en/repositories/viewing-activity-and-data-for-your-repository/viewing-a-projects-contributors
6. `Closes`는 기본 브랜치 대상 PR에서만: https://docs.github.com/en/issues/tracking-your-work-with-issues/using-issues/linking-a-pull-request-to-an-issue
7. PR 작성자는 자기 PR 승인 불가: https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/approving-a-pull-request-with-required-reviews
8. 보호 규칙은 기본적으로 관리자 제외: https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches
9. force push·삭제 금지는 관리자 포함: https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/managing-a-branch-protection-rule
10. 개인 계정 저장소 권한(승인 없이 보호 브랜치 병합은 주인만): https://docs.github.com/en/account-and-profile/reference/permission-levels-for-a-personal-account-repository
11. 저장소 Activity 화면(push, 병합 기록): https://docs.github.com/en/repositories/viewing-activity-and-data-for-your-repository/using-the-activity-view-to-see-changes-to-a-repository
12. 열린 PR이 쓰는 브랜치를 지우면 PR이 닫힘: https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-and-deleting-branches-within-your-repository
13. Git Flow 원저자의 2020년 덧붙임: https://nvie.com/posts/a-successful-git-branching-model/
