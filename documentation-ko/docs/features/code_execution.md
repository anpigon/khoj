---
sidebar_position: 4
---

# 코드 실행

Khoj는 간단한 Python 코드를 생성하고 실행할 수 있습니다. 이는 Khoj가 데이터 분석을 수행하고, 플롯 및 보고서를 생성하도록 하려는 경우에 유용합니다. LLM은 기본적으로 복잡한 정량적 작업에 능숙하지 않습니다. 코드 생성 및 실행은 이러한 작업에 유용할 수 있습니다.

Khoj는 코드 도구를 사용해야 할 때 자동으로 추론합니다. 또한 코드 도구를 사용하도록 명시적으로 지시하거나 채팅에서 `/code` [슬래시 명령](https://docs.khoj.dev/features/chat/#commands)을 사용할 수 있습니다.

## 설정 (자체 호스팅)
### 테라리움 샌드박스
[Cohere의 테라리움](https://github.com/cohere-ai/cohere-terrarium)을 사용하여 머신에 코드 샌드박스를 로컬로 무료로 호스팅할 수 있습니다.

Docker로 실행하려면 [docker-compose.yml](https://github.com/khoj-ai/khoj/blob/master/docker-compose.yml)을 사용하여 테라리움 코드 샌드박스를 자동으로 설정하거나 다음과 같이 수동으로 시작할 수 있습니다:

```bash
docker pull ghcr.io/khoj-ai/terrarium:latest
docker run -d -p 8080:8080 ghcr.io/khoj-ai/terrarium:latest
```

소스에서 실행하려면 [이 지침](https://github.com/khoj-ai/cohere-terrarium?tab=readme-ov-file#development)을 확인하세요.

#### 확인
간단한 Python 표현식을 평가하여 실행 중인지 확인합니다:

```bash
curl -X POST -H "Content-Type: application/json" \
--url http://localhost:8080 \
--data-raw '{"code": "1 + 1"}' \
--no-buffer
```

### E2B 샌드박스
[E2B](https://e2b.dev/)는 Khoj가 더 많은 Python 라이브러리를 지원하는 원격이지만 다재다능한 샌드박스에서 코드를 실행할 수 있도록 합니다. 이는 [무료가 아닙니다](https://e2b.dev/pricing).

Khoj가 E2B를 코드 샌드박스로 사용하도록 하려면:
1. [대시보드](https://e2b.dev/dashboard)에서 API 키를 생성합니다.
2. Khoj 서버를 실행하는 머신에서 `E2B_API_KEY` 환경 변수를 해당 키로 설정합니다.
   - [docker-compose.yml](https://github.com/khoj-ai/khoj/blob/master/docker-compose.yml)을 사용하는 경우, `docker-compose.yml` 파일에서 `E2B_API_KEY` 환경 변수를 주석 해제하고 설정합니다.
3. 이제 Khoj 서버를 다시 시작하여 E2B 코드 샌드박스를 사용하도록 전환합니다.
