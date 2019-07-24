---
title: 2.3 Service SDK 작업하기
category: 2. 서비스 개발하기
order: 3
toc: true
date: 2019-07-19
---

> 기가지니 AI Kits 중 Service SDK에 대하여 알아봅시다.

Service SDK는 기가지니 서비스를 개발하기 위한 필수 개발 KIT으로 3rd Party가 기가지니에 탑재된 음성, TTS, 녹음, 데이터 관리 기능 등을 사용할 수 있도록 Java Script API로 제공하고 있습니다.

기본적인 기가지니의 서비스 실행 구조는 다음과 같습니다. 

기가지니는 컨테이너 앱을 통해 Service SDK API를 이용하여 개발한 웹 앱 서비스를  실행시킵니다. 여기서 컨테이너 앱은 쉽게 크롬이라고 생각해주시면 됩니다.  



<img src="https://user-images.githubusercontent.com/36177711/59748833-e0849800-92b6-11e9-8cd4-ac4463251ec3.png"/>

### API 초기화

Service SDK API를 이용하기 위해서는 API 초기화가 반드시 진행되어야 합니다. 

```javascript
//callback 방식
var options={};
options.apikey="RTUwMDI5NzV8R0JPWERFVk18MTU2MDczODE2MjMzNA=="; // API Link에서 발급받은 개발 key
options.keytype="GBOXDEVM"; // 개발 환경
//options.keytype="GBOXCOMM"; // 상용 환경
gigagenie.init(options,function(result_cd,result_msg,extra){
    if(result_cd===200){
        alert('initialize success');
    };
});
```

- options.apikey : API Link에서 발급받은 개발 key를 설정합니다.
- options.keytype : 서비스 실행 환경에 맞는 keytype을 지정합니다. 
  - options.keytype = "GBOXDEVM" : 개발 환경에서 사용하는 type으로, 개발자 모드 실행 시 사용합니다.
  - options.keytype = "GBOXCOMM" : 상용 환경에서 사용하는 type으로 검증 완료 후 상용 배포시에 적용합니다.
- result_cd 값이 200으로 리턴되어야 API를 사용할 수 있습니다.

### API 공통 사항

모든 Service SDK는 callback 방식으로 호출 결과를 전달합니다. 

- gigagenie.[영역].[함수] (함수 파라미터, callback)
  - 호출 예: gigagenie.voice.getVoiceText("안녕 기가지니", null, callback)

- function callback(result_cd, result_msg, extra)
  - result_cd: 결과 코드, 숫자
  - result_msg: 결과 메세지, 문자
  - extra: 호출 결과로 전달되는 데이터로, 각 API에 따라 전달되는 데이터가 다름

API는 JavaScript Object로 제공되며, 객체를 가져오기 위해 서비스 코드 내에 다음을 Embed 해야 합니다.

```html
<script type="text/javascript" src="https://svcapi.gigagenie.ai/sdk/v1.0/js/gigagenie.js">
```

### 링크, 소스 태그의 경로 설정

3rd Party 웹 서버로 접근 시, 링크(href)와 소스(src) 태그의 경우 절대 경로를 사용해야 합니다. 3rd Party 서비스는 Base URL을 기준으로 연결됩니다. 아래 처럼 작성해야 정상적으로 접근이 됩니다.

```html
<link href = "/css/style.css" rel="stylesheet">
<script src = "/js/jquery-min.js"></script>
```

### API 전체보기

기가지니 서비스를 개발 할 때 사용할 수 있는 API 종류를 한번에 볼 수 있습니다.

