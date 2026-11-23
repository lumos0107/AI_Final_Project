# 2라운드: 현업 엔지니어

1라운드 결과 4개와 2R 지시를 읽고, 읽기 전용 조회와 문서로 새 사실을 확인했습니다. 대괄호 번호는 맨 끝 출처입니다.

## 1. 다른 검토자 의견에 대한 동의와 반박

### 가. 교수

1) 동의: 이메일 연결, 팀원 기록 0, 합치기 마감, PR #3에 "11/17~19 작업을 11/19에 올림" 한 줄 넣기, 날짜 고쳐 쓰기 금지. "프로필은 author date, 저장소 화면은 commit date"[1]도 맞습니다. 이 사실은 쟁점 7)에도 걸립니다. 작성자를 다시 쓰면 commit date가 다시 쓴 시각으로 바뀌어 저장소 화면에 11/20 커밋으로 보입니다.
2) 반박: 확인 필요 2)에서 "메일을 추가하면 기존 커밋이 연결되는지 문서에 없다"고 했지만, 문서에 있습니다. 연결 안 된 메일은 계정에 추가하라고 하고, 추가하면 기여 그래프를 자동으로 다시 만든다고 적혀 있습니다[2].
3) 보완: Skill·MCP 설정 파일을 커밋하자는 데 동의합니다. 다만 MCP 설정에는 API 키가 들어가는 경우가 많습니다. 키 자리를 비운 예시 파일만 올리고, 키는 `.gitignore`에 넣은 `.env`에 둡니다.

### 나. 팀원

1) 동의: GH007 push 거부[7], 초대 7일 만료, `.gitignore`와 `.env.example`, 리뷰 응답 24시간, PR #3 리뷰 범위 좁히기, 문서에 이름 머리글자 넣기. `.gitignore`는 1라운드에서 제가 놓친 것입니다. 공개 저장소라 우선순위가 높습니다.
2) 반박: "main 보호는 실수로 main에 push해도 막는다"는 팀원(협업자)에게만 맞습니다. 주인은 관리자 예외라 막히지 않습니다[8]. 이슈 양식 2개도 PR 양식 하나로 충분하다고 봅니다.

### 다. GPT

1) 동의:
   - 마감 뒤 허용 범위를 공지 문구대로 "README와 발표 자료"만으로 좁히기
   - squash 설명 문구 바꾸기
   - 큰 기능의 중간 PR은 `Refs #n`, 마지막 PR만 `Closes #n`. 키워드는 기본 브랜치 대상 PR에서만 작동합니다[6].
   - 테스트를 3주차까지 미루지 않기
2) GPT의 확인 필요 두 개는 조회로 풀립니다.
   - 깃허브는 이메일로만 커밋을 계정에 연결합니다[3]. `user.name`은 연결과 관계없습니다.
   - main 보호 API를 보면 `dismiss_stale_reviews`와 `require_last_push_approval`이 모두 false입니다. 승인 뒤에 커밋을 더 올려도 다시 승인받지 않고 합칠 수 있습니다. 2명이라 지금 설정을 유지하는 편이 낫습니다.

## 2. 쟁점별 최종 입장

1) **브랜치 구성:** A를 유지합니다. C에서는 `spike/`, "12/17부터 fix·docs PR만" 규칙, 마지막 `v1.0` 태그를 가져옵니다. 주 끝 태그는 한 줄짜리라 선택으로 둡니다. Release는 v1.0 하나만 만듭니다. A에 반대할 근거는 남지 않았습니다.
2) **버린 사전 시험 코드:** 조건이 맞으면 합칩니다. 합치지 않은 브랜치의 커밋은 기여로 세지 않기 때문입니다[1]. 조건은 셋입니다. `experiments/이름/` 안에만 둘 것, 루트의 의존성 파일을 건드리지 않을 것, 키와 큰 파일이 없을 것. 조건이 안 맞으면 결과만 `06_pretest.md`로 합치고 PR은 닫힌 채로 남깁니다.
3) **squash를 끈 이유:** "작업 단위와 각 커밋의 작성자·날짜를 기본 브랜치에 그대로 남기려고"로 적습니다. merge commit은 Contributors 그래프에서 빠지므로[5] "합치기 = 기여"로 읽히지 않게 합니다.
4) **마감 기준:** "12/20 23:59(한국 시각)까지 main에 합치기 완료"로 합니다.
   - 웹에서 합치면 그 시각에 새 merge commit이 생기고, 저장소 화면은 commit date로 날짜를 셉니다[1]. 0:10에 합치면 12/21 커밋이 됩니다.
   - 커밋 날짜는 자기 PC 시각이라 마음대로 바꿀 수 있습니다. 서버가 기록하는 시각은 PR의 합친 시각과 Activity 화면의 push·병합 기록뿐입니다[9]. 엄격하게 보는 사람은 이쪽을 봅니다.
   - API 시각은 UTC입니다. 12/20 23:59(한국 시각)는 `2026-12-20T14:59Z`입니다.
   - 내부 마감: 기능 PR은 12/19까지 열고 12/20 18:00까지 합칩니다. 버그 PR은 22:00까지, `v1.0` 주석 태그는 23:00입니다. 승인 1명 대기 시간을 계산에 넣은 일정입니다.
   - 마감 뒤에는 `git diff --stat v1.0 main`에 README와 발표 자료만 나오는지가 한 줄짜리 증명이 됩니다. 실제 판정 기준은 교수에게 물어봐야 합니다(확인 필요).
