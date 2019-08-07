---
title: 5. Service SDK 샘플 코드
category: 
order: 2
date: 2019-08-05
---

> Service SDK에서 제공하는 기가지니 샘플 코드를 다운로드 받고, 직접 실행해봅니다.

### 5.1 서비스 샘플 코드

#### **실행 방법**

- 샘플 코드 안에 있는 api key값을 자신의 key값으로 변경 (참고: [Service SDK - API 초기화](https://ktaidevelopers.github.io/2_서비스 개발하기/Service SDK/#api-초기화){: target="_blank"})
- 자신의 웹 서버에 파일 업로드
- 개발자모드 등록 후, 해당 파일의 url 입력으로 코드 실행 (참고: [개발자모드 등록](https://ktaidevelopers.github.io/2_서비스 개발하기/개발 환경 셋팅하기/){: target="_blank"})

#### 종류

##### [구구단  게임](https://github.com/GiGAGenie-ServiceSDK/gigagenie-ninenine){: target="_blank"}

- 사용 API
  - [gigagenie.init (초기화)](<https://github.com/GiGAGenie-ServiceSDK/UserGuide/wiki/init>){: target="_blank"}
  - [gigagenie.voice.getVoiceText (음성 인식)](<https://github.com/GiGAGenie-ServiceSDK/UserGuide/wiki/voice.getVoiceText>){: target="_blank"}
  - [gigagenie.voice.stopTTS (음성 인식 중단)](<https://github.com/GiGAGenie-ServiceSDK/UserGuide/wiki/voice.stopTTS>){: target="_blank"}
  - [gigagenie.media.onMuteRequest (Mute 요청 이벤트 수신)](<https://github.com/GiGAGenie-ServiceSDK/UserGuide/wiki/media.onMuteRequest>){: target="_blank"}
  - [gigagenie.voice.onRequestClose (서비스 종료 수신)](<https://github.com/GiGAGenie-ServiceSDK/UserGuide/wiki/voice.onRequestClose>){: target="_blank"}
  - [gigagenie.voice.svcFinished (서비스 종료 처리)](<https://github.com/GiGAGenie-ServiceSDK/UserGuide/wiki/voice.svcFinished>){: target="_blank"}

##### [단어 퀴즈](https://github.com/GiGAGenie-ServiceSDK/gigagenie-quiz){: target="_blank"}

- 8초 간격으로 힌트를 보여주고 퀴즈 정답을 맞추는 게임
- 사용 API
  - [gigagenie.init (초기화)](<https://github.com/GiGAGenie-ServiceSDK/UserGuide/wiki/init>){: target="_blank"}
  - [gigagenie.voice.getVoiceText (음성 인식)](<https://github.com/GiGAGenie-ServiceSDK/UserGuide/wiki/voice.getVoiceText>){: target="_blank"}
  - [gigagenie.voice.sendTTS (음성 출력)](<https://github.com/GiGAGenie-ServiceSDK/UserGuide/wiki/voice.sendTTS>){: target="_blank"}
  - [gigagenie.voice.setVoiceFilter  (음성 필터 적용 단어 등록)](<https://github.com/GiGAGenie-ServiceSDK/UserGuide/wiki/voice.setVoiceFilter>){: target="_blank"}
  - [gigagenie.voice.onVoiceFilterMsg (음성 필터 적용 메세지 수신)](<https://github.com/GiGAGenie-ServiceSDK/UserGuide/wiki/voice.onVoiceFilterMsg>){: target="_blank"}
  - [gigagenie.voice.onRequestClose (서비스 종료 수신)](<https://github.com/GiGAGenie-ServiceSDK/UserGuide/wiki/voice.onRequestClose>){: target="_blank"}
  - [gigagenie.voice.svcFinished (서비스 종료 처리)](<https://github.com/GiGAGenie-ServiceSDK/UserGuide/wiki/voice.svcFinished>){: target="_blank"}

##### [Youtube 재생](<https://github.com/GiGAGenie-ServiceSDK/gigagenie-youtube>){: target="_blank"}

- Youtube 영상 플레이로 onAppStatusChange API 동작 확인
- 사용 API
  - [gigagenie.init (초기화)](<https://github.com/GiGAGenie-ServiceSDK/UserGuide/wiki/init>){: target="_blank"}
  - [gigagenie.init.onAppStatusChange (Mute/Unmute, Pause/Resume 상태 확인)](<https://github.com/GiGAGenie-ServiceSDK/UserGuide/wiki/init.onAppStatusChange>){: target="_blank"}
  - [gigagenie.media.onMuteRequest (Mute 요청 이벤트 수신)](<https://github.com/GiGAGenie-ServiceSDK/UserGuide/wiki/media.onMuteRequest>){: target="_blank"}