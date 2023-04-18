# Navigation

### Navigation

#### History.pushState - > HTML 5부터 생겨났다. 이전에는 경로에 #을 붙이면 새로고침 하지 않도록 함.

아니면 #! 이런 방법도 썼다.



> [History.pushState()](https://developer.mozilla.org/ko/docs/Web/API/History/pushState)

```tsx
const handleClick = (event ) => {
event.preventDefault();
const state = {};
const title = '';
const url = '/about';

history.pushState(state, title, url);
}
```

#### Link

> [Link](https://reactrouter.com/en/main/components/link)

```tsx
function Header() {

return (
	<header>
		<nav>
			<ul>
				<li><Link to="/">Home</Link></li>
				<li><Link to="/about">About</Link></li>
			</ul>
		</nav>
	</header>
	);
}
```

#### NavLink

> [NavLink](https://reactrouter.com/en/main/components/nav-link)

```tsx
function Header() {
	return (
		<header>
			<nav>
				<ul>
					<li><NavLink to="/">Home</NavLink></li>
					<li><NavLink to="/about">About</NavLink></li>
				</ul>
			</nav>
		</header>
	);
}
```

#### Navigate

> [Navigate](https://reactrouter.com/en/main/components/navigate)

```tsx
import { Navigate } from 'react-router-dom';

export default function LoginPage() {
	return (
		<Navigate to="/" />
	);
}
```

테스트에서 “ReferenceError: Request is not defined” 에러가 나면 “whatwg-fetch”를 임포트해서 해결할 수 있다.

#### useNavigate

> [useNavigate](https://reactrouter.com/en/main/hooks/use-navigate)

```tsx
import { useNavigate } from 'react-router-dom';

export default function Footer() {
	const navigate = useNavigate();
	
	const handleClick = () => {
		navigate('/about');
	};
	
	return (
		<footer>
			<button type="button" onClick={handleClick}>
				Press
			</button>
		</footer>
	);
}
```
