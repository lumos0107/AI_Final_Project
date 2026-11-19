# 팀 아이디어와 비슷한 사례 (11/19)

6차까지는 주로 AI가 후보를 냈습니다. 그 뒤 팀이 직접 아이디어 2개를 냈고, 비슷한 사례가 있는지 찾아보았습니다.

## 1. 아이디어 1: 바이브 코딩 용어 정리집

### 가. 팀이 낸 내용

1) 바이브 코딩을 하는 사람 중에는 비전공자나 다른 분야에 도전하는 사람이 많습니다.
2) 이들은 용어를 몰라서 "저기 위에 그거 바꿔 줘", "역동적으로"처럼 두루뭉술하게 AI에게 일을 시킵니다. 그러면 결과가 나빠지거나 오래 걸립니다.
3) 업계 사람은 웹·앱 부품 이름, 디자인 과정, 카메라 기법, 물체가 움직이는 방식을 부르는 이름을 알아서 AI에게 의도를 정확하고 빠르게 전합니다.
4) 이런 이름을 분야별로 모아, 비전공자가 보고 골라 쓸 수 있게 하는 정리집을 만든다.

### 나. 계기가 된 영상

- [업계에 있는 사람들이 AI를 '잘 쓰는' 이유](https://www.youtube.com/watch?v=zWHoU2KRAiU) (2026.10.13)
- [전문가처럼 만드는 모션 용어 5가지 알려줄게!](https://www.youtube.com/shorts/97OpNILqrnw)
- [화려한 모션 그래픽 TOP 5, 이름만 알면 AI가 만들어 줍니다](https://www.youtube.com/shorts/NRILp2qsb_Q)

### 다. 분야 지도

아이디어를 낸 팀원이 2026년 10월에 개인적으로 정리해 둔 분야 지도(17개) 중 일부입니다. "무엇을 만들 때 막히는지"를 기준으로 나눴습니다.

| 분야 | 막연하게 말할 때 | 알면 좋은 용어 |
|---|---|---|
| 화면 요소 | "알림 띄워 줘", "옆에서 메뉴 나오게" | 토스트, 모달, 드로어, 바텀 시트, 아코디언, 캐러셀 |
| 화면 동작 | "부드럽게", "살아 있는 느낌" | 이징, 트랜지션, 스태거, 패럴랙스, 스켈레톤 로딩 |
| 디자인과 배치 | "깔끔하게", "세련되게" | 여백, 그리드, 시각적 위계, 행간과 자간 |
| 게임 느낌 | "타격감 있게", "조작감 좋게" | 히트스톱, 화면 흔들림, 넉백, 코요테 타임, 입력 버퍼 |
| 카메라와 영상 연출 | "영화처럼", "멋있게 찍어 줘" | 로우 앵글, 돌리, 트래킹, 오빗, 돌리 줌 |
| 고치기와 되돌리기 | "안 돼요", "아까로 돌려 줘" | 에러 메시지, 재현 단계, 콘솔, 커밋, 롤백 |

### 라. 비슷한 사례

| 분야 | 이미 있는 것 | 비어 있는 곳 |
|---|---|---|
| 웹·앱 부품 | Name That UI(2026.7, 자기 말로 설명하면 부품 이름과 코딩 AI에게 줄 문장을 알려 주는 보이는 사전, Claude용 Skill도 있음), 위키독스 『그거 있잖아 그거! 바이브코딩 실전 용어 가이드』(무료), 크몽 『그림으로 찾는 UI 요소 사전』(유료, 61개), UI Guideline(유료, 부품 60개 이상) | 거의 없음 |
| 카메라 무빙 | Carat 블로그 용어 정리, Atlabs 「카메라 무빙 프롬프트 42가지」 등 글이 많음 | 거의 없음 |
| 화면 동작과 모션 | Emil Kowalski의 Claude Skill 「animation vocabulary」, 모션 디자인 용어집(AI용 아님) | 보이는 예시와 한국어 자료 |
| 게임 느낌 | Claude Skill 「game-feel」, 게임 느낌 체크리스트 30가지 | 보이는 예시와 한국어 자료 |

### 마. 효과에 대한 근거

| 자료 | 내용 |
|---|---|
| daisyUI 안내 | 부품 이름을 정확히 쓰면 프롬프트가 짧아지고, AI가 고치는 코드 양도 줄어든다고 함 |
| NAACL 2025 「Substance Beats Style」 | 초보 학생의 코딩 프롬프트를 실험해 보니, 전문 용어를 쓰느냐보다 프롬프트에 정보가 얼마나 담겼느냐가 성공을 갈랐음 |

두 번째 논문은 발표장에서 반론으로 나올 수 있습니다. 반대로 보면 "스태거" 한 단어에는 "여러 개가, 하나씩 차례로, 조금씩 늦게"라는 정보가 담겨 있습니다. 이름을 아는 것이 정보를 담는 지름길이라는 점을 보여 줄 수 있습니다. "이름을 알면 AI가 더 잘 만든다"는 주장을 직접 재 본 사례는 찾지 못했습니다.

### 바. 지금까지의 판단

1) 웹·앱 부품만 다루면 이미 있는 것과 거의 같습니다.
2) 남은 틈은 두 가지입니다.
   - 모션과 게임처럼 아직 보이는 예시가 없는 분야
   - "이름을 알면 정말 빨라지나"를 숫자로 재 보는 것
3) 정리집이 내용 중심이라 MCP나 Skill 같은 AI 기술 점수가 약해질 수 있습니다. 정리집을 Skill이나 MCP로 만들어 AI 대화 안에서 쓰게 하는 방법을 검토하고 있습니다.

