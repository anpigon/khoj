---
sidebar_position: 3
---

# Obsidian

> Obsidian에서 당신의 두 번째 뇌에 질문하세요

![데모](https://assets.khoj.dev/obsidian_khoj_side_panel_pak_telemedicine.gif)

## 기능
- **채팅**
  - **더 빠른 답변**: 개인 노트나 공개 인터넷에서 빠르게 답변을 찾으세요.
  - **창의력 보조**: 답변 검색과 콘텐츠 생성을 원활하게 넘나드세요.
  - **반복적 발견**: 노트를 반복적으로 탐색하고 재발견하세요.
- **검색**
  - **자연어**: 트랜스포머 기반 ML 모델을 사용한 고급 자연어 이해
  - **점진적**: 입력과 동시에 검색 결과를 보여주는 빠른 점진적 검색 경험
- **유사 항목**
  - **발견**: 현재 노트와 유사한 노트를 찾으세요.

## 설치
:::info[직접 호스팅]
Khoj 서버를 직접 호스팅하는 경우, 아래의 Khoj Obsidian 플러그인 설정 단계를 업데이트하세요:
- `Khoj URL` 필드를 당신의 Khoj 서버 URL로 설정하세요. 기본적으로 `http://127.0.0.1:42110`을 사용합니다.
- Khoj 서버가 익명 모드로 실행되는 경우 `Khoj API Key` 필드를 설정하지 마세요. 예: `khoj --anonymous-mode`
:::

1. Obsidian 설정 패널의 *Community plugins* 탭에서 [Khoj](https://obsidian.md/plugins?id=khoj)를 엽니다.
2. Obsidian의 Khoj 플러그인 페이지에서 *Install*을 클릭한 다음 *Enable*을 클릭합니다.
3. [Khoj 웹 앱](https://app.khoj.dev/settings#clients)에서 API 키를 생성합니다.
4. Obsidian의 Khoj 플러그인 설정에서 Khoj API 키를 설정합니다.
5. (선택 사항) Obsidian의 Khoj 플러그인 설정에서 `Force Sync`를 클릭하여 Obsidian 저장소를 즉시 동기화합니다.
    <br />기본적으로 Obsidian 저장소는 주기적으로 자동 동기화됩니다.

Obsidian 플러그인 설치에 대한 자세한 내용은 공식 [Obsidian 플러그인 문서](https://help.obsidian.md/Extending+Obsidian/Community+plugins)를 참조하세요.

## 사용법
### 채팅
[리본](https://help.obsidian.md/User+interface/Workspace/Ribbon)에서 *Khoj chat* 아이콘 💬을 클릭하거나 [명령어 팔레트](https://help.obsidian.md/Plugins/Command+palette)에서 *Khoj: Chat*을 실행하고 자연스러운 대화 스타일로 질문하세요.<br />
예: *"작년에 세금 신고를 언제 했나요?"*

자세한 내용은 [Khoj 채팅](/features/chat)을 참조하세요.

### 유사한 노트 찾기
현재 노트와 유사한 다른 노트를 보려면 [명령어 팔레트](https://help.obsidian.md/Plugins/Command+palette)에서 *Khoj: Find Similar Notes*를 실행하세요.

### 검색
[명령어 팔레트](https://help.obsidian.md/Plugins/Command+palette)에서 *Khoj: Search*를 실행하세요.

자세한 내용은 [Khoj 검색](/features/search)을 참조하세요. 검색할 항목을 제한하려면 [쿼리 필터](/miscellaneous/query-filters)를 사용하세요.

[search_demo](https://user-images.githubusercontent.com/6413477/218801155-cd67e8b4-a770-404a-8179-d6b61caa0f93.mp4 ':include :type=mp4')

## 업그레이드
  1. Obsidian 설정에서 *Community plugins* 탭을 엽니다.
  2. *Check for updates* 버튼을 클릭합니다.
  3. Khoj 옆에 *Update* 버튼이 있으면 클릭합니다.

## 문제 해결
  - Khoj를 설정하려면 Khoj 플러그인 설정 창을 엽니다.
  - 설정 변경 사항이 적용되지 않은 경우 Khoj를 비활성화했다가 다시 활성화합니다.
  - 결과가 실패하거나 오래된 경우 *Update* 버튼을 클릭하여 인덱스를 강제로 새로 고칩니다.