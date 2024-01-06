## The Basic of React

> :bulb: React JS는 애플리케이션이 매우 interactive 하도록 만들어주는 library이다.

<br>

### React JS 설치

> :bulb: React JS를 설치하기 위해서는 두 개의 Javascript 코드를 import 해야 한다 <br> ⇨ `react`, `react-dom`

```html
<script src="https://unpkg.com/react@17.0.2/umd/react.production.min.js"></script>
<script src="https://unpkg.com/react-dom@17.0.2/umd/react-dom.production.min.js"></script>
```

위 코드로 import를 하고 브라우저를 새로고침 했을 때, 개발자 도구의 콘솔창에서 `React`를 호출할 수 있어야 한다.

<br>

### React JS element

React element를 생성해보자! 지금 소개하는 방법은 요즘에는 사용하지 않는 방식이다.

```javascript
const span = React.createElement("span"); // span 태그 생성
```

위와 같이 코드를 작성하면 문자열로 입력한 element를 생성하게 된다. 변수명은 원하는 것으로 지정해도 상관없다.

<br>

:small_blue_diamond: **`createElement()`**

```javascript
React.createElement(
  "span",
  { id: "cool-span", style: { color: "red" } },
  "hello"
); // === <span id="cool-span" style="color: red;" >hello</span>
```

- 1st argument: 만들고자 하는 element
- 2nd argument: 해당 element의 속성(property)
- 3rd argument: 해당 element의 내용(content)

<br>

이제 React로 HTMl을 생성해보자. 그러려면 `react-dom`을 사용해야 한다.

> :bulb: `react-dom`은 library 또는 package로, 모든 React element를 HTML body에 둘 수 있도록 한다.

> :star2: 정리하면, React는 interactive UI를 만들 수 있게 하고, react-doem은 React element를 HTMl에 두는 역할을 한다.

<br>

**ReactDOM**

```javascript
ReactDOM.render(element, location);
```

:small_blue_diamond: **`render()`** <br>

- render는 React element를 HTML로 만들어서 배치한다. 즉, _사용자에게 보여준다._
- element: HTMl에 배치할 React element
- location: element를 어디에 둘 것인지

 <br>

### JSX

`JSX`는 JavaScript를 확장한 문법으로, React element를 생성할 수 있다.
별다른 설치나 설정이 없다면 브라우저는 JSX를 invalid 하다고 보기 때문에 아래와 같이 추가해주자.

```html
...
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
<script type="text/babel">
  ...  // js code
</script>
...
```

위 코드에서 `type`을 지정한 `script` 태그 사이에 JS 코드를 작성하면 된다.

<br>

```javascript
const h3 = React.createElement(
  "h3", // element
  {
    // property
    id: "title",
    onMouseEnter: () => console.log("mouse enter"), //  eventlistener
  },
  "hello h3" // content
);
```

위 코드는 요즘에는 잘 사용하지 않는 방식으로 **JSX를 사용한 아래의 방식으로 많이 사용**한다. 두 코드는 같은 의미이다.

```javascript
const Title = (
  <h3 id="title" onMouseEnter={() => console.log("mouse enter")}>
    Hello I'm a title
  </h3>
);
```

<br>

아래는 또 다른 예시 코드이다. 잘 안쓰는 방식의 코드.

```javascript
const btn = React.createElement(
  "button",
  {
    onClick: () => console.log("im clicked"), // eventlistener on react
    style: { backgroundColor: "tomato" },
  },
  "Click me"
);
```
<br>

위 코드와 같은 의미의 JSX를 사용한 방식의 코드.

```javascript
const Button = (
  <button
    style={{ backgroundColor: "tomato" }}
    onClick={() => console.log("i am click")}
  >
    click me!
  </button>
);
```

<br>

이번에는 아래 코드를 JSX 방식으로 바꿔보자.
```javascript
const container = React.createElement("div", null, [Title, Button]);
```
<br>

우선 `Title`과 `Button`을 함수로 만들어주자!

```javascript
const Title = () => (  // arrow function
  <h3 id="title" onMouseEnter={() => console.log("mouse enter")}>
    Hello I'm a title
  </h3>
);
const Button = () => (  // arrow function
  <button
    style={{ backgroundColor: "tomato" }}
    onClick={() => console.log("i am click")}
  >
    click me!
  </button>
);
```

<br>

함수로 만든 다음 `Container`를 이렇게 수정하자.

```javascript
const Container = (
  <div>
    <Title /> 
    <Button />
  </div>
);
```

> :star2: 컴포넌트의 첫 글자는 반드시 **대문자**여야 한다.

<br>

참고로 `arrow function`은 아래와 동일한 의미이다.

```javascript
function Title() {
  return (
    <h3 id="title" onMouseEnter={() => console.log("mouse enter")}>
      Hello I'm a title
    </h3>
  );
}
```
