# Typescript

**Typescript**

* Node.js

ReactNode 처럼 레거시 코드도 있기 때문에 타입을 적용해줘야 한다.

Visual Studio Code의 자동 완성 + 실시간 오류 검사 기능이 있어서 편하다.

* Interface vs Type

Type이 더 오래된 개념이다.

* 타입 추론

모든 것을 작성하지 않아도 어느 정도 검사해 준다.

* Union Type

Union Type : 합집합.

```
type bool = true | false;
```

매개변수 제한시에도 유용하게 쓸 수 있다.

다른 타입을 적으면 빨간줄로 에러 체크해줌.&#x20;

* Optional Parameter

&#x20;Undefined로 파라미터를 받는 경우

```
function add(x:number, y?:number)
```

* Intersection Type

type을확장한 것과 비슷한 개념

```
type  Person = Human & Creature;
```

Interface의 merging개념을 활용하고 싶을 때가 아니라면 type을 쓰는 것이 코드가 더 일관성 있게 된다.
