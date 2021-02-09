# Chapter 3. 상호 작용성 추가

애플리케이션에 상호 작용성을 추가한다는 것은 DOM 이벤트를 연결하고, 이를 애플리케이션 코드 내에서 응답하고, 사용자에게 해당 행동에 대한 피드백을 제공하는 것을 의미한다.
Vue는 모든 이벤트와 데이터 바인딩을 생성하고 관리하지만, 애플리케이션에서 어떻게 데이터를 조회하고 어떻게 인터페이스로 사용자 기대를 충족시킬지 결정해야 한다.

## 3.1 장바구니 데이터는 배열 추가로 시작

- add-array.js

## 3.2 DOM 이벤트에 바인딩

애플리케이션의 상호 작용 요소를 추가하려면 Vue 인스턴스에서 정의한 함수를 DOM 요소에 연결해야 한다.
이벤트 바인딩을 사용해서 click, mouseup, keyup 등 기본 DOM 이벤트와 요소를 연결할 수 있다.

### 3.2.1 이벤트 바인딩 기초

이벤트 바인딩은 v-on 지시자를 사용해서 단편 자바스크립트 코드나 함수를 DOM 요소에 연결한다.
해당 코드나 함수는 DOM 이벤트가 트리거될 때 실행된다.

```vue
<p v-on:eventname="some javascript"></p>
```



자바스크립트에서 이벤트 바인딩은 다음 두 가지 공통된 패턴이 있다.

1. 함수 이름을 사용해서 인스턴스에서 정의한 함수를 이벤트에 연결할 수 있다.
   v-on:click="clickHappened" 같은 바인딩이 있다면, 요소를 클릭했을 때 clickHappened 함수가 호출된다.
2. 노출된 속성 역할을 하는 인라인 자바스크립트를 작성할 수 있다.
   이때는 바인딩이 v-on:keyup="characterRemaining -= -1"처럼 보이는데, 이 이벤트는 characterRemaining 속성 값을 1씩 감소시킨다.

### 3.2.2 <장바구니 담기> 버튼에 이벤트 연결

마크업에 버튼을 추가하기 전에 함수를 먼저 작성해야 한다.
그러려면 애플리케이션 옵션에 method 객체를 추가해야 한다.

- add-to-cart.js
- button-product.js

## 3.3 <장바구니 담기> 버튼을 추가하고 개수 세기

계산된 속성은 다른 속성과 마찬가지로 인스턴스에서 정의되며, DOM에 묶여 있다.
하지만 일반적으로는 애플리케이션의 현재 상태에서 새로운 정보를 가져오는 기능을 제공한다.

### 3.3.1 계산된 속성은 언제 사용할까?

data 객체의 속성을 데이터베이스에 저장하는 대표 데이터로 생각하고, 계산된 속성을 뷰 맥락에서 주로 사용되는 역동적인 값으로 생각하는 것이 이해하기 쉽다.

계산된 속성을 사용할 때 또 다른 이점은 애플리케이션에서 다른 혹은 추가 데이터를 사용하는 함수의 내부를 바꿀 수 있다는 것이다.

이렇게 계산된 속성을 사용하면 백엔드나 데이터베이스를 바꿀 필요 없이 어떤 인스턴스 데이터라도 합치거나 조작할 수 있다.

- computed.js

### 3.3.2 계산된 속성으로 업데이트 이벤트 살펴보기

계산된 속성은 보통 인스턴스 데이터를 사용해서 계산되므로, 기본 데이터가 변경되면 값이 자동으로 업데이트된다.
그래서 계산된 속성에 연결된 모든 뷰 마크업은 새 값을 반영하기 위해 업데이트된다.

- computed-react.js
- area.html

### 3.3.3 장바구니에 담긴 상품 개수 표시 및 테스트

- cart-item-count.js
- cart-indicator.html

## 3.4 버튼에 사용자 편의 추가

사용자 편의를 쓰는 이유는 시각적인 큐와 피드백을 사용자에게 제공해서 사용자 기대치에 맞는 애플리케이션을 유지하려는 것이다.

### 3.4.1 재고 주시

- available-inventory.js