- Service SDK API 전체보기 [(바로가기)](https://github.com/GiGAGenie-ServiceSDK/UserGuide/wiki/API-전체-보기){: target="_blank"}

### Service SDK 정보 등록

Service SDK는 API 제공 외에 사용자 발화문에 알맞는 서비스를 실행시키는 역할도 합니다. 이는 「My Service - Service SDK 정보 등록/수정」 에서 작업할 수 있습니다. 서비스에 대한 Invoke명, Base URL, 각 인텐트의 Service URL 등을 입력합니다. 

<img src="https://user-images.githubusercontent.com/36177711/59810297-824fc780-933f-11e9-8f6b-2db29af1445b.png"/>

#### Invoke 등록

Dialog Kit 작업 전에 가장 중요한 Invoke부터 설정합니다. Invoke는 기가지니가 3rd Party 발화문 임을 확인하는 가장 중요한 요소입니다.

<u>[Invoke 지정 관련 제약 내용]</u>  
기본적으로 Invoke는 서비스의 호출어이기 때문에, 타 서비스와 중첩되지 않도록 지정해야 합니다. 서비스의 이미지를 담고 있는 명칭으로 정해주세요. 또한 Invoke만이 서비스를 실행시키는 것이 아니고, Invoke와 Intent의 조합으로 실행되기 때문에 Invoke를 문장형태로 지정해주는 것은 제한합니다.

- **4글자 이상**
- **일반 명사만 사용 제한**
  - <u>잘못된 예</u>: 피자햄버거, 스무고개  
  - <u>옳은 예</u>: 콕콕114, 시그나 건강연구소, 롯데리아

- **문장 형태 사용 제한**
  - <u>잘못된 예</u>: ㅇㅇ피자 실행하자, ㅇㅇ서비스 보여줘 

<img src = "https://user-images.githubusercontent.com/36177711/59958677-4fdfcf00-94e5-11e9-947b-c65f5fadc719.png"/>

해당 서비스는 스무고개 서비스이므로, '지니고개'라는 Invoke를 등록하였습니다.

<img src = "https://user-images.githubusercontent.com/36177711/61193221-03a73980-a6f5-11e9-871f-24a1533b1501.png">

**입력한 Invoke를 개발 환경에서 테스트 하기 위해서는 Dialog Kit의 통합 시험 배포 과정을 거쳐야 합니다.**  통합 시험 배포 환경은 [개발 환경 배포 하기](https://ktaidevelopers.github.io/2_서비스 개발하기/개발 환경 배포하기/)에서 설명하겠습니다. 

#### URL 구성 방법

3rd Party 서비스는 Base URL + Service URL을 조합한 주소를 로딩합니다. 해당 url 정보는 API Link Service sdk 정보 등록에서 설정할 수 있습니다. Dialog Kit으로 정의 내린 발화문들에 대하여 의도에 맞는 페이지를 로딩하도록 합니다.

<h5>Base URL 설정</h5>
base url은 서비스의 웹 서버 주소를 의미합니다. 

<h5>Service URL 설정</h5>

service url은 각 인텐트 실행 시에 로드 되는 페이지 주소입니다.

<img src = "https://user-images.githubusercontent.com/36177711/61266495-fbbbc800-a7ce-11e9-83e3-8e1e88a97570.png">

인텐트는 필수로 1개 등록되어야 service sdk 정보 등록이 되므로, 서비스 실행에 대한 인텐트를 등록하겠습니다. 인텐트 실행에 대한 내용은 [Dialog Kit 작업하기](https://ktaidevelopers.github.io/2_서비스 개발하기/Dialog Kit/)과 [서비스 시작과 종료 처리](https://ktaidevelopers.github.io/2_서비스 개발하기/서비스 시작과 종료 처리/) 내용을 확인해주세요.

<img src = "https://user-images.githubusercontent.com/36177711/61259274-70353d80-a7b4-11e9-8fb3-1535b1811baa.png">

#### Window 유형 설정

기가지니 서비스에 대한 화면 구성은 세 가지 타입으로 분류 됩니다. window type에서의 with sound 와 without sound의 차이점은 해당 서비스에서 미디어 기능을 사용하는지에 대한 차이점입니다. 기가지니 TTS 에는 영향을 주지 않습니다. 

<img src = "https://user-images.githubusercontent.com/36177711/61266437-d7f88200-a7ce-11e9-9a2c-2195fb72d96c.png">

<h5>1) Full Screen</h5>

전체 화면에 대한 window type으로 일반적인 기가지니 서비스에서 사용되는 타입입니다. (1920 X 1080)

<h5>2) Overlay Screen</h5>

전체 화면이 아닌 자신이 원하는 위치와 화면 크기를 설정할 수 있습니다. 대표적인 서비스로는 '팟캐스트' 서비스가 있습니다. 기본적인 full screen 타입이 아니기 때문에 기능 제약이 있을 수 있습니다. 추가적으로 투명도 설정도 가능합니다.

<h5>3) Background Screen</h5>

기가지니 화면 없이 백그라운드로 실행되는 서비스인 경우에 해당됩니다. 대표적으로는 블루캔버스, 스마트렌탈 등의 서비스가 있으며 IoT 제어 관련 서비스일 경우 많이 사용됩니다.   
Background 서비스를 진행할 경우, 사용자가 서비스가 실행 중인지 모르기 때문에 서비스 시나리오 구성 시 더 많은 신경을 써야 합니다. 예를 들어 IoT 서비스로 어느 단말을 제어한다고 가정한다면, 기가지니가 해당 단말에 대한 제어가 끝나면 "(단말 이름) ㅇㅇ을 실행합니다."의 TTS와 함께 해당 서비스가 종료되도록 시나리오를 구성해야 합니다.  

#### Main Page 선택

마지막으로 main page는 해당 서비스에서 가장 메인으로 실행되는 인텐트(service url)를 선택하면 됩니다. 기가지니는 발화로 어느 서비스나 접근할 수 있어서 메인 페이지 개념이 따로 없지만, 해당 기능은 앱 갤러리에서 필요한 요소입니다.   
기가지니 홈 화면에서 앱 갤러리를 진입하면, 사용자는 리모컨으로 원하는 서비스를 실행시키게 됩니다. 메인 페이지가 없다면 가장 핵심이 되는 페이지를 로드하도록 선택하면 됩니다. 

#### Service SDK 적용 테스트 해보기

기가지니 개발자모드에서는 발화 실행 외에 url 입력으로도 서비스를 직접 실행해볼 수 있습니다. 해당 서비스에 대한 dialog kit 발화문 구성이 완료되지 않은 경우, 서비스 주소를 직접 입력하여 정상적으로 실행되는지 (기가지니 init이 정상적으로 되는지, 화면 UI는 문제 없는지 등) 확인해봅니다. 

<img src="https://user-images.githubusercontent.com/36177711/59584115-2e16ce80-9118-11e9-9b0c-d3ff44b3db8d.png"/>