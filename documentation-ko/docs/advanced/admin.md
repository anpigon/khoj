# 관리자 패널
> 관리자 패널을 통해 구성 가능한 Khoj 설정 설명

기본적으로 관리자 패널은 `http://localhost:42110/server/admin/`에서 사용할 수 있습니다. 관리자 자격 증명(`KHOJ_ADMIN_EMAIL` 및 `KHOJ_ADMIN_PASSWORD`)으로 로그인하여 관리자 패널에 접근할 수 있습니다. 관리자 패널을 통해 Khoj 서버의 다양한 설정을 구성할 수 있습니다.

## 앱 설정
### 에이전트
작성자, 연구원, 치료사 등 다양한 사용 사례에 사용할 모든 에이전트를 추가합니다.
- `성격`: 채팅 모델에 에이전트의 성격을 조정하는 방법을 알려주는 프롬프트입니다.
- `채팅 모델`: 에이전트에 사용할 채팅 모델입니다.
- `이름`: 에이전트의 이름입니다. 이 필드는 앱 전체에서 에이전트에 고유한 ID를 부여하는 데 도움이 됩니다.
- `아바타`: 에이전트 프로필 사진의 URL입니다. 앱 전체에서 에이전트에 고유한 시각적 ID를 부여하는 데 도움이 됩니다.
- `스타일 색상`, `스타일 아이콘`: 이 필드는 앱 전체에서 에이전트에 고유하고 시각적으로 식별 가능한 ID를 부여하는 데 도움이 됩니다.
- `슬러그`: URL에서 사용할 에이전트 이름입니다.
- `공개`: 이 에이전트가 이 Khoj 서버의 모든 사용자에게 표시되어야 하는 경우 이 옵션을 선택합니다.
- `관리자 관리`: 이 에이전트가 사용자가 아닌 관리자에 의해 관리되는 경우 이 옵션을 선택합니다.
- `생성자`: 에이전트를 생성한 사용자입니다.
- `도구`: 이 에이전트에서 사용할 수 있는 도구 목록입니다. 도구에는 메모, 이미지, 온라인이 포함됩니다. 이 필드는 현재 구성할 수 없으며 모든 도구(예: `["*"]`)만 지원합니다.