5) **소급 문서화:** PR #3 본문에 소급이라고 한 줄 적습니다. PR #3은 쪼개지 않고 리뷰 범위를 04·05와 공개 여부로 좁힙니다. 쪼개려면 커밋을 다시 써야 하고, 그러면 날짜 문제가 생깁니다(쟁점 7).
6) **팀원 기여 0:** 초대 → 팀원의 이메일 연결 확인(첫 커밋의 `author.login`) → PR #4, #3 순서로 줄 코멘트를 달아 승인 → 팀원 이름으로 이슈 하나와 분야 지도 커밋. "팀이"는 머리글자로 바꿉니다.
7) **이메일: (나)에 더해 앞으로는 noreply를 권합니다.** 즉 gmail을 계정에 추가·인증하고, 전역 `user.email`은 계정의 noreply 주소(Initial commit이 쓴 주소)로 바꿉니다. 커밋은 다시 쓰지 않습니다.
   - 개인정보: (가)로 얻는 비공개 효과가 거의 없습니다. 같은 gmail이 이미 다른 공개 저장소의 커밋에 있습니다(저장소 이름과 커밋 수는 공개본에서 가림). 다시 써서 force push해도 옛 커밋은 SHA 직접 접근이나 PR 기록으로 계속 볼 수 있고, 완전히 지우려면 GitHub Support가 필요합니다[4].
   - 기여 연결: (나)는 이 7개와 다른 저장소의 커밋(수 가림)을 한 번에 연결합니다. 문서는 "추가하면 그래프를 자동으로 다시 만든다, 반영은 최대 24시간"이라고 적습니다[2]. 추가한 뒤 `gh api .../commits/aaa8792 --jq .author.login`이 `lumos0107`인지 확인합니다.
   - (가)의 비용:
     - 7개 모두 SHA가 바뀝니다.
     - PR #3·#4는 열린 채로 남고 `Closes` 연결도 유지되지만, 타임라인에 force push가 기록되고 diff가 바뀝니다[4]. 지금은 리뷰가 0이라 잃을 코멘트는 없습니다.
     - `--amend --author`는 작성 시각(author date)을 유지합니다(`--reset-author`만 새로 씁니다[10]). 커밋 시각(commit date)은 실행 시각으로 바뀝니다. 유지하려면 `--exec`에 `GIT_COMMITTER_DATE="$(git log -1 --format=%aI)"`를 넣어야 합니다. 원래 두 날짜가 같아서 가능한 방법입니다.
     - 작업 브랜치는 보호 대상이 아니라 force push 자체는 됩니다.
   - 덧붙일 것: 계정의 "비공개"와 "명령줄 push 차단"이 켜져 있으면, 맨 위 커밋의 작성자가 비공개 메일인 push는 거부됩니다[7]. noreply로 바꾼 뒤라면 실수를 막는 장치가 되니 켜 둘 만합니다. 계정에 비공개가 켜져 있는지는 확인 필요입니다.
8) **AI 표시:** 작성자는 계정에 연결된 사람이고, Claude는 `Co-Authored-By` 줄에만 둡니다. 작성자가 Claude인 커밋(다른 저장소에 있음, 수 가림)은 합치기 전에 작성자를 바꾸거나 쓰지 않습니다. 공동 작성자도 프로필 기여에 들어갈 수 있으므로[11] Claude 계정이 함께 보이는 것은 정상입니다.
9) **1주차 확장 장치:** PR 양식 하나(무엇을, AI 사용과 틀린 점, 시험 방법), `.gitignore`와 `.env.example`, 겹치는 기본 라벨 정리까지만 넣습니다. Actions는 첫 테스트가 생길 때 넣습니다. 이슈 양식, 영역 라벨, CODEOWNERS는 넣지 않습니다.

