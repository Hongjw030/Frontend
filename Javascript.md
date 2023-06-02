# javaScript 공부 노트. 

## 1. JS란?
사용자와 웹이 동적으로 상호작용하게 하는 프로그래밍 언어. js는 html 웨에서 동작하는 언어이다! 
```ex.js
<input type="button" value="button1" onclick="alert('clicked button!!')">

<script>
  document.write(1+1 + "<br>");
  document.write("hello!");
</script>
```

## 2. 변수와 대입 연산자
js는 프로그래밍 언어기 때문에 변수, 연산자의 개념이 있다. 
```ex.js
var name = "hellen";
var numb = 1;
```

## 3. 조건문
조건문을 작성해보자.
```ex.js
<input type="button" id="changeBut" value="fornight" onclick="
  if(document.querySelector('#changeBut').value=='fornight'){
    document.querySelector('body').style.backgroundColor = 'black';
    document.querySelector('body').style.color='white';
    document.querySelector('#changeBut').value='forday';
  }
  else{
    document.querySelector('body').style.backgroundColor = 'white';
    document.querySelector('body').style.color='black';
    document.querySelector('#changeBut').value='fornight';
  }
">
```

## 3-1. 리팩토링?
좋은 코드란 중복이 없는 코드이다. 코드에서 중복을 없애고 비효율적인 부분을 제거하는 것을 리팩토링이라 하는데, 이 과정은 필수다!! this 키워드를 잘 활용하고, 중복이 생기는 코드는 하나의 변수로 묶어버리자.
```ex.js
<input type="button" id="changeBut" value="fornight" onclick="
  var target = document.querySelector('body');
  if(this.value=='fornight'){
    target.style.backgroundColor = 'black';
    target.querySelector('body').style.color='white';
    this.value='forday';
  }
  else{
    target.querySelector('body').style.backgroundColor = 'white';
    target.querySelector('body').style.color='black';
    this.value='fornight';
  }
">
```

## 4. 반복문
iterator로 검색하자.
```ex.js
<script>
  var i = 0;
  var coworkers = ["hellen", "john", "nana", "lisa"];
  while(i<coworkers.length){
    document.write('<a href="http://www.naver.com/'+coworkers[i]+'">' + coworkers[i] + '</a>' + "<br>");
    i=i+1;
  }
</script>
```

## 5. 함수
객체를 가지고 함수를 만드는 방법. 
중복된 기능을 하나의 함수로 묶는 것은 매우 중요하다!! 함수의 매개 변수를 잘 이해하고, this 와 같은 키워드를 사용해 함수를 구현하자.
```ex.js
<!doctype html>
<html>
    <head>
        <title>object</title>
        <meta charset="utf-8">
    </head>

    <body>
        <h1>객체 object</h1>
        <h2>속성 생성하기 create</h2>
        <script>
            var coworkers = {
                "programmer" : "hellen",
                "designer" : "john",
                "client" : "lisa"
            };
            document.write("programder : " + coworkers.programmer + "<br>");
            document.bookkeeper = "maria";
            coworkers["scientist"] = "elsa"
            document.write("scientist : " + coworkers.scientist + "<br>");        
        </script>

        <h2>모두 출력하기 iterator</h2>
        <script>
            for(var key in coworkers){
                document.write(key + " : " + coworkers[key] + "<br>");
            }
        </script>

        <h2>함수 구현하기 function</h2>
        <script>
            coworkers.showAll = function(){
                for(var key in this){
                    document.write(this[key] + " : " + coworkers[key] + "<br>");
                }
            }
            coworkers.showAll();
        </script>

    </body>
</html>
```

실제로 써먹는다면?
```ex.js
var Links = {
    setColor:function(color){
        var alist = document.querySelectorAll('a');
    var i = 0;
        while(i<alist.length){
            alist[i].style.color = color;
            i=i+1;
        }
    } 
}
var Body = {
    setColor:function (color){
        document.querySelector('body').style.color = color;
    },
    setBackgroundColor:function (color){
        document.querySelector('body').style.backgroundColor = color;
    }
}

function nightDayHandler(self){
    var target = document.querySelector('body');
    if(self.value=='fornight'){
        Body.setColor('white');
        Body.setBackgroundColor('black');
        self.value='forday';
        Links.setColor('powderblue');

    }
    else{
        Body.setColor('black');
        Body.setBackgroundColor('white');
        self.value='fornight';
        Links.setColor('green');
    }
}
```
## 7. 마지막...
ui: 유저 인터페이스. 사용자가 시스템을 조작하기 위해 사용하는 장치들. 버튼, textbox 등...

api: 어플리케이션 프로그래밍 인터페이스. 유저가 볼 수 있고 유저의 조작에 의해 발생한 장치지만, 프로그래머가 우선적으로 만든 장치. alert 창 등...
DOM, window, ajax, cookie 등 모든 게 api이다!!

즉, 내가 프로그램을 만들고 싶다면 api를 잘 활용하는 것이 관건. 앞으로 웹을 만들 때엔 여러 api를 검색하고 사용하면서 만들어보자!!
