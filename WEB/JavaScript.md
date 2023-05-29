# JavaScript

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