### 채팅 모델 옵션
다양한 사용 사례에 대해 시도하고 사용하며 전환할 모든 채팅 모델을 추가합니다. 추가하는 각 채팅 모델에 대해:
- `채팅 모델`: [OpenAI](https://platform.openai.com/docs/models), [Anthropic](https://docs.anthropic.com/en/docs/about-claude/models#model-names), [Gemini](https://cloud.google.com/vertex-ai/generative-ai/docs/learn/models#gemini-models) 또는 [오프라인](https://huggingface.co/models?pipeline_tag=text-generation&library=gguf) 채팅 모델의 이름입니다.
- `모델 유형`: `OpenAI`, `오프라인`과 같은 채팅 모델 공급자입니다.
- `비전 활성화`: 모델이 비전을 지원하는 경우 `true`로 설정합니다. 현재 `gpt-4o`와 같은 비전 지원 OpenAI 모델에서만 지원됩니다.
- `최대 프롬프트 크기`, `구독된 최대 프롬프트 크기`: 선택 사항 필드입니다. 컨텍스트를 모델에 전달할 수 있는 최대 컨텍스트 크기로 자르는 데 사용됩니다. 이는 정확성과 비용 절감에 도움이 될 수 있습니다.<br />
- `토크나이저`: 선택 사항 필드입니다. 토큰을 정확하게 계산하고 채팅 모델에 전달되는 컨텍스트를 모델의 최대 프롬프트 크기 내에 있도록 자르는 데 사용됩니다.
  ![채팅 모델 옵션 구성 예시](/img/example_chatmodel_option.png)

### 서버 채팅 설정
서버 채팅 설정은 다음과 같이 사용됩니다.
1. 구독 사용자(`고급` 필드) 및 비구독 사용자(`기본` 필드)의 기본 채팅 모델.
2. 채팅 응답 생성 중 의도 감지, 웹 검색 등 모든 중간 단계에 대한 채팅 모델.

서버 채팅 설정이 추가되지 않은 경우 구성의 첫 번째 ChatModelOption이 기본 채팅 모델로 사용됩니다.

서버 채팅 설정을 추가하려면:
- [ServerChatSettings](http://localhost:42110/server/admin/database/serverchatsettings/)의 `기본` 필드에 선호하는 기본 채팅 모델을 설정합니다.
- `고급` 필드는 자체 호스팅 시 설정할 필요가 없습니다. 설정되지 않은 경우 `기본` 채팅 모델이 모든 사용자와 중간 단계에 사용됩니다.

### AI 모델 API
이 설정은 AI 모델과 상호 작용하기 위한 API를 구성합니다.
추가하는 각 AI 모델 API에 대해 [추가](http://localhost:42110/server/admin/database/aimodelapi/add):
- `API 키`: [OpenAI](https://platform.openai.com/api-keys), [Anthropic](https://console.anthropic.com/account/keys) 또는 [Gemini](https://aistudio.google.com/app/apikey) API 키로 설정합니다.
- `이름`: `OpenAI`, `Gemini`, `Anthropic`과 같이 친숙한 이름을 지정합니다.
- `API 기본 URL`: API 기본 URL을 설정합니다. [Ollama](/advanced/ollama) 또는 [LMStudio](/advanced/lmstudio)와 같은 다른 OpenAI 호환 프록시 서버를 사용하는 경우에만 설정하는 것이 중요합니다.
  ![AI 모델 API 구성 예시](/img/example_openai_processor_config.png)

### 검색 모델 구성
검색 모델은 자연어 검색 및 채팅을 위해 문서의 벡터 임베딩을 생성하는 데 사용됩니다. [HuggingFace의 임베딩 모델](https://huggingface.co/models?pipeline_tag=sentence-similarity)을 선택하여 자연어 검색 및 채팅을 위해 문서의 벡터 임베딩을 생성할 수 있습니다.

<img src="/img/example_search_model_admin_settings.png" alt="검색 모델 설정 예시" style={{width: 500}} />

### 텍스트-이미지 모델 옵션
이 설정을 사용하여 텍스트-이미지 생성 모델을 추가합니다. Khoj는 현재 OpenAI, Stability 또는 Replicate API를 통해 사용할 수 있는 텍스트-이미지 모델을 지원합니다.
- `api-key`: OpenAI, Stability 또는 Replicate API 키로 설정합니다.
- `model`: 선택한 모델 공급자를 통해 사용할 수 있는 모델 이름을 설정합니다.
- `model-type`: 적절한 모델 공급자로 설정합니다.
- `openai-config`: OpenAI (호환) API를 통해 사용할 수 있는 이미지 생성 모델의 경우 위에서 `api-key` 필드를 지정하는 대신 적절한 OpenAI 프로세서 대화 설정을 설정할 수 있습니다.

### 음성-텍스트 모델 옵션
이 설정을 사용하여 음성-텍스트 모델을 추가합니다. Khoj는 현재 OpenAI API 또는 오프라인을 통한 whisper 음성-텍스트 모델만 지원합니다.

### 음성 모델 옵션
이 설정을 사용하여 텍스트-음성 모델을 추가합니다. Khoj는 현재 [ElevenLabs](https://elevenlabs.io/)의 모델을 지원합니다.

### 반성적 질문
이것은 각 사용자를 위한 시작 질문 제안의 정적 목록입니다. 현재 어떤 클라이언트 앱에서도 사용되지 않습니다. 웹 앱 홈 페이지에 표시되곤 했습니다. 최근 대화 또는 동기화된 지식 기반을 기반으로 각 사용자에게 개인화된 동적 시작 질문 목록으로 전환할 수 있습니다.

## 사용자 데이터
- 사용자, 항목, 대화, 구독, Github 구성, Notion 구성, 사용자 검색 구성, 사용자 대화 구성, 사용자 음성 구성

## 기타 데이터
- 프로세스 잠금: 자동화를 위한 영구 잠금
- 클라이언트 애플리케이션:

  클라이언트 애플리케이션을 사용하면 클라이언트 애플리케이션 ID + 비밀을 사용하여 Khoj 서버에 쿼리할 수 있는 타사 애플리케이션을 설정할 수 있습니다. 비밀은 베어러 토큰에 들어갑니다.