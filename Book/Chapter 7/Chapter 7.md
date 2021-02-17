# Chapter 7. 고급 컴포넌트와 라우팅

## 7.1 슬롯 사용

컴포넌트를 사용할 때, 컴포넌트에 데이터를 전달하기 위해 보통 부모 콘텐츠와 자식 콘텐츠를 엮어야 할 때가 있다.

컴포넌트를 사용할 때 시작과 끝 내그 사이에는 콘텐츠를 추가할 수 없다.

콘텐츠를 보여 줄 수 있는 가장 쉬운 방법은 슬롯 요소를 사용하는 것이다.  
이는 Vue의 slot 요소를 사용하면 된다.  
슬롯 요소는 Vue.js에서 컴포넌트의 시작과 끝 태그 사이에 추가된 데이터를 어딘가에 표시해야 할 때 사용하는 특별한 태그다.  
다른 자바스크립트 프레임워크에서는 이러한 과정을 content distribution(콘텐츠 분배)이라고도 한다.

- parent-child.html
- parent-child-slots-extract.html

## 7.2 지정 슬롯 살펴보기

지정 슬롯은 일반 슬롯과 같지만, 컴포넌트 안에 구체적으로 배치할 수 있다는 점이 다르다.  
이름 없는 슬롯과 다르게 컴포넌트에 여러 지정 슬롯을 가질 수 있다.  
해당 지정 슬롯을 컴포넌트의 원하는 곳에 어디든지 배치할 수 있다.  
추가하려면 먼저 자식 컴포넌트 안의 어느 곳에 추가할지 정의해야 한다.

지정 슬롯은 다양한 곳에서 쉽게 요소를 부모에서 자식 컴포넌트로 추가할 수 있게 한다.

- named-slots.html

## 7.3 범위 슬롯

범위 슬롯은 지정 슬롯과 비슷하지만, 데이터를 넘겨줄 수 있는 재활용 가능한 템플릿에 더 가깝다.  
범위 슬롯을 사용하려면 slot-scope라는 특별한 요소를 이용하는 템플릿 요소를 써야 한다.  

slot-scope 요소는 컴포넌트로 넘겨받은 속성을 담고 있는 일시적인 변수다.  
자식 컴포넌트로 값을 넘겨주는 대신 자식 컴포넌트에서 다시 부모로 값을 넘겨줄 수 있다.