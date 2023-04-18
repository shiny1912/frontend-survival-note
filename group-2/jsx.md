# JSX

**ECMAScript**

JSX는 React의 부산물이지만 꼭 React에서 사용되는건 아니다.

&#x20;

\<name>홍길동\</name>



JSX는 XML을 React.createElement 를 쓰는 Javascript 코드로 변환해준다.

Babel.js.io 에서 React를 JSX로 변환하는 내용을 실험할 수 있다.

&#x20;

**JSX코드**

\<p>Hello, world!\</p>

변환된 JS코드

React.createElement("p", null, "Hello world!");

JSX파일에 /\*@jsx 어쩌고 \*/ 주석을 추가하면 React.createElement대신 "어쩌고"를 쓰게 된다.

Tree

JSX와 Javascript는 상호 호환이다.

JSX Runtime

Preact

&#x20;

VDOM

React Developer Tools

&#x20;

&#x20;

**React Developer Tools**

Strict Mode를 쓰지 않으면 경고한다.

&#x20;

**VDOM**

트리 = 한방향 구조로 무조건 간다.

VDOM을 쓰는 이유는?

VDOM이 더 빠르다기 보다는, 충분히 빠르기는 하다. 근데 유지하기에 좋은 것은 확실하다. (핵심)

React는 선언형 UI라는 더 좋은 구조를 제공한다.

최적화 할 수 있는 여러가지 방법들이 존재한다: production. Rollup. 등등..

긴 목록을 가상화하세요 : 적절히 slice해서 렌더링하기

Key 만들어주기(비교를 위해)

컴포넌트 분할하는 방법에 따라서 최적화시켜서 속도를 빠르게 만들 수 있다.
