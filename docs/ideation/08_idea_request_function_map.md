# 아이디어 5: 요청에서 자라는 기능 분류표

사람들이 실제로 한 요청을 모아 거꾸로 "생활 기능 분류표"를 뽑고, 그 칸을 여러 회사의 MCP로 채우되 기존 MCP로 채워지지 않는 칸은 직접 만들어 채워서, 지금 AI 비서가 끝내지 못하는 요청을 끝까지 실현하게 하는 층입니다. 낸 사람은 lgosoup입니다.

## 1. 나온 과정

```mermaid
flowchart TD
    A["출발점<br>아이디어 3<br>기억하는 비서<br>11/20"] --> B["기억과 실행을<br>함께 하는<br>비서로 냄<br>11/23"]
    B --> C["비슷한 사례<br>조사<br>피클 등이<br>이미 함<br>11/23"]
    C --> D["초점 이동<br>앱 없는<br>스마트폰<br>11/24"]
    D --> E["발상 뒤집기<br>앱이 아니라<br>요청에서 출발<br>11/24"]
    E --> F["요청에서 자라는<br>기능 분류표<br>11/24"]
    F --> G["주제 결정<br>이슈 5번에서<br>진행 중"]
```

### 가. 출발점: LLM 취약계층 (11/20)

1) LLM(대규모 언어 모델)은 빠르게 발전하고 있지만, 모든 사람이 쉽게 쓰지는 못합니다. 고령층만이 아니라 20대에도 AI를 끝까지 활용하지 못하는 사람이 있습니다.
2) 이들은 원하는 일을 말로 요청할 수는 있습니다. 어려운 것은 AI 비서가 중간에 "그건 할 수 없어요"로 멈출 때 다른 방법을 찾지 못한다는 점입니다.
3) 처음에는 [아이디어 3](06_idea_memory_assistant.md)처럼 기억(지식 그래프)과 실행을 함께 하는 비서로 생각했습니다.

### 나. 기억과 실행을 함께 하는 비서 (11/23)

1) 사용자의 활동을 기억해 막연한 말을 알아듣고, 여러 앱의 기능을 MCP(Model Context Protocol)로 이어 실행하는 비서로 후보를 냈습니다.
2) MCP는 AI가 바깥 도구나 서비스의 기능을 쓸 수 있게 이어 주는 표준 방식입니다.

### 다. 사례 조사로 초점을 옮김 (11/23~11/24)

1) 사용자 기억을 쌓아 일까지 대신 하는 것은 피클이 이미 하고 있었고, Gemini와 Siri AI도 앱 기능을 대신 실행합니다(6장).
2) 그래서 요청을 알아듣는 부분(의도, 맥락, 기억)은 이런 앞단 서비스에 맡기고, 그 뒤에서 요청을 실제로 실현하는 쪽, 즉 앱 없는 스마트폰 쪽으로 초점을 옮겼습니다(4장).

### 라. 발상을 뒤집음: 앱이 아니라 요청에서 출발 (11/24)

1) 앱은 결국 기능 묶음입니다. 처음에는 앱을 기능 단위로 쪼개 MCP로 잇는 방향을 보았지만, 앱 기능을 모아 내놓는 것은 Zapier MCP, MCP 게이트웨이, 구글 AppFunctions가 이미 하고 있었습니다.
2) 그래서 순서를 뒤집었습니다. 서비스가 가진 기능에서 출발하지 않고, 사용자가 진짜 원하는 요청에서 출발해 그 요청을 실현하는 데 필요한 기능으로 나눕니다(3장).

### 마. 요청에서 자라는 기능 분류표 (11/24)

1) 나눈 기능을 "생활 기능 분류표"로 정리하고, 그 분류표를 실제 요청에서 거꾸로 뽑아 계속 늘려 가는 것으로 정했습니다.
2) 분류표 칸마다 기존 MCP로 되는지를 표시하고, 안 되는 칸은 직접 채웁니다(2장).

## 2. 무엇을 하나

```mermaid
flowchart LR
    R["사용자가<br>진짜 원하는 요청<br>(앞단 서비스가<br>만듦)"] --> T["생활 기능<br>분류표<br>(중간 단계)"]
    T --> M1["기존 MCP<br>회사 A"]
    T --> M2["기존 MCP<br>회사 B"]
    T --> N["새로 채운<br>기능"]
```

