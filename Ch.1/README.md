# 1-1 변수 선언
var a : 식별자, 변수명 variable a 등으로 불림

# 1-2 변수 선언과 할당
var a : 변수 a 선언

a = 'abc' : 변수 a에 데이터 할당

var a = 'abc' : 변수 선언과 할당

# 1-3 불변성
모든 기본형 데이터는 모두 immutable

# 1-4 참조형 데이터의 할당
a 와 b는 identifier 또는 property

1과 'bbb'는 data 또는 value

obj1, a, b 는 모두 identifier area에 존재, {}, 1, 'bbb'는 data area에 존재

# 1-5 참조형 데이터의 프로퍼티 재할당
obj1이 reference type 데이터를 가리킴

reference type 데이터는 실질적 data인 1,'bbb'를 가리킴

# 1-6 중첩된 참조형 데이터(객체)의 프로퍼티 할당
array의 값을 index를 통해 통제

x와 arr의 3은 data area의 같은 3을 가리킴

# 1-7 변수 복사
10과 'ddd' 같은 primitive type은 immutable

똑같은 값을 할당 또는 복사할 때 data가 새로 생성되지 않고 원래 있던 주소 활용

# 1-8 변수 복사 이후 값 변경 결과 비교 (1) - 객체의 프로퍼티 변경 시
기존 객체의 c 값이 변하는 것이 아닌 새로운 데이터 20을 가리키는 주소를 할당

# 1-9 변수 복사 이후 값 변경 결과 비교 (2) - 객체 자체를 변경했을 때
내부 property를 변경할 때는 기존 data를 변경하는 것이 아니라 새로운 객체를 할당하는 것이 좋음

위와 같이 할당할 경우 기존 c와 d는 불변

# 1-10 객체의 가변성에 따른 문제점
user object가 변하면서 새로운 값만 기억하고, 이전의 값을 삭제한다는 문제점 발생

변경 전과 후에 서로 다른 객체를 바라보게 만드는 것이 좋음

# 1-11 객체의 가변성에 따른 문제점의 해결 방법
예제 10에서 changeName의 함수를 위와 같이 변경하면 가변성에 의한 문제점 해결

# 1-12 기존 정보를 복사해서 새로운 객체를 반환하는 함수(얕은 복사)
copyObject 함수는 result 객체에 target 객체의 프로퍼티를 복사하는 함수 (얕은 복사)

# 1-13 copyObject를 이용한 객체 복사
예제 12번에서의 copyObject를 활용한 예제

# 1-14 중첩된 객체에 대한 얕은 복사
예제 12번에서의 copyObject를 활용한 예제

얇은 복사의 문제점을 확인할 수 있는 예제

user.urls 프로퍼티에 대해서도 불변 객체로 만들 필요가 있음

# 1-15 중첩된 객체에 대한 깊은 복사
14번까지의 copyObject를 위와 같이 수정

깊은 복사를 통해 얕은 복사로 인해 발생하는 문제점을 해결

# 1-16 객체의 깊은 복사를 수행하는 범용 함수
재귀적 방법을 이용해 범용성 있는 깊은 복사 함수를 구현

# 1-17 깊은 복사 결과 확인
예제 16에서 구현한 함수를 활용한 결과를 확인하는 예제

# 1-18 JSON을 활용한 간단한 깊은 복사
JSON과 객체 간의 변환을 이용한 깊은 복사

JSON으로 변환시 string으로 변환되기 때문에 순수 data만 copy되는 단점이 존재

# 1-19 자동으로 undefined를 부여하는 경우
undefined를 할당하는 것은 혼동을 가져오기 때문에 null을 할당하는 것을 권장

undefiend는 자바스크립트 엔진만 사용하는 것이 좋음

undefined가 부여되는 상황을 보여주는 예제

# 1-20 undefined와 배열
빈 array에 대해서는 empty와 undefined가 구분이 힘든 문제점이 발생

undefined를 사용하는 것은 권장되지 않음

# 1-21 빈 요소와 배열의 순회
undefined를 할당한 경우 empty가 아니라 실제 undefined가 할당된 것

비어있는 index의 경우 forEach 함수가 실행되지 않음

# 1-22 undefined와 null의 비교
null인지 undefined인지 확실히 구별하기 위해서는 동등 연산자를 활용

null의 type이 object로 나옴
