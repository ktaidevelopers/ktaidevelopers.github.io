---
title: 4.3 웹 앱을 이용한 IoT 연동 가이드
category: 4. 참고
order: 3
date: 2019-07-25
---

> 기가지니 웹 앱 서비스로 IoT를 제어하는 방법입니다.

### 목적

해당 시나리오는 **IoT Makers 및 홈 IoT API와 별개**로, 기가지니 웹 앱 서비스를 기반으로 3rd Party의 IoT 단말을 제어하는 개발 시나리오 입니다.

### 동작 방식

기가지니 웹 앱 서비스에서 화면 UI 없이 제어 명령만 전달

<span style="color:red">필수 정책</span>  
기가지니에서 3rd Party 서버로 제어 명령 전달 후 바로 서비스 종료 처리

- 시나리오
  - 기가지니에 IoT 단말 제어 관련 발화 실행
  - IoT 단말 동작
  - 동작 후 기가지니 서비스 강제 종료
- 따라서, 기능 동작을 위해서는 <span style="color:blue">항상 invoke를 포함하여 발화를 해야 합니다. (invoke + 동작 제어 명령)</span>
- 최초 연동 시에 QR 코드를 이용하는 경우, 해당 인텐트만 Full Window with Sound로 진행합니다.

#### [GiGA Genie + IoT 단말 제어 개발 가이드 다운로드](https://docs.google.com/uc?export=download&id=1hitFPcKVAmOheIpV0O1sqV48HVEj15W1)