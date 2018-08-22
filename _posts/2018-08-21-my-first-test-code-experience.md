---
title: '배민찬 프로젝트에서의 Front-End Test Code 작성 경험기'
tag: [ test ]
---

(작성중) 

처음 작성해보는 테스트코드라 시행착오가 많았고,  노하우가 없어서 고민할 거리가 많았던 경험이었다.  
테스트는 이론보다 이런 경험을 잘 누적해두는게 더 중요하다 생각되어 글로 정리해놓기로 마음먹었다.

## 공부순서

- 1: 테스트 환경구성
  - 사용할 라이브러리 검색, 호환성 체크 및 환경구성, 테스트용 폴더구조 구성
- 2: (테스트라는 환경에 들어가기 위한) 최소한의 테스트 이론 공부
  - 주요 키워드 파악이 목적
- 3: 라이브러리 기초 익히기
  - 공식문서 + 구글검색
- 4: 테스트코드 작성 + 공부 (오픈소스 테스트 코드 벤치마킹, 그때그때 필요한 내용) + 고민과정 메모
  - ⇒ 이 단계부터는 위의 3가지를 계속 반복했다.

## 테스트 환경구성은 아래와 같다.

- Unit Test ⇒ test.html을 만들고 node server로 라우팅하여, 브라우저에서 확인
  - mocha.js (test framework)
  - chai.js (assertion library)
  - sinon.js (test double library)
- E2E Test (가볍게 경험) ⇒ node.js로 확인
  - testcafe (e2e node module)

## 테스트 결과

### [unit] helpers.test.js (유틸 메서드 모음)

![helpers.test.js결과화면](https://user-images.githubusercontent.com/23192677/44468605-8b5d0300-a660-11e8-906d-ee805bc65e1a.png)

### [unit] AutoCompleteSearcher.test.js (자동완성검색 UI)

![AutoCompleteSearcher.test.js결과화면](https://user-images.githubusercontent.com/23192677/44468631-9ca60f80-a660-11e8-93bb-e7d1d1c1241c.png)

### [e2e] autoCompleteSearcher.test.js

![autoCompleteSearcher.test.js결과화면-01](https://user-images.githubusercontent.com/23192677/44468655-adef1c00-a660-11e8-9f95-0be8286d71a0.png)
![autoCompleteSearcher.test.js결과화면-02](https://user-images.githubusercontent.com/23192677/44468670-b3e4fd00-a660-11e8-9180-580215cf15bd.png)

---

## 테스트 주요 키워드 파악하기

처음에는 라이브러리를 먼저 공부하려 했으나 자꾸 생소한 용어가 나와서 찾아 보니 소프트웨어 테스트 분야에서 통용되는 용어라는 것을 알게 되어 키워드 파악을 목적으로 공부를 했다.

주요 키워드는 아래과 같았다.

- 유닛 테스트=단위 테스트(unit test), 통합 테스트(integration test), E2E 테스트
- 테스트 프레임워크, 단언문(assertion), 테스트 커버리지(test coverage), 테스트 더블(test double, spy, stub), 테스트 케이스(test case)


## 테스트 코드 설계

테스트 코드는 기존 코드의 로직을 보지 않고도 명세와 테스트 타겟의 속성명, 메소드명 만으로도 잘 읽혀야 하기에 개발이라기보다 문서를 코드로 작성한다는 느낌이 들었다.

그렇기 때문에 **가독성, 특히 일관성있는 코드 구조**가 필요하다고 생각되어 아래와 같은 규칙들을 세우고 일관성있게 작성하려고 하였다.

이런 규칙을 가지고 작성하게 되면, 실제코드의 수정이 일어날 때마다 어디서 무엇을 테스트 하는지 빨리 파악하고 대응할 수 있어 관리가 용이할 거라 생각되었다.

### 1. **시각적/기능적으로 읽기 쉬운 구조로 테스트 그룹짓기**



## 테스트코드 작성 중 만났던 고민과 해결책



## (테스트를 통한) 기존코드 수정사항

밸리데이션

- storage가 구조를 제안한 parentStorage를 상속받지 않았을 경우 에러를 throw하도록 수정 (_checkModule)
- 클래스 생성시 필수옵션인  wrapperElem이 없을 경우 에러를 throw하도록 수정
- 벨리데이션을 이상하게 하고 있던 부분이 확인되어 수정

코드 가독성

- 변수명: 목적이 명확하게 보이지 않는 이름을 많이 개선
- 메서드 선언순서 : 동작이 발생되는 순서로 일부 개선하여 코드파악을 쉽게 함

(언젠가는 문제가 될 수도 있었던) 티 안나던 기능실수 개선

- 자동완성 목록을 close하는 메서드가 중복되는 시나리오가 있다는 걸 알게 되어 개선함. (spy로 호출 횟수를 expect 하던 중)

기타 개선

- 스토리지 이름을 종류별로 (최근목록, 검색응답데이터) 받던 것을 --> 대표이름 하나만 받게 하고 내부적으로 두 개로 나눠 사용하게 하여 개발자를 위한 UX 개선

다행히 리팩토링을 많이 한 덕인지 함수를 더 쪼개야 하는 식의 리팩토링은 많이 없었던 거 같다.
일부 코드만 작업하였기 때문에, 모두 테스트한다면 또 다른 식의 리팩토링을 하게 될 수도 있겠다 생각함.

## 느낀 점


## 좀 더 발전하고 싶은 방향