### 3.4.2 계산된 속성과 재고 작업

- computed-remaining.js

### 3.4.3 v-show 지시자 기초

v-show 지시자는 지정된 조건이 참일 때만 마크업을 렌더링한다.

표현식이 거짓이면, Vue는 인라인으로 CSS의 display 속성을 none으로 지정한다.
이는 뷰에서 요소를 효과적으로 숨길 수 있지만, DOM에는 여전히 남아 있다.
나중에 표현식이 참을 반환하면 인라인 스타일이 제거되고, 사용자는 다시 해당 요소를 볼 수 있다.

또 염두에 두어야 할 점은 v-show 지시자는 여러 근접한 요소보다 하나에 연결되어 있을 때 가장 효율적이다.

정확하게는 애플리케이션 어디에서나 v-show를 사용해도 된다.
성능을 더 좋게 하는 것과 코드 요소를 같이 변경하는 것을 깜빡할 수 있기 때문에 가능하면 데이터에 반응하는 여러 요소를 합치는게 가장 좋다.

- button-v-show.html
- wrap-content.html

### 3.4.4 v-if와 v-else를 사용해서 버튼 활성화

사용자에게 비활성화된 버튼을 렌더링해서 보여 주는 것이 더 유익할 수 있다.
이렇게 해야 최대한 인터페이스의 연속성을 흐리지 않고, 레이아웃을 유지하기 때문이다.

v-if와 v-else 지시자는 주어진 표현식의 진릿값에 따라 두 가지 선택 중 하나를 표시하는 데 사용된다.

v-if와 v-else를 같이 사용할 때 마크업에는 조건이 참일 때 사용할 것과 거짓일 때 사용할 요소가 2개 필요하다.
추가로 이 두 요소는 마크업에 나란히 나열해야 Vue가 올바르게 바인딩할 수 있다.

v-if와 v-else 지시자를 사용해서 Vue.js는 DOM에서 거짓일 때 한 요소를 제거하고, 참일 때 다른 요소를 제거한다.
이 모든 과정은 DOM에 단일 혹은 동시 업데이트의 일부로 이루어진다.

v-show 지시자를 사용할 때는 v-if와 v-else를 붙일 수 있는 단일 컨테이너 요소가 있어야 한다.
특히, v-else 마크업은 무조건 v-if 마크업에 붙어 있어야 한다.

- v-if-and-v-else.html
- single-container.html

### 3.4.5 토글 기능이 있는 <장바구니 담기> 버튼 추가

삼항 연산자는 if 문의 단축문이며 매개변수가 3개 있다.
첫 번째 매개변수는 조건이다.
참이면 첫 번째 표현식을 거짓으로 반환한다.
거짓이면 마지막 표현식을 참으로 반환한다.
삼항 조건 연산자는 빠르게 조건문을 만들어야 할 때 아주 유용하다.

- cart-button.js
- add-cart-button.html

### 3.4.6 v-if를 사용해서 체크아웃 페이지 표시

- v-if-checkout.html

### 3.4.7 v-show와 v-if/v-else 비교

사용자와 개발자 모두에게 v-show와 v-if/v-else는 둘 다 장단점이 있다.
알다시피 v-show 지시자는 CSS를 사용해서 요소를 숨기거나 보여 주는 반면, v-if/v-else 지시자는 DOM에 콘텐츠를 제거한다.

v-show 지시자는 '다른' 사례가 없을 때 가장 적합하다.
조건이 참일 때 보여 줄 마크업은 있는데, 거짓일 때 보여 줄 콘텐츠가 없을 때를 의미한다.

v-if와 v-else 지시자는 마크업 덩어리 2개 중 하나가 렌더링되어야 할 때 적합한 선택이다.
하지만 둘 중에 적어도 하나는 무조건 보여야 한다.

## 3.5 연습 문제

## 3.6 요약

- 계산된 속성으로 데이터 객체 안에 없는 데이터를 표시한다.
- v-if와 v-else 지시자를 사용해서 조건에 따른 애플리케이션 일부를 보여 준다.
- 메서드를 사용해서 애플리케이션에 더 많은 기능을 추가한다.