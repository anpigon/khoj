# 온라인 검색

Khoj는 쿼리에 답변하기 위해 기존 지식 외에 새로운 정보가 필요하다고 판단될 때, 응답의 근거를 마련하기 위해 인터넷을 검색합니다. 요청에 응답하는 데 사용한 모든 온라인 참조를 항상 표시합니다.

기본적으로 Khoj는 질문에 답하기 위해 어떤 정보 소스를 읽어야 하는지 추론하려고 시도합니다. 여기에는 문서 읽기 또는 온라인 정보 검색이 포함될 수 있습니다. 채팅 쿼리에 `/online` 접두사를 추가하여 온라인 검색을 명시적으로 트리거할 수도 있습니다.

온라인 검색을 트리거해야 하는 쿼리 예시:
- 이스라엘-팔레스타인 전쟁에 대한 최신 뉴스는 무엇입니까?
- 뉴욕시에서 최고의 피자를 어디서 찾을 수 있습니까?
- /online 2024년 세금 신고 마감일.
- 이 기사를 요약해 주세요: https://en.wikipedia.org/wiki/Haitian_Revolution

직접 사용해보세요! https://app.khoj.dev

## 자체 호스팅

### 검색

온라인 검색은 자체 호스팅에서도 작동합니다! 몇 가지 옵션이 있습니다:

- Docker를 사용하는 경우, 표준 `docker-compose.yml`을 사용하여 [searxng](https://github.com/searxng/searxng)와 함께 온라인 검색이 즉시 작동해야 합니다.
- 비로컬 무료 솔루션의 경우, [JinaAI의 리더 API](https://jina.ai/reader/)를 사용하여 온라인 검색 및 웹 페이지를 읽을 수 있습니다. https://jina.ai/reader에서 무료 API 키를 얻을 수 있습니다. 온라인 검색을 활성화하려면 `JINA_API_KEY` 환경 변수를 Jina AI 리더 API 키로 설정합니다.
- 프로덕션 수준의 빠르고 온라인 검색을 얻으려면 `SERPER_DEV_API_KEY` 환경 변수를 [Serper.dev](https://serper.dev/) API 키로 설정합니다. 이러한 검색 결과에는 답변 상자, 지식 그래프 등과 같은 추가 컨텍스트가 포함됩니다.

### 웹 페이지 읽기

기본적으로 웹 페이지 읽기를 활성화하기 위해 **아무것도 할 필요가 없습니다**. Khoj는 `requests` 라이브러리를 사용하여 웹 페이지를 자동으로 읽습니다. 더 분산되고 확장 가능한 웹 페이지 읽기를 위해 다음 옵션을 사용할 수 있습니다:

- Jina AI의 리더 API를 검색에 사용하는 경우, 웹 페이지 읽기에도 자동으로 작동해야 합니다.
- 확장 가능한 웹 페이지 스크래핑을 위해 [Firecrawl](https://www.firecrawl.dev/)을 사용할 수 있습니다. 새 [웹 스크래퍼](http://localhost:42110/server/admin/database/webscraper/add/)를 생성합니다. Firecrawl API 키를 Api Key 필드에 설정하고 유형을 Firecrawl로 설정합니다.
- 고급 웹 페이지 읽기를 위해 [Olostep](https://www.olostep.com/)을 사용할 수 있습니다. 이는 기본 웹 페이지 리더보다 웹 페이지 읽기 성공률이 높습니다. 새 [웹 스크래퍼](http://localhost:42110/server/admin/database/webscraper/add/)를 생성합니다. Olostep API 키를 Api Key 필드에 설정하고 유형을 Olostep으로 설정합니다.
