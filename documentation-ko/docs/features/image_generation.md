# 이미지 생성
Khoj를 사용하여 텍스트 프롬프트에서 이미지를 생성할 수 있습니다. 이미지 생성 흐름에 대한 자세한 내용은 다음 블로그 게시물에서 확인할 수 있습니다: https://blog.khoj.dev/posts/how-khoj-generates-images/.

이미지를 생성하려면 이미지 생성이 지침에 포함된 프롬프트를 Khoj에 제공하기만 하면 됩니다. Khoj는 이미지 생성 의도를 자동으로 감지하고, 생성 프롬프트를 증강한 다음 이미지를 생성합니다. 다음은 몇 가지 예시입니다:
| 프롬프트 | 이미지 |
| --- | --- |
| 지난달에 얻은 식물 그림, 픽사 애니메이션 | ![식물](/img/plants_i_got.png) |
| 내 관심사를 바탕으로 꿈의 집 그림 만들기 | ![집](/img/dream_house.png) |


## 설정 (자체 호스팅)

몇 가지 이미지 생성 옵션이 있습니다.

### 이미지 생성 모델

Ideogram, Flux, Stable Diffusion을 포함한 대부분의 최신 이미지 생성 모델을 지원합니다. 이 모델들은 [Replicate](https://replicate.com)를 사용하여 실행됩니다. 설정 방법은 다음과 같습니다:

1. [여기](https://replicate.com/account/api-tokens)에서 Replicate API 키를 얻습니다.
2. 새 [텍스트-이미지 모델](http://localhost:42110/server/admin/database/texttoimagemodelconfig/)을 생성합니다. `type`을 `Replicate`로 설정합니다. [이 목록](https://replicate.com/pricing#image-models)에서 볼 수 있는 모델 이름 중 하나를 사용합니다. [Replicate](https://replicate.com/black-forest-labs/flux-1.1-pro)의 `black-forest-labs/flux-1.1-pro` 모델 이름을 권장합니다.

### OpenAI

1. [OpenAI API 키](https://platform.openai.com/settings/organization/api-keys)를 얻습니다.
2. 아직 설정하지 않았다면 OpenAI API 키를 설정합니다. 지침은 [여기](/get-started/setup#add-chat-models)를 참조하세요.
3. http://localhost:42110/server/admin/database/texttoimagemodelconfig/에서 텍스트-이미지 구성을 생성합니다. 이미지 생성을 위해 OpenAI를 사용하려면 `dall-e-3` 모델 이름을 사용합니다. `Ai model api` 필드를 2단계에서 설정한 OpenAI AI 모델 API로 설정해야 합니다.