1) 요청은 앞단(피클 같은 비서, 상용 서비스)이 의도와 맥락을 담아 만든 것을 그대로 받습니다.
2) 그 요청을 생활 기능 분류표의 칸들로 나눕니다. 예: 연락하기 > 사진 보내기, 사진 > 사람별로 고르기, 일정 > 추가하기
3) 칸마다 여러 회사의 기존 MCP·API 기능을 통째로 또는 일부만 잇고, "기존 MCP로 됨 / 일부만 됨 / 안 됨"을 표시합니다.
4) 안 되는 칸은 기존 기능을 조합하거나 새 기능을 만들어 채웁니다. 한 번 채운 칸은 분류표에 남아 다음 요청에도 쓰입니다.
5) 사용자에게는 이번 요청이 어떤 칸들로 이뤄졌고, 그중 어느 칸을 새로 채워서 가능해졌는지를 쉬운 말로 보여 줍니다. 되돌릴 수 없는 일(전송, 결제)은 확인을 받은 뒤 실행합니다.
6) 예를 들어 "지난주 사진 중 엄마 나온 것만 골라 큰 글씨 설명과 함께 보내 줘"에서 "사람별로 사진 고르기", "큰 글씨 설명 붙이기"가 기존 MCP에 없으면 그 칸을 채워서 요청을 끝까지 실현합니다.

## 3. 발상의 차이

### 가. 출발점이 반대

| 비교 | 기존 (Zapier MCP, MCP 게이트웨이, AppFunctions) | 이 아이디어 |
|---|---|---|
| 출발점 | 서비스: 이미 있는 앱과 API | 사용자가 진짜 원하는 요청 |
| 방향 | 아래에서 위로: 서비스가 가진 기능을 쪼개 내놓음 | 위에서 아래로: 요청을 실현하는 데 필요한 기능으로 나눔 |
| 기능이 없으면 | 쓸 수 없음 | 만들거나 덧붙여 채움 |
| 목표 | 기존 기능을 AI가 쓸 수 있게 하기 | 요청을 끝까지 실현하기 |
| 범용성 | 연결된 서비스 범위 안 | 분류표가 기준이라 서비스가 바뀌어도 그대로 |

### 나. 분류표가 다른 점

애플 App Intents 스키마 도메인과 schema.org Action도 기능을 분류합니다. 그러나 이 분류는 회사나 표준 단체가 미리 정한 분야 틀이고, 앱이 그 틀에 맞춰 들어갑니다. 이 아이디어의 분류표는 실제 요청에서 거꾸로 뽑고, 새 요청이 기존 칸으로 설명되지 않으면 칸이 새로 생깁니다.

### 다. 언어로 비유하면

| 단계 | 프로그래밍에서 | 이 아이디어에서 | 맡는 쪽 |
|---|---|---|---|
| 초고수준 | 사람이 쓴 코드 | 의도와 맥락이 담긴 자연어 요청 | 앞단 서비스 |
| 중간 단계 | 중간 언어 | 생활 기능 분류표로 옮긴 요청 | 이 아이디어 |
| 저수준 | 기계어 | 실제 MCP·API 호출 | 기존 서비스와 새로 채운 기능 |

## 4. 앱 없는 스마트폰

### 가. 그리는 모습

1) 폰에는 LLM 하나를 두고, 기능은 MCP처럼 하나의 방식으로 기능 단위로 이어 둡니다.
2) 사용자는 앱을 찾아 고르는 대신 하고 싶은 일을 말하고, 그 요청에 맞는 기능 조합이 그때그때 만들어집니다. 앱이 기능 묶음이라면, 요청마다 만들어지는 이 기능 조합이 그 사람만의 앱입니다.
3) 이 모습은 지금 완성된 기술이나 이번에 만들 결과물이 아니라 먼 방향입니다. 생활 기능 분류표는 이 방향의 바탕이 됩니다.

### 나. 비슷한 시도

| 시도 | 하는 일 | 이 방향과 비교 |
|---|---|---|
| 구글 AppFunctions | 안드로이드 앱이 기능을 기능 단위로 내놓고 Gemini가 씀 | 기능 단위로 내놓기는 하지만, 앱이 정한 단위이고 안드로이드 안에서만 |
| iOS 27 단축어 | 말로 설명하면 여러 앱 동작을 엮은 자동화를 만들어 줌 | 애플 기기 안에서만, 앱이 내놓은 동작만 엮음 |
| 구글 Create My Widget | 말로 설명하면 Gemini가 데이터를 엮은 위젯을 만듦 | 위젯만 |
| Nothing Playground, Essential Apps | 프롬프트로 위젯 미니 앱을 만들어 올림 | 위젯만, 새 앱 게시는 잠시 멈춤 |
| MCP Apps | 앱 회사가 만든 화면을 ChatGPT, Claude 대화 안에 띄움 | 앱 회사가 만든 것을 보여 줄 뿐, 요청에 맞춰 기능을 조합하지는 않음 |

