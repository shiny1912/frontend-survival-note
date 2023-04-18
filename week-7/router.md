# Router

#### Router

App에는 전체적인 레이아웃과, 어떻게 라우팅이 되는지가 들어간다.

그럼레이아웃을 따로 관리하는 것은 어떨까?

```javascript
function Pate () {
//라우팅 관련

}
export default function App() {
return (
    <Page />
);
}
```

React Router 버전 6.4부터 지원하는, 라우터 객체를 만들어서 쓰는 방법.

라우팅 정보만 별도의 파일로 관리.

```tsx
import { Outlet } from 'react-router-dom';
import { createBrowserRouter } from 'react-router-dom';

//레이아웃을 몰아서 컴포넌트로 잡아준다.
//따로 컴포넌트로 분리해주는 것도 괜찮다.
function Layout() {
	return (
		<div>
			<Header />
			<Outlet />
			<Footer />
		</div>
	);
}
//계층형으로 되도록 아래와 같이 작성해 준다.
//routes도 따로 분리해주면 좋다. 테스트 작성시에도 routes 정보가 필요하기 때문.
const routes = [
	{
		element: <Layout />, 
		children: [
			{ path: '/', element: <HomePage /> },
			{ path: '/about', element: <AboutPage /> },
		],
	}, //
];
const router = createBrowserRouter(routes);

export default routes;
```

App 컴포넌트를 거치지 않고 바로 브라우저 라우터 만들어서 사용.

```tsx
import { createBrowserRouter, RouterProvider } from 'react-router-dom';

import routes from './routes';

const router = createBrowserRouter(routes);

root.render((
	<React.StrictMode>
		<RouterProvider router={router} />
	</React.StrictMode>
));
```

메모리 라우터 만들어서 테스트한다.

RouterProvider로 따로 분리해준다.



App.tsx에서 route 테스트가 불가능하므로, routes.test.tsx 파일을 만들어서 따로 테스트해준다.

```tsx
describe('routes'', () => {	
	function renderRouter(path: string) {
		const router = createMemoryRouter(routes, { initialEntries: [path] });
		render(<RouterProvider router={router} />);
	}
	
	context('when the current path is “/”', () => {
		it('renders the home page', () => {
			renderRouter('/');
	
			screen.getByText(/Hello/);
		});
	});
	
	context('when the current path is “/about”', () => {
		it('renders the about page', () => {
			renderRouter('/about');
	
			screen.getByText(/About/);
		});
	});
});
```
