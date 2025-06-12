# Ch.7 클래스, 상속, 추상화

## 7-1 스태틱 메서드와 프로토타입 메서드

생성자 함수로 만든 인스턴스는 프로토타입 메서드에 접근 가능함.  
그러나 생성자 함수에 직접 붙은 메서드는 인스턴스에서 접근할 수 없음.  
이런 메서드를 스태틱 메서드라고 부름.

---

## 7-2 Grade 생성자 함수와 다중 프로토타입 체이닝

Grade 생성자는 배열처럼 동작하도록 설계되었음.  
`Grade.prototype`을 배열로 설정함으로써 배열 메서드를 사용할 수 있음.  
하지만 `length`가 configurable하다는 점과 `prototype`에 데이터를 포함시켰다는 문제가 있음.

---

## 7-3 length 프로퍼티 삭제의 영향

Grade 인스턴스는 객체로써 `length`를 삭제할 수 있음.  
배열과 달리 `length`가 configurable이기 때문.  
삭제 이후 push를 수행하면 비정상적으로 동작함.  
내장 배열 객체와는 다르게 동작함에 주의해야 함.

---

## 7-4 prototype에 요소가 있는 경우의 문제

`Grade.prototype`에 데이터를 포함시키면 인스턴스에 예기치 못한 영향이 생길 수 있음.  
이는 클래스의 추상성을 해치는 것으로, 바람직하지 않음.

---

## 7-5 Rectangle과 Square 클래스 구조

Rectangle과 Square 클래스는 유사한 구조를 가짐.  
`getArea` 메서드는 내용만 조금 다르며, 구조적으로 비슷함.  
`Square`가 `Rectangle`을 상속받도록 변경하면 중복을 줄일 수 있음.

---

## 7-6 Square 클래스 구조 변경

`Square`에서 `height`를 `width`와 동일하게 설정하면  
`getArea` 메서드를 `Rectangle`과 동일하게 사용할 수 있음.  
이로 인해 상속이 가능한 구조로 바뀌게 됨.

---

## 7-7 Rectangle을 상속하는 Square 클래스

`Square` 생성자 내에서 `Rectangle` 생성자를 직접 호출하고,  
`prototype`을 `Rectangle` 인스턴스로 설정함.  
하지만 여전히 구체적인 데이터를 지니고 있어서  
완전한 추상적 상속 구조라고 보기 어려움.

---

## 7-8 클래스 상속 및 추상화 (방법 1: 인스턴스 생성 후 프로퍼티 제거)

`SuperClass`로부터 상속받은 후,  
`prototype`의 구체적인 데이터를 삭제하고,  
`Object.freeze`로 고정함.  
이는 추상성을 확보하는 방법 중 하나임.

---

## 7-9 클래스 상속 및 추상화 (방법 2: 빈 함수 활용)

Bridge라는 빈 함수를 사용하여  
`SubClass.prototype`이 `SuperClass.prototype`을 바라보게 함.  
`Bridge`를 클로저로 감싸 메모리 낭비를 줄임.  
이 방식은 프로토타입 연결 구조를 안전하게 유지함.

---

## 7-10 클래스 상속 및 추상화 (방법 3: Object.create)

`Object.create(SuperClass.prototype)`를 사용하여  
`SubClass.prototype`을 설정함.  
이 방법은 `SubClass`가 `SuperClass`의 인스턴스가 되지 않으므로  
보다 안전하고 간결한 상속 구조를 제공함.

---

## 7-11 상속 및 추상화 완성본 (방법 1)

`extendClass1` 함수에서 `constructor`를 명시적으로 재설정함.  
기존 방식의 단점을 보완함.  
이제 `SubClass.prototype.constructor`가 정확히 자신을 가리킴.

---

## 7-12 상속 및 추상화 완성본 (방법 2)

빈 함수 방식에서도 `constructor`를 명시적으로 재설정함.  
구조는 유지하되, `prototype.constructor` 정합성을 확보함.

---

## 7-13 상속 및 추상화 완성본 (방법 3)

`Object.create`를 이용한 방식에서도  
`SubClass.prototype.constructor`를 명확히 설정함.  
안정성과 추상성 면에서 가장 권장되는 방식임.

---

## 7-14 super 메서드 구현

`SubClass.prototype`에 `super` 메서드를 추가하여  
상위 클래스의 생성자나 메서드에 접근할 수 있도록 함.  
ES6의 `super` 키워드를 흉내낸 구조로  
직접 구현한 슈퍼 호출 기능을 제공함.

---

## 7-15 ES5 vs ES6 클래스 문법 비교

ES5에서는 생성자 함수와 프로토타입을 활용하여 클래스 구현함.  
ES6에서는 `class` 문법을 제공하여 구조화가 간편해짐.  
정적 메서드와 인스턴스 메서드 구분이 명확해짐.

---

## 7-16 ES6 클래스 상속과 super

ES6에서 `extends`와 `super()`를 통해  
상위 클래스의 생성자와 메서드에 손쉽게 접근 가능해짐.  
이전 장에서 직접 구현한 `super` 메서드와 비교 가능함.

---
