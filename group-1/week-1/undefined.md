# 개발환경 셋팅

### JavaScript 개발 환경 (Node.js) 세팅

* [**Node.js**](https://nodejs.org/ko/) 최신 버전인지 확인해야 한다. ⇒ 현재 기준으론 18.12.1 LTS
* [**fnm (Fast Node Manager)**](https://fnm.vercel.app/)
* <pre><code><strong>npx ts-node
  </strong></code></pre>

### TypeScript + React + Jest + ESLint + Parcel 개발 환경 세팅

작업 폴더 준비

```bash
mkdir my-app

cd my-app
```

바로 Visual Studio Code를 오픈하는 명령어

```bash
code .
```

npm 패키지를 준비

```bash
npm init -y
```

.gitignore 파일 꼭 셋팅해주기

.eslintignore파일도 셋팅. 아래 명령어들을 파일에 작성해준다.

```
/node_modules/
/dist/
/.parcel-cache/
```



타입스크립트 설정

```bash
npm i -D typescript

npx tsc --init
```

`tsconfig.json` 파일의 jsx 속성을 변경한다.

ESLint 설정

```bash
npm i -D eslint

npx eslint --init
```

`.eslintrc.js` 파일을 적절히 수정한다. 아직 Jest를 설치하지 않았지만, 여기서 미리 `jest: true`를 잡아주면 좋다.

React 설치

```bash
npm i react react-dom

npm i -D @types/react @types/react-dom
```

테스팅 도구 설치

```bash
npm i -D jest @types/jest @swc/core @swc/jest \\
    jest-environment-jsdom \\
    @testing-library/react @testing-library/jest-dom
```

`jest.config.js` 파일 작성

````
```javascript
module.exports = {
    testEnvironment: 'jsdom',
    setupFilesAfterEnv: [
        '@testing-library/jest-dom/extend-expect',
        './jest.setup',
    ],
    transform: {
        '^.+\\.(t|j)sx?$': ['@swc/jest', {
            jsc: {
                parser: {
                    syntax: 'typescript',
                    jsx: true,
                    decorators: true,
                },
                transform: {
                    react: {
                        runtime: 'automatic',
                    },
                },
            },
        }],
    },
    testPathIgnorePatterns: [
        '<rootDir>/node_modules/',
        '<rootDir>/dist/',
    ],
};
```
````

Parcel 설치

```bash
npm i -D parcel
```

`package.json` 파일의 scripts를 적절히 수정한다.
