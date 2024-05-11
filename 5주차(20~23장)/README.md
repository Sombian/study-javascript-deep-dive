# 5주차

## [건]

JS 도 Java 처럼 Primitive Class <-> Wrapper Class 를 자동적(Out-of-Box)으로 변환한다.

## [민재]

새롭게 알게된 개념이라기 보다 헷갈리는 개념입니다.

| 함수 호출 방식 | this바인딩 |
| --- | --- |
| 일반 함수 호출 | 전역 객체 |
| 메서드 호출 | 메서드를 호출한 객체 |
| 생성자 함수 호출 | 생성자 함수가 (미래에) 생성할 인스턴스 |
| Function.prototype.apply/call/bind 메서드에 의한 간접 호출 | Function.prototype.apply/call/bind 메서드에 첫 번째 인수로 전달된 객체 |
