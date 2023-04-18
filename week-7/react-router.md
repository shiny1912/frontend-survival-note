---
description: React Router 노트
---

# React Router

### Routes 작성법

```tsx
import { Routes } from 'react-router-dom';

<Routes>
 <Route path = "/"  && element = {<HomePage />} />
 <Route path = "/about" && element = {<AboutPage />} />
 
</Routes>
```

{% code title="Main.tsx" %}
```tsx
root. render ((
<React.StrictMode>
    <BrowserRouter>
        </App />
    </BrowserRouter> //BrowserRouter로 감싸 준다.
</React.StrictMode>    
));
```
{% endcode %}

Test 코드 작성하기

{% code title="App.test.tsx" %}
```tsx
import { MemoryRouter } from 'react-router-dom';

const context = describe;

 describe ('App', () => {
  context ('when the current path is "/"', () => {
  it ('renders the home page', () => {
   
   render ((
   <MemoryRouter initialEntries={['/']}>
    <App/>
   </MemoryRouter>
  ));
  
  screen.getByText(/Welcome/);
  
  }
  });
  
   context ('when the current path is "/about"', () => {
  it ('renders the about page', () => {
   
   render ((
   <MemoryRouter initialEntries={['/about']}>
    <App/>
   </MemoryRouter>
  ));
  
   screen.getByText(/This is test/);
  
  }
  })
  
 }); 
```
{% endcode %}