## 5. 12/16까지 만들 범위

1) 연락·사진·일정 영역의 실제 요청 100개를 모아 생활 기능 분류표를 뽑습니다.
2) 분류표 칸에 기존 MCP를 잇고, 칸마다 "됨 / 일부만 됨 / 안 됨"을 표시합니다.
3) 안 되는 칸 가운데 2~3개를 직접 채웁니다.
4) 같은 요청 100개를 (가) 일반 AI 비서에 MCP를 연결한 경우와 (나) 이 아이디어로 처리한 경우로 나눠 끝까지 실현된 요청 수를 비교하고, 새로 채운 칸 덕분에 처음 실현된 요청 수를 따로 셉니다.

## 6. 비슷한 사례

| 분야 | 이미 있는 것 | 비어 있는 곳 |
|---|---|---|
| 요청을 받아 대신 실행하는 비서 | 피클(사용자마다 기억을 쌓는 에이전트가 연결한 캘린더·메일·외부 서비스로 일정 확인, 식당 예약, 매장 전화 등을 대신 함, 2026년 11월 국내 앱스토어 무료 앱 상위권), 구글 Gemini, 애플 Siri AI, ChatGPT·Claude의 앱 연결 기능 | 연결된 서비스가 내놓은 기능 안에서만 일함 |
| 여러 서비스 기능을 한 MCP로 모으기 | Zapier MCP(9,000개 넘는 앱의 동작 가운데 원하는 것만 골라 내놓고, 칸 값을 고정해 일부만 쓸 수 있음), MCP 게이트웨이(Kong 등, 여러 MCP 서버의 도구를 모아 일부만 내놓음) | 개발자나 관리자가 앱 기준으로 고름. 서비스에 없는 기능은 쓸 수 없음 |
| 기능 분류 | 애플 App Intents 스키마 도메인(분야별 동작 틀), schema.org Action(웹용 동작 분류), JSPLIT(MCP 도구를 분류해 AI가 도구를 잘 고르게 함) | 미리 정한 틀이거나 이미 있는 도구를 분류함. 실제 요청에서 자라지 않음 |
| 요청 분류 | TUNA(실제 대화 1,193개에서 요청 분류 57가지를 뽑음) | 칸마다 도구로 되는지와는 잇지 않음 |
| 없는 도구를 스스로 만드는 에이전트 | Alita·Alita-G(부족한 도구를 MCP로 만들어 쓰고 다시 쓰는 "MCP Box"로 쌓음), MCP-Zero(기존 도구를 먼저 찾고 없으면 만듦), Tool-Genesis(도구 만들기 벤치마크) | 에이전트가 과제를 풀려고 만들고 쌓음. 사람이 읽는 생활 기능 분류표로 남지는 않음 |
| MCP를 더 낮은 언어로 옮기기 | Cloudflare Code Mode(MCP 도구를 TypeScript API로 바꿔 LLM이 코드를 짜게 함) | 토큰을 아끼려는 개발자용 |

## 7. 지금까지의 판단

1) "그냥 AI한테 물어보면 되지 않나"에 "AI 채팅은 앱을 못 쓴다"로는 답할 수 없습니다. ChatGPT, Claude 같은 AI 채팅도 메일, 일정 같은 앱에 연결하는 기능이 있고, Gemini와 Siri AI는 앱 기능을 대신 실행합니다.
2) 요청을 알아듣고 대신 실행하는 것은 피클과 큰 회사들이 이미 하고 있습니다. 그래서 이 아이디어는 그 부분을 앞단에 맡기고, 앞단이 만든 요청을 끝까지 실현하는 쪽만 맡습니다.
3) 남은 틈은 두 가지로 보입니다.
   - 실제 요청에서 거꾸로 뽑아 계속 자라는 생활 기능 분류표
   - 그 칸마다 지금 MCP로 되는지 안 되는지를 보여 주는 지도. 기능 분류 연구와 요청 분류 연구는 있지만, 둘을 이어 "생활 요청 가운데 무엇이 되고 무엇이 안 되는지"를 보여 주는 것은 검색한 범위에서 찾지 못했습니다.
4) 빈 칸을 직접 만들어 채우는 것은 Alita, MCP-Zero 같은 연구가 이미 하고 있습니다. 이 아이디어에서 다른 점은 채운 칸이 에이전트 혼자 쓰는 도구가 아니라 사람이 읽을 수 있는 분류표 칸으로 남아 다음 요청에 다시 쓰인다는 것입니다.
5) 아이디어 3과 다른 점은 이렇습니다.
   - 아이디어 3: 사용자의 기억을 찾아 앱 하나(Gmail)의 작업까지 이어 주는 비서
   - 아이디어 5: 기억과 요청 이해는 앞단에 맡기고, 요청을 실현하는 데 필요한 기능을 분류표로 나누어 여러 회사의 MCP로 채우고 빈 칸을 메우는 층
