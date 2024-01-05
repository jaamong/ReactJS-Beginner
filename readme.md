## The Basic of React

> :bulb: React JS는 애플리케이션이 매우 interactive 하도록 만들어주는 library이다.

<br>

### React JS 설치

> :bulb: React JS를 설치하기 위해서는 두 개의 Javascript 코드를 import 해야 한다 <br> ⇨ `react`, `react-dom`

```javascript
<script src="https://unpkg.com/react@17.0.2/umd/react.production.min.js"></script>
<script src="https://unpkg.com/react-dom@17.0.2/umd/react-dom.production.min.js"></script>
```

위 코드로 import를 하고 브라우저를 새로고침 했을 때, 개발자 도구의 콘솔창에서 `React`를 호출할 수 있어야 한다. 

<br>

### React JS element

React element를 생성해보자!
```javascript
const span = React.createElement("span");  // span 태그 생성
```
위와 같이 코드를 작성하면 문자열로 입력한 element를 생성하게 된다. 변수명은 원하는 것으로 지정해도 상관없다. 

<br>

:small_blue_diamond: **`createElement()`**
```javascript
React.createElement("span", { id: "cool-span", style: { color: "red" } }, "hello");  // === <span id="cool-span" style="color: red;" >hello</span>
```
- 1st argument: 만들고자 하는 element
- 2nd argument: 해당 element의 속성(property)
- 3rd argument: 해당 element의 내용(content)

<br>

이제 React로 HTMl을 생성해보자. 그러려면 `react-dom`을 사용해야 한다. 
> :bulb: `react-dom`은 library 또는 package로, 모든 React element를 HTML body에 둘 수 있도록 한다.

> :star2: 정리하면, React는 interactive UI를 만들 수 있게 하고, react-doem은 React element를 HTMl에 두는 역할을 한다. 

<br>

**`ReactDOM`** 
```javascript
ReactDOM.render(element, location); 
```

:small_blue_diamond: **`render()`** <br>
 - render는 React element를 HTML로 만들어서 배치한다. 즉, *사용자에게 보여준다.*
 - element: HTMl에 배치할 React element
 - location: element를 어디에 둘 것인지