## 2. 아이디어 2: 세금 도우미

### 가. 팀이 낸 내용

1) 홈택스는 쓰기 어려워서, 사람들은 세무사나 삼쩜삼, 토스 같은 대행 서비스에 수수료를 내고 맡깁니다.
2) 만드는 일 자체는 그렇게 어려워 보이지 않습니다.
3) 한국인뿐 아니라 외국인에게는 더 어렵습니다. 이 관점도 괜찮아 보입니다.

### 나. 비슷한 사례와 걸리는 점

| 내용 | 뜻 |
|---|---|
| 국세청 원클릭 환급이 2025년 3월 31일부터 무료로 운영 중. 삼쩜삼 수수료는 환급액의 10~20% | 한국인 대상 "수수료 없는 환급"은 국세청이 이미 함 |
| 외국인용으로 국세청 다국어 안내서(영어, 중국어, 베트남어)와 영어 상담 전화가 있음 | 외국인용 환급 도우미 앱은 찾지 못함. 검색이 놓쳤을 수 있음 |
| 2026년 6월 24일 개정 세무사법 시행: 자격 없이 세무대리처럼 보이게 광고하는 것을 금지 | "대신 신고해 주는" 기능은 법적으로 위험함. 안내만 하는 도구로 한정해야 함 |
| 삼쩜삼은 홈택스 자료 수집 문제로 개인정보보호법 위반 혐의로 검찰에 송치됨 | 개인 세금 자료를 다루는 방식이 문제가 될 수 있음 |

### 다. 지금까지의 판단

1) 어려운 부분은 코드보다 세법을 정확하게 맞추는 일, 틀렸을 때의 책임, 홈택스 자료를 가져오는 방법입니다.
2) 한국인 쪽은 국세청 무료 서비스가 이미 있습니다. 외국인 쪽에 빈자리가 있을 수 있지만, 법과 개인정보 위험이 큽니다.

## 3. 출처

### 가. 아이디어 1
- [Name That UI 소개 (디자인 나침반)](https://designcompass.org/2026/08/25/namethatui-visual-dictionary/)
- [namethatui Skill (skills.sh)](https://www.skills.sh/jpcaparas/skills/namethatui)
- [그거 있잖아 그거! 바이브코딩 실전 용어 가이드 (위키독스)](https://wikidocs.net/book/19160)
- [그림으로 찾는 UI 요소 사전 (크몽)](https://kmong.com/gig/822056)
- [UI Guideline](https://www.everydev.ai/tools/ui-guideline)
- [daisyUI: 글로 UI 만들기 안내](https://daisyui.com/ai/generate-ui-from-text/)
- [Animation Vocabulary Skill (Emil Kowalski)](https://claudepluginhub.com/skills/emilkowalski-emil-design-skills/animation-vocabulary)
- [Motion Design Glossary (Design Shifu)](https://www.designshifu.com/blog/motion-design-glossary)
- [game-feel Skill](https://claudeskills.info/ko/skills/gamedev-skills/awesome-gamedev-agent-skills/game-feel/)
- [Game Juice 체크리스트 30가지](https://gamejuice.pages.dev/articles/game-juice-checklist-30-techniques)
- [카메라 무빙 용어 가이드 (Carat)](https://carat.im/blog/camera-moving-terms-guide)
- [Substance Beats Style (NAACL 2025)](https://preview.aclanthology.org/setup/2025.naacl-long.433)

### 나. 아이디어 2
- ['삼쩜삼'은 수수료 있어요...국세청 원클릭은 무료로 환급 (SBS Biz)](https://biz.sbs.co.kr/amp/article/20000225720)
- [외국인 근로자 연말정산 2026 (아시아경제)](https://cm.asiae.co.kr/en/article/2026010709522291133)
- [세무사회 "삼쩜삼, 아직 3건 남아있어" (세정신문)](https://www.taxtimes.co.kr/news/article.html?no=270088)
- [세무사회, 삼쩜삼 공정위 2차 신고 (택스워치)](https://www.taxwatch.co.kr/article/tax/2026/05/29/0003)
