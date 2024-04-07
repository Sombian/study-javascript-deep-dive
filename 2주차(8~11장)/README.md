# 2주차

## [영준]
## 인스턴스
클래스에 의해 생성되어, 메모리에 저장된 실체를 말한다.

객체지향 프로그래밍에서 객체는 클래스와 인스턴스를 포함한 개념이다.

클래스는 인스턴스를 생성하기 위한 템플릿의 역할을 한다.

OOP적 관점에서 객체와 인스턴스의 차이점으로는 객체는 선언, 인스턴스는 실체화를 의미한다.

인스턴스는 객체가 메모리에 저장되어, 실제로 존재하는 것에 초점을 맞춘 용어이다.

[instance란?](https://velog.io/@k7nsuy/%EC%9D%B8%EC%8A%A4%ED%84%B4%EC%8A%A4%EB%9E%80)

## 식별자 네이밍 규칙, 네이밍 컨벤션

- 식별자는 특수문자를 제외한 문자,숫자,언더스코어(_),달러 기호($)를 포함할 수 있다.
- 식별자는 특수문자를 제외한 문자,언더스코어,달러 기호로 시작해야한다. 숫자로 시작하는것은 허용하지 않는다.
- **예약어**는 식별자로 사용할 수 없다.
- 
**💡Camel Case (ECMAScript 사양에 정의)**
- userList, newTodoList, firstName…
- 첫단어의 첫글자는 소문자, 두번째 단어부터 첫글짜를 대문자로 표기.
- JAVA에서 권장되는 표기법이다.

**💡Pascal Case (ECMAScript)**
- UserList, NewTodoList, FirstName…
- 단어마다 첫글자를 대문자로 표기.
- C++에서 권장되는 표기법이다.

**Snake Case**
- user_list, new_todolist, first_name…
- 모두 소문자, 단어 사이에 _를 표시한다.
- DB에서 주로 사용된다.

**Kebab Case**
- user-list, new-todolist, first-name…
- 모두 소문자, 단어 사이에 -를 표시한다.
- url, html, css등에서 자주 사용된다.

**Scream Snake Case**
- USER_LIST, NEW_TODOLIST, FIRST_NAME…
- 모두 대문자, 단어 사이에 _를 표시한다.
- 상수를 표현할 때 사용한다.

## 템플릿 리터럴은 왜 객체 속성 키가 안 될까?
```jsx
var foo = { `bar` : 'baz' } // syntaxerror

var foo = {
	[`bar`+1] : 'baz'
}; // {'bar1' : 'baz'}
```
템플릿 리터럴은 표현식이다. 

객체 속성 키(이름)에는 문자열 리터럴(및 식별자)만 사용이 가능하다.

그 밖의 경우, 계산된 속성 이름이 필요하다.

템플릿 리터럴을 포함한 배열의 경우, 자연스럽게 문자열 변환이 가능하므로 유효한 키로 사용이 가능하다. 템플릿 표현식을 평가한 후, 배열을 문자열로 변환하기 때문이다.

⇒ 템플릿 리터럴은 표현식이다. 문자열 리터럴이 아니다! 런타임에서 문자열로 변환해주는 것이다!

[Template String As Object Property Name](https://stackoverflow.com/questions/33194138/template-string-as-object-property-name)

## 😇Object.defineProperty(obj, prop, descriptor);

객체에 직접 새로운 속성을 정의, 이미 존재하는 속성을 수정, 수정된 객체를 리턴한다.

- 프로퍼티 속성에 접근 권한을 설정할 수 있다.
- get, set을 만들 수 있다.
  
**매개변수**

- obj: 속성을 정의할 객체
- prop: 새로 만들거나 수정하려는 속성의 이름
- descriptor: 객체에 정의하는 속성을 기술하는 객체
    
    
    | 속성 | 설명 | 디폴트 값 |
    | --- | --- | --- |
    | value | 속성의 값 | undefined |
    | configurable | 속성을 변경하거나 삭제 할 경우 true 로 설정 | false |
    | writable | 속성의 값을 변경할 경우 true로 설정 | false |
    | enumarable | for-in 루프에서 해당 프로퍼티를 반환하려면 true 로 설정 | false |
    | set | 속성 설정자로 사용할 함수입니다. | undefined |
    | get | 속성 접근자로 사용할 함수로 속성 접근시 해당 함수의 반환값이 속성의 값이 됩니다. | undefined |
  
**get, set**

JAVA의 getter, setter와 같은 기능을 한다.

```jsx
const person = {};
let personName = '';

Object.defineProperty(person, 'name',{
  set(value) { personName = `${value}-set`; }, 
  get() { return `get-${personName}`; },
}); 

person.name = 'sungin'; // set을 통해 sungin-set 으로 설정
console.log(person.name);  // get을 통해 get-sungin-set 으로 설정
```

[JAVA) 자바 Getter/Setter 의미와 왜 사용하는지 알아보자](https://luanaeun.tistory.com/141)

[Object.defineProperty() - JavaScript | MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty)

## [민재]

## [건]
- JavaScript 에서도 label 을 부여해서 선택적 break 가 가능하다는 것을 알게되었다.

## [혜린]
##### 1. 함수 선언식에는 세미콜론이 없는데 왜 함수 표현식의 끝에는 세미콜론이 붙을까?

```
function sayHi() {
  // ...
}

let sayHi = function() {
  // ...
};
```

일반적으로 코드를 작성할 때 함수 표현식에서는 세미콜론을 붙히고 함수 선언식으로 작성할 시에는 ;(세미콜론)을 붙이지 않는다.

if { ... }, for { }, function f { } 같이 중괄호로 만든 코드 블록 끝엔 세미콜론이 없어도 된다. 이유는 블록문은 언제나 문의 종료를 의미하는 자체 종결성을 갖기 때문이다.

반면 함수 표현식은 let sayHi = ...;과 같은 구문 안에서 값의 역할을 한다. 따라서 코드 블록이 아니고 값처럼 취급되어 변수에 할당된다. 

모든 구문의 끝엔 세미콜론을 붙이는 것이 좋다. 함수 표현식에 쓰인 세미 콜론은 함수 표현식 때문에 붙여진 게 아니라, 구문의 끝이기 때문에 붙여졌다.

----

##### 2. 리액트에서 컴포넌트를 선언할 때 함수 선언식 vs 함수 표현문

- 함수 선언식
```
export default function Greeting() {
  ...
}
```
- 함수 표현식
```
const Greeting = () => {}
export default Greeting;
```

- 함수 선언식 vs 함수 표현문 차이점

1) 호이스팅 여부

함수 선언식의 경우 호이스팅이 가능. 따라서 선언부를 모두 모듈 하단에 내려놓고, 메인 로직만 상단에 배치함으로써 가독성을 높일 수 있음

2) export default를 선언과 동시에 할 수 있는가

export default와 함수 선언을 동시에 한다는건 무슨 의미일까?
default로 내보내는 함수는 그 모듈의 메인 로직 일테고, 이는 코드를 보는 사람으로 하여금 가장 중요한 로직이 무엇인지 인지시킬 수 있다. 
또한 한 줄에 작성할 수 있어서 편리하다.

- 그렇다면 컴포넌트 내부 함수는 어떻게 할까?

컴포넌트 내부의 함수는 기본적으로 선언식으로 작성하되, 필요에 따라 표현식을 사용한다.

1) 인자전달 
```
const Greeting = (name) => {
  return `Hello, ${name}!`;
};

console.log(Greeting("John")); // Hello, John!
```
2) 즉시 실행 함수

즉시 실행 함수는 스코프 내에서 한 번 호출하고 사용되지 않는다. 
또한 호출 뒤 참조가 불가능해서 스코프의 오염을 막아준다. 따라서 즉시 실행 함수를 사용할 거라면 굳이 함수 이름을 정의해줄 필요가 없다.
```
const result = (() => {
  const x = 10;
  const y = 20;
  return x + y;
})();

console.log(result); // 30
```