## 3. 1라운드에서 고칠 내 주장

1) 5장 1) "문서가 엇갈린다"는 틀렸습니다. "예전 커밋은 연결되지 않을 수 있다"[3]는 문장은 잘못된 이메일(계정에 추가할 수 없는 주소) 항목 바로 뒤에 붙은 문장입니다. 정상 gmail을 추가하는 경우는 [2]가 적용됩니다.
2) 4장 가.1)에서 (가) 재작성을 같은 무게의 선택지로 적었습니다. 다음 세 가지를 빠뜨렸으므로 (나)+noreply로 바꿉니다.
   - 커밋 시각이 바뀌는 문제
   - 옛 SHA가 계속 보이는 문제
   - gmail이 이미 다른 저장소에 공개된 사실
3) 마감 예시 "21:00 기능 합치기"를 쟁점 4)의 일정으로 바꿉니다. "판 번호 태그 필요 없음"은 "주 끝 태그 선택"으로, "Actions 3주차"는 "첫 테스트가 생길 때"로 바꿉니다.
4) `.gitignore`가 빠졌던 것을 더합니다. 주인 계정이 main에 바로 push할 수 있는지는 여전히 시험하지 않은 추정입니다(확인 필요).

## 4. 최종 우선순위

### 가. 지금 당장 (최대 5개)

1) gmail을 계정에 추가·인증합니다. 전역 `user.email`을 noreply로 바꾸고 `author.login`으로 확인합니다.
2) 팀원을 초대하고 이메일 연결을 확인합니다. 팀원이 PR #4·#3을 리뷰·승인한 뒤 합칩니다.
3) PR #4에서 CONTRIBUTING을 고칩니다.
   - 기여 설명 문구, 7장 확인 방법
   - 합치기 마감과 마감 뒤 허용 범위(README·발표 자료)
   - squash 이유
   - 작성자 규칙, `spike/`, 관리자 예외의 용도
4) PR #3 본문에 소급 한 줄과 리뷰 범위를 적습니다.
5) C는 적용하지 않기로 정합니다.

### 나. 1주차 안 (~11/25)

PR 양식 하나, `.gitignore`와 `.env.example`(코드 첫 커밋 전), 라벨 정리, 두 사람이 함께 한 번 돌려 보는 PR 순환, `spike/` 사전 시험 2개(한 명씩)

### 다. 나중

첫 테스트와 함께 Actions. 12/19 기능 PR 열기 마감, 12/20 18:00·22:00·23:00 일정, `v1.0` 태그와 Release. 12/21부터는 README·발표 자료 PR만. 마감 판정 기준은 교수에게 미리 묻습니다.

### 출처

1. https://docs.github.com/en/account-and-profile/reference/profile-contributions-reference (프로필 author date, 저장소 commit date, 기본 브랜치)
2. https://docs.github.com/en/account-and-profile/reference/why-are-my-contributions-not-showing-up-on-my-profile ("rebuilt automatically when you add the new address", 최대 24시간)
3. https://docs.github.com/en/pull-requests/committing-changes-to-your-project/troubleshooting-commits/why-are-my-commits-linked-to-the-wrong-user (이메일로 연결, Invalid email 항목 뒤 "Old commits might not be linked")
4. https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository (force push 뒤에도 SHA·PR로 접근 가능, SHA 변경과 PR diff 변화)
5. https://docs.github.com/en/repositories/viewing-activity-and-data-for-your-repository/viewing-a-projects-contributors
6. https://docs.github.com/en/issues/tracking-your-work-with-issues/using-issues/linking-a-pull-request-to-an-issue
7. https://docs.github.com/en/account-and-profile/how-tos/email-preferences/blocking-command-line-pushes-that-expose-your-personal-email-address
8. https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches
9. https://docs.github.com/en/repositories/viewing-activity-and-data-for-your-repository/using-the-activity-view-to-see-changes-to-a-repository
10. https://git-scm.com/docs/git-commit (`--reset-author`가 작성 시각을 새로 씀)
11. https://docs.github.com/en/pull-requests/committing-changes-to-your-project/creating-and-editing-commits/creating-a-commit-with-multiple-authors
