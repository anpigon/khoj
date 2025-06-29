---
sidebar_position: 3
---

# 검색

두 번째 두뇌에서 관련 노트와 문서를 찾기 위해 초고속 검색을 활용하세요.

### 사용법
1. Khoj 검색 열기
  - **웹에서**: 웹 브라우저에서 https://app.khoj.dev/를 엽니다.
  - **Obsidian에서**: [리본](https://help.obsidian.md/User+interface/Workspace/Ribbon)에서 *Khoj 검색* 아이콘 🔎을 클릭하거나 [명령 팔레트](https://help.obsidian.md/Plugins/Command+palette)에서 *Khoj: 검색*을 검색합니다.
  - **Emacs에서**: `M-x khoj <user-query>`를 실행합니다.
2. 자연어를 사용하여 지식 기반에서 관련 항목을 쿼리합니다. [쿼리 필터](/miscellaneous/query-filters)를 사용하여 검색할 항목을 제한합니다.

### 데모
![](/img/search_agents_markdown.png ':size=400px')


### 구현 개요
문서와 검색 쿼리의 의미 벡터(일명 벡터 임베딩)를 생성하는 데 이중 인코더 모델이 사용됩니다.
1. 문서를 Khoj와 동기화하면 이중 인코더 모델을 사용하여 문서(청크)의 의미 벡터를 생성하고 저장합니다.
2. 자연어 검색을 시작하면 이중 인코더 모델이 쿼리를 의미 벡터로 변환하고 의미 벡터를 비교하여 해당 쿼리에 가장 관련성이 높은 문서 청크를 찾습니다.
3. 더 느리지만 더 높은 품질의 교차 인코더 모델이 해당 쿼리에 대한 문서를 다시 순위 지정하는 데 사용됩니다.

### 설정 (자체 호스팅)
자체 호스팅 시 검색 모델 구성을 **필요로 하지 않습니다**. Khoj는 일반적인 사용을 위해 적절한 기본 로컬 검색 모델 구성을 설정합니다.

더 나은 다국어 검색이 필요하거나, 다르거나 새로운 모델을 실험하고 싶거나, 기본 모델이 사용 사례에 적합하지 않은 경우 이 설정을 구성할 수 있습니다.

[Huggingface에서 로컬로 다운로드한](https://huggingface.co/models?library=sentence-transformers) 이중 인코더 모델을 사용하거나, [HuggingFace 추론 API](https://endpoints.huggingface.co/), OpenAI API, Azure OpenAI API 또는 Ollama, LiteLLM 등과 같은 OpenAI 호환 API를 통해 제공되는 모델을 사용할 수 있습니다. 검색 모델을 구성하려면 아래 단계를 따르세요:

1. Khoj 관리 패널에서 [SearchModelConfig](http://localhost:42110/server/admin/database/searchmodelconfig/) 페이지를 엽니다.
2. 더하기 버튼을 눌러 새 모델 구성을 추가하거나 기존 모델 구성의 ID를 클릭하여 편집합니다.
3. `biencoder` 필드를 구성하는 API를 통해 [로컬로](https://huggingface.co/models?library=sentence-transformers) 지원되는 이중 인코더 모델의 이름으로 설정합니다.
4. OpenAI 임베딩 모델을 사용하려면 `Embeddings inference endpoint api key`를 OpenAI API 키로 설정하고 `Embeddings inference endpoint type`을 `OpenAI`로 설정합니다.
5. 또한 해당 API를 통해 모델을 사용하려면 `Embeddings inference endpoint`를 Azure OpenAI 또는 OpenAI 호환 API URL로 설정합니다.
6. 사용하려는 검색 모델 구성이 `name` 필드가 `default`[^1]로 설정된 **유일한** 구성인지 확인합니다.
7. 검색 모델 구성을 저장하고 Khoj 서버를 다시 시작하여 새롭게 업데이트된 검색 구성을 사용합니다.

:::info
다른 이중 인코더 모델을 사용하려면 모든 문서를 다시 색인해야 합니다.
:::

:::info
지식 기반과의 채팅에 적절한 수의 문서를 얻으려면 각 이중 인코더에 대해 `Bi encoder confidence threshold` 필드를 조정해야 할 수 있습니다.

여기서 신뢰도는 쿼리와 문서 간의 의미론적 거리의 정규화된 측정값입니다. 신뢰도 임계값은 이 필드에 지정된 거리 내에 있는 채팅으로 반환되는 문서를 제한합니다. 0.0(정확히 겹침)에서 1.0(의미 겹침 없음) 사이의 값을 가질 수 있습니다.
:::

[^1]: Khoj는 시작 시 `default`라는 이름의 첫 번째 검색 모델 구성을 해당 세션의 검색 모델 구성으로 사용합니다.
