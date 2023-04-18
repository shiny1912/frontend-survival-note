# React Hooks

초기화 해주기

```
npm init -y
```

&#x20;.gitignore 파일 생성 빼먹지 말기

```html
echo "/node_modules/" > .gitignore
```

&#x20;

Typescript 설치

```
Npm i -D typescript
```



Tsconfig 파일 만들기

```
npx tsc --init
npm i -D ts-node
```



```
Npm i -D eslint
Npx eslint --init
Npm i express
Npm i -D @types/express
Npm i -D nodemon
Npx nodemon app.ts
```

필딩 제약 조건

&#x20;

Fetch api : fetch 라는 함수를 쓴다.&#x20;

useRef() : 각자 하나씩 참조를 갖고 싶을 때 사용한다.

Ref.current 를 사용 가능하다.

&#x20;

```
Const {
 filterText, setFilterText, ...
} = useProductsFilter(products);
```

재활용 가능하도록 따로 뺀다.

&#x20;

Hook 규칙

&#x20;

Usehooks-ts

&#x20;Custom hooks를 직접 만들어서 사용하면 좋고, 테스트 코드 작성할 때도 좋다.
