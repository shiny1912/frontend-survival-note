---
description: React Router
---

# Week 7

### Routing

&#x20;

{% code title="App.tsx" %}
```tsx

const pages : {Record<string>, React.FC }= {
 '/' : HomePage,
 '/about' : AboutPage,
};

export default function App() {
const path = window.location.pathname;
const Page = pages[path] || Homepage;  //이렇게 선언해서< Page /> 컴포넌트로 변경가능하다.

return (
<p>Hello, World! {path} </p>
<div>
 <header> link </header>
 {path === '/' &&  <HomePage /> }
{path === '/about' &&  <AboutPage /> }
<footer> </footer>
 ) : 

</div>
);
}

}


```
{% endcode %}

{% code title="Header.tsx" %}
```tsx
export default function Header () {
return (
 <header>
	<nav>
	<ul>
	<li >
	 <a href = "/" > Home </a>
	</li>
	<li >
	 <a href = "/about" > About </a>
	</li>
	
	</ul>
	</nav>
</header>
);
}
```
{% endcode %}

{% code title="HomePage.tsx" %}
```tsx
export default function HomePage(){
 return (
	<div>
	  <h1>welcome </h1>
	<p> This is test </p>
		</div>
);

}
```
{% endcode %}

{% code title="Footer.tsx" %}
```tsx
export default function Header () {

 return (
 <footer>
<hr />
footer</footer>
);
}
```
{% endcode %}

