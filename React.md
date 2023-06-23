# 리액트 공부
: 리액트는 js 기반으로, 사용자가 태그를 정의해 사용할 수 있게 하는 도구. 

## 1. 실습 환경 구축
먼저 Node.js를 설치한다.
프로젝트 폴더를 만든다. react-app이라는 이름으로 폴더를 만들었다!!
vs code 프로그램으로 폴더를 열고, 터미널을 열어 리액트 설치 명령어를 실행한다
```
npx create-react-app .
```
설치가 끝나면, 리액트 개발환경을 실행하는 명령어를 친다.
```
npm start
```
그럼 포트 3000번을 사용하는 웹 창이 뜬다!!

## 2. 소스코드 수정하고 배포하기
* 소스코드를 수정하기 위해...
npm start 명령어를 통해 개발환경을 열면,
워크스페이스 공간에 src 라는 폴더가 생성된다. 이 안에 index.js가 핵심 파일!! 이 파일을 읽어 웹페이지를 연다.
<b>즉, 맨 처음 localhost:3000 링크를 통해 열리는 웹페이지는 index.js를 읽어 보여준 화면이다!!</b>

> ...index.js 내부...
<App/> 태그의 내용이 웹을 나타냄. 
이 앱 태그의 내용은 어디에 있냐면, import App from './App' 이라는 코드에 따라 App.js 파일에 나타나있다. 
App.js 파일에서 배운 html 태그를 통해 입력하면 그 내용 그대로 웹에 나타난다!!


* 소스코드를 배포하기 위해...
```
  npm run build
```
명령어를 통해 배포판을 만든다. >> 그럼 build 폴더가 생기는데 이 안에 보면 index.html이 있음. 그럼 배포 받은 클라이언트들은 이 index.html을 열어서 보게 되는 거다!!
```
  npx serve -s build
```
명령어를 통해 서버를 세운다. >> 그럼 내가 이 웹에 접속할 수 있는 주소가 나온다. 기본적으론 localhost:3000 이다. 


## 3. 컴포넌트 만들기
: 리액트는 사용자 정의 태그를 만드는 것이다
그렇다면 어떻게 태그를 만들까?

태그를 만드는 방법은
1. class를 활용
2. function을 활용
이 두 가지 방법이 있는데, 여기서는 함수만을 활용할 것!!

기본적인 App.js 전문
```App.js
import logo from './logo.svg';
import './App.css';

function App() {
  return (
    <div>
      <header>
        <h1><a href="/">WEB</a></h1>
      </header>
      <nav>
        <ol>
          <li><a href="/read/1">html</a></li>
          <li><a href="/read/2">css</a></li>
          <li><a href="/read/3">javascript</a></li>          
        </ol>
      </nav>
    </div>
  );
}

export default App;
```

만약 이 파트를 모든 수십개의 사이트에 적용하려면, 하나의 함수로 묶어 해당 html들에 함수를 적용시키기만 하면 된다.

```App.js
//함수 적용

import logo from './logo.svg';
import './App.css';
function Header(){
  return <header>
    <h1><a href="/">WEB</a></h1>
  </header>
}

function App() {
  return (
    <div>
      <Header></Header>
      <nav>
        <ol>
          <li><a href="/read/1">html</a></li>
          <li><a href="/read/2">css</a></li>
          <li><a href="/read/3">javascript</a></li>          
        </ol>
      </nav>
    </div>
  );
}

export default App;
```

함수를 만들 때 주의할 점. 이름을 무조건 대문자로 시작하게 짓자. 
이렇게 만든 사용자 정의 태그를 <b>컴포넌트</b> 라고 한다
  
  
## 4. props

이렇게 우리가 만든 컴포넌트에도, 디자인 속성을 부여할 수 있다. 함수에 매개변수 props를 주는 방식으로 구현하면 된다!!
```App.js
// 매개변수가 없는 기초적인 컴포넌트
<Header></Header>

//매개변수가 있는 컴포넌트
//title, body 등 사용자가 지정한 변수를 통해 매개변수를 넘겨준다.
<Header title="매개변수 값"></Header>
<Article title="매개변수1" body="매개변수2"></Header>
```

매개변수를 받는 함수의 구조는 다음과 같다
```App.js
//props 라는 이름의 매개변수를 받는다
//이 매개변수는 문자열도, 숫자형도 아닌 object 형이다.
//따라서 props.title 속성으로 문자열을 받아와야 한다!!

function Header(props){
  return <header>
    <h1><a href="/">{props.title}</a></h1>
  </header>
}
```
  
전체 코드
```App.js
import logo from './logo.svg';
import './App.css';
function Header(props){
  return <header>
    <h1><a href="/">{props.title}</a></h1>
  </header>
}
function Nav(){
  return <nav>
    <ol>
      <li><a href="/read/1">html</a></li>
      <li><a href="/read/2">css</a></li>
      <li><a href="/read/3">javascript</a></li>          
    </ol>
  </nav>
}
function Article(props){
  return <article>
    <h2>{props.title}</h2>
    {props.body}
  </article>
}

function App() {
  return (
    <div>
      <Header title="REACT"></Header>
      <Nav></Nav>
      <Article title="Welcome!" body="hello, WEB."></Article>
      <Article title="Hi!" body="hello, REACT."></Article>
    </div>
  );
}

export default App;
```

이번에는 props 여러 개를 array 안에 저장해 쓰는 형식을 구현해보자. 
이 때 array 내부 값은 변하지 않기 때문에 const 로 지정해주면 코드가 더 튼튼해진다!!
const를 적재적소에 쓰는 것도 중요함.

```ex.js
import logo from './logo.svg';
import './App.css';

function Header(props){
  return <header>
  <h1><a href="/">{props.title}</a></h1>
</header>
}

function Nav(props){
  const lis =[]
  for(let i=0;i<props.topics.length;i++){
    let t=props.topics[i];
    lis.push(<li key={t.id}><a href={'/read/' + t.id}>{t.title}</a></li>)
  }

  return <nav>
  <ol>
    {lis}
  </ol>
</nav>
}

function Article(props){
  return <article>
  <h2>{props.title}</h2>
  {props.body}
</article>
}

function App() {
  const topics =[
    {id:1, title:'html', body:'html is ...'},
    {id:2, title:'css', body:'css is ...'},
    {id:3, title:'js', body:'js is ...'}
  ]
  return (
    <div>
      <Header title="REACT"></Header>
      <Nav topics={topics}></Nav>
      <Article title="Welcome" body="hello, web!!"></Article>
      
    </div>
  );
}

export default App;

```
nav 안에 여러 개의 정보를 담아야 하므로 topics라는 변수를 만들어 정보값을 담는다.
topics 내 값들은 서로 고유한 값이기 때문에, 각자 id를 부여해야 한다. 
function 내부에서 for문을 통해 각 <li> 태그에 아이디 값을 부여하고, 링크를 걸어준다.

## 5. 이벤트 (6,7)

## 6. 생성 기능 구현 (8)

## 7. 수정 기능 구현 (9)

## 8. 삭제 기능 구현 (10)
