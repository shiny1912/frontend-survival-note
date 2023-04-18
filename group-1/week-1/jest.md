# Jest

**Jest**

expect로 assertion할 수 있다. Mocking도 쉽게 사용 가능.

```
Function add(x:number, y:number): number {
return x + y;
}
```

```
Test('숫자 더하기', () => {
 expect(add(1,2)).toBe(3);
});
```

```
Screen.getByText(\Hi\); -> 정규표현식도 가능
```



**React Testing Library**

UI 테스트 라이브러리. 테스트 코드를 많이 작성하면 오히려 유지보수 할 때 로드가 더 많이 들어갈 수 있다.
