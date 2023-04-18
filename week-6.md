---
description: 상태관리
---

# Week 6

### 관심사의 분리

각 부분은 하나의 역할, 하나의 관심사로 격리됨으로써 복잡도를 낮추게 된다.

널리 알려진 MVC로 거칠게 매핑하면 다음과 같다.

* Model → Process
* View → Output
* Controller → Input

### Flux Architecture

Redux는 아래와 같이 반영된다.

1. Action
2. Store → dispatch를 통해 Action을 받고, 사용자가 정의한 reducer를 통해 State를 변경한다.
3. View → State를 반영.

[**External Store**](#user-content-fn-1)[^1]

상태가 바뀌면 해당 컴포넌트의 하위 컴포넌트를 다시 렌더링해줘야 한다.

```
function useForceUpdate() {
	const [, setState] = useState({});
	return useCallback(() => setState({}), []);
}
```

**TSyringe**

TypeScript용 DI 도구(IoC Container). External Store를 관리하는데 활용할 수 있다. React 컴포넌트 입장에서는 “전역”처럼 여겨진다.

```
npm i tsyringe reflect-metadata //설치
```

Store.ts 생성

```
import {singleton} from 'tsyringe';
type ForceUpdate = () => void;

@singleton()
export default Class Store {
count= 0;
}

const store = container.resolve(Store);
```

&#x20;&#x20;

reflect-metadata는  Main.tsx 가장 위에도 써주고, setupTests.ts 에도 써준다.

```
import 'reflect-metadata'
```

&#x20;

Tsconfig.json의 주석 풀기

```
"experimentalDecorators" : true,
"emitDecoratorMetadata" : true

```

ForceUpdate해주는 부분을 만들어 줘야 한다.

```
@singleton()
Export default Class Store {
Count= 0;
forceUpdates - new Set();
}
 
Const store = container.resolve(Store);
Update() {
This.forceUpdates.forEach((forceUpdate) => forceUpdate());
 
}
store.forceUpdates.add(forceUpdate);
useEffect(() =>
Store.forceUpdates.add(forceUpdate);
}, [])
 
return () => {
   store.forceUpdates.delete(forceUpdate);
}, [store, forceUpdate]);
```

&#x20;

**usestore-ts 사용**

{% code title="" %}
```
import { singleton } from 'tsyringe';

import { Store, Action } from 'usestore-ts';

@singleton()
@Store()
export default class CounterStore {
	count = 0;
	
	@Action()
	increase(step = 1) {
		this.count += step;
	}
	
	@Action()
	decrease() {
		this.count -= 1;
	}
}
```
{% endcode %}

아래와 같이 커스텀 hook을 작성해 준다.

```
import { container } from 'tsyringe';

import { useStore } from 'usestore-ts';

import CounterStore from '../stores/CounterStore';

export default function useCounterStore() {
	const store = container.resolve(CounterStore);
	return useStore(store);
}
```

&#x20;

[^1]: 