6) 걸리는 점이 있습니다.
   - 사회공헌이 약합니다. 대상(LLM 취약계층)이 넓고, 사진 보내기나 일정 넣기 같은 예시는 피해보다 불편을 줄입니다. 대상을 좁히고 요청이 실현되지 않아 생기는 실제 손해를 재야 합니다.
   - 사진, 연락처를 다루므로 개인정보 위험이 있습니다. 피클은 사용자가 말하지 않은 가족 관계를 메일, 넷플릭스 프로필, 연락처를 조합해 알아내거나 시키지 않은 식당 전화를 스스로 건 일로 기사가 났습니다. 시연은 지어낸 데이터로 하고, 되돌릴 수 없는 실행은 확인을 받아야 합니다.
   - 새로 채운 기능이 잘못 동작할 수 있습니다. 채운 칸은 사례 시험을 거쳐야 분류표에 남깁니다.

## 8. 출처

- [What is the Model Context Protocol (MCP)? (Model Context Protocol)](https://modelcontextprotocol.io/introduction)
- [캘린더 속 송년회 일정 훑고 식당 빈자리 예약까지⋯AI 비서 '피클' 써보니 (아이뉴스24)](https://www.inews24.com/view/2025971)
- [Privacy Control Concerns Become Reality Amid Craze for 'Pickle,' the AI That Acts on Its Own (아시아경제)](https://view.asiae.co.kr/en/article/2026110909414917294)
- [Pickle: The personal AI agent network for Asia (Y Combinator)](https://www.ycombinator.com/companies/pickle-2)
- [Ask Gemini to handle your multi-step tasks in select Android apps (Pixel Phone Help)](https://support.google.com/pixelphone/answer/16940971)
- [Google details 'AppFunctions' that let Gemini use Android apps (9to5Google)](https://9to5google.com/2026/02/25/android-appfunctions-gemini/)
- [Apple introduces Siri AI, a profoundly more capable and personal assistant (Apple)](https://www.apple.com/newsroom/2026/06/apple-introduces-siri-ai-a-profoundly-more-capable-and-personal-assistant/)
- [Apple Brings Natural Language Creation to Shortcuts App (MacRumors)](https://www.macrumors.com/2026/06/08/apple-brings-natural-language-to-shortcuts/)
- [Gemini Intelligence brings gen UI, Gboard 'Rambler' to Android (9to5Google)](https://9to5google.com/2026/05/12/gemini-intelligence-announcement/)
- [Nothing launches AI tool for building mini apps using prompts (TechCrunch)](https://techcrunch.com/2025/09/30/nothing-launches-ai-tool-for-building-mini-apps-using-prompts/)
- [Hands-on: Nothing 'Essential Apps' let you vibe code widgets (9to5Google)](https://9to5google.com/2026/02/10/nothing-essential-apps-hands-on/)
- [MCP Apps - Bringing UI Capabilities To MCP Clients (Model Context Protocol Blog)](https://blog.modelcontextprotocol.io/posts/2026-01-26-mcp-apps/)
- [How Zapier MCP tools work (Zapier)](https://docs.zapier.com/mcp/overview/how-tools-work)
- [How to: Aggregate MCP tools from multiple AI MCP Server entities (Kong)](https://developer.konghq.com/ai-gateway/aggregate-mcp-tools/)
- [App schema domains (Apple Developer)](https://developer.apple.com/documentation/appintents/app-schema-domains)
- [Potential Actions (schema.org)](https://schema.org/docs/actions.html)
- [JSPLIT: A Taxonomy-based Solution for Prompt Bloating in Model Context Protocol (arXiv 2510.14537)](https://arxiv.org/abs/2510.14537)
- [Taxonomy of User Needs and Actions (arXiv 2510.06124)](https://arxiv.org/abs/2510.06124)
- [Alita (arXiv 2505.20286)](https://arxiv.org/abs/2505.20286)
- [Alita-G (arXiv 2510.23601)](https://arxiv.org/abs/2510.23601)
- [MCP-Zero: Active Tool Discovery for Autonomous LLM Agents (arXiv 2506.01056)](https://arxiv.org/abs/2506.01056)
- [Tool-Genesis (arXiv 2603.05578)](https://arxiv.org/abs/2603.05578)
- [Code Mode: the better way to use MCP (Cloudflare)](https://blog.cloudflare.com/code-mode/)
