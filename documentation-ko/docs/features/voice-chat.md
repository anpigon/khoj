# 음성

음성을 사용하여 Khoj와 대화할 수 있습니다. Khoj는 채팅 기능과 동일한 모델을 사용하여 쿼리에 응답합니다. 웹, 데스크톱 및 Obsidian 앱에서 음성 채팅을 사용할 수 있습니다.

![음성 채팅](https://assets.khoj.dev/speech_to_text_demo.gif)

작은 마이크 아이콘을 클릭하여 Khoj에 음성 메시지를 보냅니다. Khoj는 들은 내용을 텍스트로 다시 보냅니다. 필요한 경우 메시지를 보내기 전에 편집할 수 있습니다. https://app.khoj.dev/에서 사용해보세요!

## 음성 응답

음성 메시지를 보내면 Khoj는 자동으로 음성 메시지로 응답합니다.
또한 모든 메시지 옆에 있는 스피커 아이콘을 클릭하여 소리 내어 들을 수 있습니다. 음성 응답 기능은 현재 웹 보기에서만 사용할 수 있습니다.

![스피커 아이콘](/img/text_to_speech.png)

## 설정 (자체 호스팅)

음성 채팅은 애플리케이션을 초기화할 때 자동으로 구성됩니다. 기본 구성은 로컬에서 실행됩니다. 음성 채팅에 OpenAI Whisper API를 사용하려면 다음 단계에 따라 설정할 수 있습니다:

1. OpenAI API 키를 설정합니다. 지침은 [여기](/get-started/setup#add-chat-models)를 참조하세요.
2. http://localhost:42110/server/admin/database/speechtotextmodeloptions/에서 새 구성을 생성합니다. `whisper-1` 값과 `Openai` 모델 유형을 권장합니다.

텍스트 음성 변환 기능을 사용하려면 다음 단계에 따라 설정할 수 있습니다:

1. [ElevenLabs.io](https://elevenlabs.io/)에서 계정을 설정합니다.
2. `ELEVEN_LABS_API_KEY` 키로 환경 변수에 API 키를 구성합니다.
3. (선택 사항) 사용하려는 음성의 특정 음성 ID로 새 [음성 모델 옵션](http://localhost:42110/server/admin/database/voicemodeloption/)을 생성합니다. [여기](https://elevenlabs.io/app/voice-library)에서 옵션을 탐색할 수 있습니다.
