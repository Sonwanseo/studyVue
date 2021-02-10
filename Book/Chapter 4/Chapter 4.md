# Chapter 4. 폼과 입력

## 4.1 v-model 바인딩 사용

애플리케이션의 모델 바인딩은 템플릿을 사용하여 사용자 입력 데이터의 업데이트를 도와준다.

v-model은 주로 입력과 폼 바인딩에 사용된다.
v-bind는 주로 HTML 속성 바인딩에 사용된다.

v-on 지시자는 DOM 요소에 함수를 바인딩할 수 있다.

Vue 생성자는 애플리케이션 안에서 트리거되는 모든 함수를 포함한 methods 객체를 가지고 있다.

- first-last.html
- data-property.js
- text-input.html
- data-new-properties.js
- adding-buttons.html
- more-props.js
- adding-v-on.html

## 4.2 값 바인딩 살펴보기

### 4.2.1 체크 박스에 값 바인딩

v-bind 지시자는 HTML 요소의 속성에 값을 바인딩한다.

- true-false.html
- prop-gift.js

### 4.2.2 값 바인딩과 라디오 버튼 작업

체크 박스와 마찬가지로 라디오 버튼에도 값을 지정할 수 있다.
값을 직접 바인딩하면 된다.

- radio-bind.html
- update-order.js

### 4.2.3 v-for 지시자 알아보기

v-for 지시자는 코드나 객체 내 값을 쉽게 나열할 수 있게 한다.

- bind-select.html
- states.html
- select-drop-down.html
- options.html
- detour.html

## 4.3 수식어 살펴보기

v-model은 입력 값에 바인딩할 수 있다.
해당 값은 각각의 입력 이벤트에 따라 업데이트된다.
v-model 지시자를 사용한 수식어로 작동 방식으로 바꿀 수 있다.

### 4.3.1 .number 수식어 사용

.numbers 수식어는 v-model 지시자 값을 숫자로 자동 타입 변환할 때 사용한다.

HTML 입력은 type="number"를 추가해도 항상 문자열을 반환한다.
.number 수식어를 사용하면 해당 현상을 방지하고 숫자를 반환한다.

- number-mod.html
- type-of.html

### 4.3.2 입력 값 다듬기

.trim 수식어는 자동으로 모든 여백을 없앤다.

- trim-mod.html
- trim-mod-add.html

### 4.3.3 .lazy v-model 수식어

v-model 지시자는 각 입력 이벤트 이후에 동기화된다.
실제로는 텍스트 박스에서 글자를 입력할 때마다 일어나므로 값이 키 입력마다 동기화되는 것이다.

.lazy 수식어는 대신 on change 이벤트에 동기화된다.

## 4.4 연습 문제

## 4.5 요약

- v-model 지시자는 입력, 셀렉트, 텍스트 영역, 컴포넌트 바인딩에 사용한다.
  이는 폼 입력 요소와 컴포넌트에 양방향 데이터 바인딩을 생성한다.
- v-for 지시자는 주어진 데이터에 따라 데이터를 여러 번 렌더링한다.
  순환하고 있는 현재 요소의 표현식에 별칭을 사용할 수 있다.
- v-model 지시자에는 .trim, .lazy, .number 수식어가 있다.
  .trim 수식어는 공백을 제거하고 .number 수식어는 문자열을 숫자로 타입 변환한다.
  .lazy 수식어는 데이터가 동기화되면 변경된다.