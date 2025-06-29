---
sidebar_position: 4
---

# 에이전트

에이전트를 사용하여 Khoj와 함께 사용자 지정 시스템 프롬프트를 설정할 수 있습니다. 서버 호스트는 모든 사용자가 접근할 수 있는 자체 에이전트를 설정할 수 있습니다. 저희 에이전트는 https://app.khoj.dev/agents에서 확인할 수 있습니다.

![데모](/img/agents_page_full.png)

## 에이전트 생성 (자체 호스팅)

서버의 `server/admin/database/agent`로 이동하여 `에이전트 추가`를 클릭하여 새 에이전트를 생성합니다. 모든 서버 사용자가 접근할 수 있도록 `public`으로 설정해야 합니다. 특정 사용자에게 접근을 제한하려면 `public` 플래그를 설정하지 않고 `Creator` 필드에 사용자를 추가합니다.

`personality` 필드에 사용자 지정 프롬프트를 설정합니다.
