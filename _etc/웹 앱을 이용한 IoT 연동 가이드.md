---
title: 4. 웹 앱을 이용한 IoT 연동 가이드
category: 
order: 1
date: 2019-07-25
---

> 기가지니 웹 앱 서비스로 IoT를 제어하는 방법입니다.

## 4.1 목적

**※ 기가지니 - IoT 제어의 경우 반드시 IoT Makers를 통해 개발해야 합니다.**  [링크 바로가기](<https://apilink.kt.co.kr/api/menu/apiSvcDetail.do?sysId=IOTMAKERS>){: target="_blank"}  
해당 시나리오는 <u>부득이하게</u> IoT Makers를 사용하지 못하는 경우, 기가지니 웹 앱 서비스를 기반으로 IoT 단말을 제어할 때 사용합니다.

## 4.2 동작 방식

기가지니 웹 앱 서비스에서 화면 UI 없이 제어 명령만 전달

**<span style="color:red">필수 정책</span>**  
기가지니에서 3rd Party 서버로 제어 명령 전달 후 바로 서비스 종료 처리

### 시나리오

1. 기가지니에 IoT 단말 제어 관련 발화 실행
2. IoT 단말 동작
3. 동작 후 기가지니 서비스 강제 종료

기능 동작을 위해서는 <span style="color:blue">항상 invoke를 포함하여 발화를 해야 합니다. (invoke + 동작 제어 명령)</span>  
최초 연동 시에 QR 코드를 이용하는 경우, 해당 인텐트만 Full Window with Sound로 진행합니다.

## 4.3 가이드 다운로드

[GiGA Genie + IoT 단말 제어 개발 가이드 다운로드](https://docs.google.com/uc?export=download&id=1hitFPcKVAmOheIpV0O1sqV48HVEj15W1)