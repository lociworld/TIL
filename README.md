# Today I Learned

> ​	매일 배운 내용을 정리합니다.

## 200622

- 뷰를 이용해 앤트픽 랜딩페이지를 만들어보았다.
- 이미지가 한 화면에 꽉차게 배치하였고, 버튼을 클릭하면 앱다운로드 링크가 렌더링되도록 했다. 아직 앱링크가 없어서 페이지만 연결시켰다.
- 백그라운드 이미지 넣기

```
.hello {
  background-image: url('~@/assets/ants_1920_1280.jpg');
  background-size: cover;
  background-position: center;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align:center;
  padding: 0 20px;
}

.hello .box{
  position: relative;
  max-width: 600px;
  padding: 50px;
  background: rgba(255,255,255,.7);
  box-shadow: 0 5px 15px rgba(0,0,0,.5);
  border-radius: 10px;
}
.hello h1{
  font-size: 50px; 
  line-height: 1.2;
}
```

- 물결없이 '@/assets//ants_1920_1280.jpg' 로 해주니까 안됨. 물결해주기
- 플렉스로 4칸 가로길이 같게 배열 하는 방법

```
#section-c{
  display:flex;
  flex-wrap: wrap;
  text-align:center;
}

#section-c div{
  padding:20px;
  flex:1;
}
```

- 플렉스, flex:1;
- flex:1;은  `flex-grow: 1;` 과 같다., 자동으로 플렉스 아이템들의 너비가 플렉스 컨테이너의 너비를 기준으로 알맞게 같은너비를 가지고 확장된다.

- html 꿀팁

```
div#section-a 하고 탭키를 누르면
<div id="section-c"></div>이 뙇! 
.box1 하고 탭키를 누르면
<div class="box1"></div>이 뙇!
lorem20 탭키 누르면
lorem 20글자가 뙇!
```

- aws를 이용해 뷰 배포도 진행해보았고, 문서로 정리했다. 블로그에 올릴예정

## 200708

- 깃에 대해 더 공부했다

- git 충돌이 나도 당황하지 말자

- 오류 메시지 나오면 당황하지 말고 git lab에서 커밋내역이랑 local에서 git log 비교해보자

- 해결방법은 git pull origin master하고 , 병합해서 푸쉬하면 된다 

- 충돌 상황을 고쳤다면 git add . , git commit 하면 자동으로 커밋메시지가 저장되어 있음을 확인할 수 있다

- |MERGING 플래깅이 없어졌다면 해결된 것이고, 이 상태에서  git push origin master하면 잘 올라간다

- 충돌 상황 시나리오에 대해 생각해 보면 크게 세 가지 이다.

- 상황1: fast-foward:   feature 브랜치 생성된 이후 master 브랜치에 변경 사항이 없는 상황, 즉 혼자 쌓아나갈 때

- 상황2: 서로 다른 이력(commit)을 병합(merge)하는 과정에서 **다른 파일이 수정**되어 있는 상황 => git이 auto merging을 진행하고, **commit이 발생된다.**

- 상황3: 서로 다른 이력(commit)을 병합(merge)하는 과정에서 **같은 파일의 동일한 부분이 수정**되어 있는 상황

  git이 auto merging을 하지 못하고, 충돌 메시지가 뜬다.

  - 해당 파일의 위치에 표준형식에 따라 표시 해준다.

  - 원하는 형태의 코드로 직접 수정을 하고 직접 commit을 발생 시켜야 한다.

- 같은 파일을 수정했을 경우에는 이력을 바로 합칠 수 없음
- 이 때는 우리가 선택하면 됨. 파일을 열어보면 head 플래그(지금 내가 작업한 곳)랑,  incoming Change 플래그 삭제해주고 내가 남기고 싶은 부분만 남기면 됨. 파일을 수정 하고 깃에드 깃커밋 깃푸쉬 ㄱㄱ

## 200709

- 깃에 대해 더 공부했다. 

- 깃헙에서는 pull request, 깃랩에서는 merge request라는 표현을 쓴다 

- pull request의 의미

  - **내가 작업한 코드가 있으니 내 브랜치를 당겨 검토 후 병합해주세요 (^0^)/**
  - **풀 리퀘스트를 이용한 흐름은 GitHub의 원격 저장소를 각자의 계정으로 Fork해 간 뒤에 fork 한 저장소를 클론 받아서 작업용 브랜치를 하나 만들어서 작업하고 이를 Fork 한 저장소에 푸시해서 풀 리퀘스트로 원격 저장소에 보내는 방식이다**

- 깃헙 플로우

  1. 프로젝트를 `Fork` 한다.
  2. `master` 기반으로 토픽 브랜치를 만든다.
  3. 뭔가 수정해서 커밋한다.
  4. 자신의 GitHub 프로젝트에 브랜치를 Push 한다.
  5. GitHub에 Pull Request를 생성한다.
  6. 토론하면서 그에 따라 계속 커밋한다.
  7. 프로젝트 소유자는 Pull Request를 Merge 하고 닫는다.

  > [https://git-scm.com/book/ko/v2/GitHub-GitHub-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%EC%97%90-%EA%B8%B0%EC%97%AC%ED%95%98%EA%B8%B0](https://git-scm.com/book/ko/v2/GitHub-GitHub-프로젝트에-기여하기)

- 깃포크: 내가 권한이 없는 곳에서 고치고 싶을 때 포크를 이용한다. 

  - 참여하고 싶은 프로젝트가 생기면 아마 그 프로젝트에 Push 할 권한은 없을 테니까 “Fork” 해야 한다. “Fork” 하면 GitHub이 프로젝트를 통째로 복사해준다. 그 복사본은 사용자 네임스페이스에 있고 Push 할 수도 있다.
  - 내가 권한이 없는 곳에서 고치고 싶을 때 포크를 이용한다. 
  - 포크를 이용하면 url이 내 아이디로 바뀌고, 내 저장소로 포크한 것이 가져와진다.
  - 수정을하고, 에드 커밋한다(로컬에서 깃 클론해서 수정해도 됨)
  - git push origin master한다
  - 이제 내 프로젝트에는 반영이 됐고, 포크한 원래 프로젝트에는 반영이 안된상태이다.
  - pull requests 클릭 > New pull request  클릭 > Create pull reuquest 클릭하면 원래 포크주인에게 pull request가 보내진다

- 더 알아보면 좋은 것: rebase

> https://tech.10000lab.xyz/git/git-rebase-workflow.html

## 200730

 파비콘

- vue.js 에서 파비콘과 타이틀을 수정했다
- 파비콘 파일을 public/favicon.io 이다 
- io 파일이 더 좋은 지 png가 더 좋은 지에 대해 정리한 글이 있었는데 아직 이해가 힘들다
- 파비콘을 등록하는 것은 쉬워보였지만 경로설정을 잘못하는 바람에 한 참을 헤맸다
- 자세한 내용은 블로그에 적겠다

## 200805

자바스크립트 공부 시작! 

> https://poiemaweb.com/

자바스크립트는 개발자가 별도의 컴파일 작업을 수행하지 않는 **[인터프리터](https://ko.wikipedia.org/wiki/인터프리터) 언어(Interpreter language)**이다. 대부분의 모던 자바스크립트 엔진(Chrome의 V8, FireFox의 Spidermonkey, Safari의 JavaScriptCore, Microsoft Edge의 Chakra 등)은 인터프리터와 컴파일러의 장점을 결합하여 비교적 처리 속도가 느린 인터프리터의 단점을 해결했다. 인터프리터는 소스코드를 즉시 실행하고 컴파일러는 빠르게 동작하는 머신 코드를 생성하고 최적화한다. 이를 통해 컴파일 단계에서 추가적인 시간이 필요함에도 불구하고 보다 빠른 코드의 실행이 가능하다.

자바스크립트는 [명령형(imperative)](https://ko.wikipedia.org/wiki/명령형_프로그래밍), [함수형(functional)](https://ko.wikipedia.org/wiki/함수형_프로그래밍), [프로토타입 기반(prototype-based) 객체지향 프로그래밍](https://ko.wikipedia.org/wiki/프로토타입_기반_프로그래밍)을 지원하는 [멀티 패러다임 프로그래밍 언어](https://ko.wikipedia.org/wiki/다중_패러다임_프로그래밍_언어)다.

비록 다른 객체지향 언어들과의 차이점에 대한 논쟁들이 있긴 하지만, 자바스크립트는 강력한 객체지향 프로그래밍 능력을 지니고 있다. 간혹 클래스(ES6에서 새롭게 도입되었다), 상속, 정보 은닉을 위한 키워드 private가 없어서 객체지향 언어가 아니라고 오해하는 경우도 있지만 자바스크립트는 클래스 기반 객체지향 언어보다 효율적이면서 강력한 **프로토타입 기반의 객체지향 언어**이다.

> 콘솔에서 디버깅 하는 방법
>
> https://developers.google.com/web/tools/chrome-devtools/javascript/?hl=ko

**body 요소의 가장 아래에 자바스크립트를 위치시키는 것이 좋은 이유 2가지**

- HTML 요소들이 스크립트 로딩 지연으로 인해 렌더링에 지장 받는 일이 발생하지 않아 페이지 로딩 시간이 단축된다.
- DOM이 완성되지 않은 상태에서 자바스크립트가 DOM을 조작한다면 에러가 발생한다.

**자바스크립트의 모든 값은 데이터 타입을 갖는다. 자바스크립트는 7가지 데이터 타입을 제공한다.**

- 원시 타입 (primitive data type), 기본 타입
  - 원시 타입의 값은 [변경 불가능한 값(immutable value)](https://poiemaweb.com/js-immutability)이며 **[pass-by-value(값에 의한 전달)](https://poiemaweb.com/js-object#5-pass-by-value)** 이다.
  - `number`
  - `string`
  - `boolean`
  - `null`
  - `undefined`
  - `symbol` (New in ECMAScript 6)
- 객체 타입 (Object data type)
  - `object`

**동적 타이핑**

자바스크립트는 C나 Java외는 다르게 변수를 선언할 때 데이터 타입을 미리 지정하지 않는다. 다시 말해, 변수에 할당된 값의 타입에 의해 동적으로 변수의 타입이 결정된다. 이를 동적 타이핑이라 하며 자바스크립트가 다른 프로그래밍 언어와 구별되는 특징 중 하나이다.

~~~
var foo = 42;    // foo 는 이제 Number 임
var foo = "bar"; // foo 는 이제 String 임
var foo = true;  // foo 는 이제 Boolean 임
~~~

- 타입은 프로그램이 처리되는 과정에서 자동으로 파악됨
- 같은 변수에 여러 타입의 값을 넣을 수 있음

한줄 주석은 `//` 다음에 작성하며 여러 줄 주석은 `/*`과 `*/`의 사이에 작성한다. 

다른 언어와 달리 자바스크립트에서는 블록 유효범위(Block-level scope)를 생성하지 않는다. 함수 단위의 유효범위(Function-level scope)만이 생성된다.

 원시 타입(Primitives)을 제외한 나머지 값들(함수, 배열, 정규표현식 등)은 모두 객체이다.

오늘은 자바스트립트의 개념과 기본 문법에 대해 학습했다.

다음 공부가 기대된다.



## 200806

### 1. Today I Learned

자바스크립트 공부 시작!

자바스크립트의 숫자 타입은 모든 수를 실수를 처리한다. 정수로 표시된다해도 사실은 실수다. 따라서 정수로 표시되는 수 끼리 나누더라도 실수가 나올 수 있다.

추가적인 수 표현

- `Infinity` : 양의 무한대
- `-Infinity` : 음의 무한대
- `NaN` : 산술 연산 불가(not-a-number)

자바스크립트의 문자열은 원시 타입이며 변경 불가능(immutable)하다. 이것은 한 번 문자열이 생성되면, 그 문자열을 변경할 수 없다는 것을 의미한다

새로운 문자열을 재할당하는 것은 가능함

~~~javascript
var str = 'string';
// 문자열은 유사배열이다. 배열처럼 인덱스를 통해 접근가능
for (var i = 0; i < str.length; i++) {
  console.log(str[i]);
}

// 문자열을 변경할 수 없다.
str[0] = 'S';
console.log(str); // string
~~~

null

~~~javascript
var foo = null;
console.log(typeof foo === null); // false
console.log(foo === null);        // true
~~~

var 키워드로 선언된 변수의 문제점

1. 함수 레벨 스코프(Function-level scope)
   - 전역 변수의 남발
   - for loop 초기화식에서 사용한 변수를 for loop 외부 또는 전역에서 참조할 수 있다.
2. var 키워드 생략 허용
   - 의도하지 않은 변수의 전역화
3. 중복 선언 허용
   - 의도하지 않은 변수값 변경
4. 변수 호이스팅
   - 변수를 선언하기 전에 참조가 가능하다.

전역 변수는 유효 범위(scope)가 넓어서 어디에서 어떻게 사용될 지 파악하기 힘들다. 이는 의도치 않은 변수의 변경이 발생할 수 있는 가능성이 증가한다. 또한 여러 함수와 상호 의존하는 등 부수 효과(side effect)가 있을 수 있어서 복잡성이 증가한다.

변수의 유효 범위(scope)는 좁을수록 좋다.

ES6는 이러한 var의 단점을 보완하기 위해 [let과 const 키워드](https://poiemaweb.com/es6-block-scope)를 도입하였다.

### 2. Today I Found Out

자바스크립트 데이터타입과 변수에 대해 학습했다. 술술 읽어나갈 수는 있다. 그러나 그냥 읽어서는 남에게 설명해줄 수는 없을 것 같다. 어제배운 자바스크립트의 타입과 동적타이핑, var 키워드로 선언된 변수의 문제점를 외워야지!

## 200807

###  https://poiemaweb.com/ 공부 -7. 연산자 

문은 리터럴, 연산자, 표현식, 키워드 등으로 구성되며 세미콜론( ; )으로 끝나야 한다. (코드 블록 { … }은 제외)

~~~javascript
var x = 5, result;

// 선대입 후증가 (Postfix increment operator)
result = x++;
console.log(result, x); // 5 6

// 선증가 후대입 (Prefix increment operator)
result = ++x;
console.log(result, x); // 7 7

// 선대입 후감소 (Postfix decrement operator)
result = x--;
console.log(result, x); // 7 6

// 선감소 후대입 (Prefix decrement operator)
result = --x;
console.log(result, x); // 5 5

~~~

`+` 연산자는 피연산자 중 하나 이상이 문자열인 경우 문자열 연결 연산자로 동작한다. 그 외의 경우는 덧셈 연산자로 동작한다. 

~~~javascript
// 문자열 연결 연산자
'1' + '2'      // '12'
'1' + 2       // '12'

// 산술 연산자
1 + 2          // 3
1 + true       // 2 (true → 1)
1 + false      // 1 (false → 0)
true + false    // 1 (true → 1 / false → 0)
1 + null       // 1 (null → 0)
1 + undefined // NaN (undefined → NaN)
~~~

동등/ 일치 비교 연간자

| 비교 연산자 | 의미        | 사례    | 설명                     |
| :---------: | :---------- | :------ | :----------------------- |
|     ==      | 동등 비교   | x == y  | x와 y의 값이 같음        |
|     ===     | 일치 비교   | x === y | x와 y의 값과 타입이 같음 |
|     !=      | 부등 비교   | x != y  | x와 y의 값이 다름        |
|     !==     | 불일치 비교 | x !== y | x와 y의 값과 타입이 다름 |

동등 비교 연산자는 편리한 경우도 있지만 수많은 부작용을 일으키므로 사용하지 않는 편이 좋다.

```javascript
NaN === NaN // false
isNaN(NaN) // true

```

삼항연산자

```
조건식 ? 조건식이 ture일때 반환할 값 : 조건식이 false일때 반환할 값
```

논리연산자

| 논리 연산자 |    의미     |
| :---------: | :---------: |
|    \|\|     | 논리합(OR)  |
|     &&      | 논리곱(AND) |
|      !      |  부정(NOT)  |

~~~javascript
// 논리합(||) 연산자
true || true   // true
true || false  // true
false || true  // true
false || false // false

// 논리곱(&&) 연산자
true && true   // true
true && false  // false
false && true  // false
false && false // false

// 논리 부정(!) 연산자
!true  // false
!false // true
~~~

쉼표연산자

쉼표(,) 연산자는 왼쪽 피연산자부터 차례대로 피연산자를 평가하고 마지막 피연산자의 평가가 끝나면 마지막 피연산자의 평가 결과를 반환한다.

~~~javascript
var x, y, z;
x = 1, y = 2, z = 3; // 3
~~~

type of 연산자

~~~javascript
typeof ''              // "string"
typeof 1               // "number"
typeof NaN             // "number"
typeof true            // "boolean"
typeof undefined       // "undefined"
typeof Symbol()        // "symbol"
typeof null            // "object"
typeof []              // "object"
typeof {}              // "object"
typeof new Date()      // "object"
typeof /test/gi        // "object"
typeof function () {}  // "function"
~~~

주의해야 할 것은 typeof 연산자로 null 값을 연산해 보면 null이 아닌 “object”를 반환한다는 것이다. 이것은 자바스크립트의 첫 번째 버전에서 이렇게 설계된 것을 현재의 버전에 반영하지 못하고 있기 때문이다

따라서 null 타입을 확인할 때는 typeof 연산자를 사용하지 말고 일치 연산자(===)를 사용하도록한다.

~~~javascript
typeof undeclared  // "undefined"
~~~

 선언하지 않은 식별자를 typeof 연산자로 연산해 보면 ReferenceError가 발생하지 않고 “undefined”를 반환한다.

## JavaScript30 day1

Window와 document

> https://www.zerocho.com/category/JavaScript/post/573b321aa54b5e8427432946

윈도우

- 윈도우는 브라우저 최상위 객체이다.  **브라우저**의 요소들과 자바스크립트 엔진, 그리고 모든 **변수**를 담고 있는 객체. 생략 가능

document 

- . document도 윈도우 객체의 속성이기 때문에 `window.document` 로 접근. 하지만 window는 생략 가능(전역 객체)하기 때문에 그냥 **document**로 접근

~~~javascript
document.getElementById(아이디)
document.getElementsByClassName(클래스), document.getElementsByName(이름), document.getElementsByTagName(태그)
document.querySelector(선택자), document.querySelectorAll(선택자)
//css 선택자로 선택할 수 있게 해줍니다. 아이디는 #, 클래스는 .(점)
//태그명[속성명=속성값] 같은 것도 할 수 있고, 부모 > 자식, 부모 자손 등등 css의 선택자는 거의 다 쓸 수 있습니다.
//  const audio = document.querySelector(`audio[data-key="${e.keyCode}"]`);

var div = document.createElement('div'); // 메모리에 div가 생성됨
~~~

`**Document.getElementById()**` 메서드는 주어진 문자열과 일치하는 [`id`](https://developer.mozilla.org/ko/docs/Web/API/Element/id) 속성을 가진 요소를 찾고, 이를 나타내는 [`Element`](https://developer.mozilla.org/ko/docs/Web/API/Element) 객체를 반환합니다. ID는 문서 내에서 유일해야 하기 때문에 특정 요소를 빠르게 찾을 때 유용합니다.

ID가 없는 요소에 접근하려면 [`Document.querySelector()`](https://developer.mozilla.org/ko/docs/Web/API/Document/querySelector)를 사용하세요. 모든 [선택자](https://developer.mozilla.org/en-US/docs/Glossary/CSS_selector)를 사용할 수 있습니다.

~~~javascript
function changeColor(newColor) {
  var elem = document.getElementById('para');
  elem.style.color = newColor;
}
~~~

`**Array.from()**` 메서드는 유사 배열 객체(array-like object)나반복 가능한 객체(iterable object)를 얕게 복사해새로운`Array` 객체를 만듭니다.

~~~javascript
console.log(Array.from('foo'));
// expected output: Array ["f", "o", "o"]

console.log(Array.from([1, 2, 3], x => x + x));
// expected output: Array [2, 4, 6]
~~~

addEventListener

~~~javascript
// Function to change the content of t2
function modifyText() {
  var t2 = document.getElementById("t2");
  if (t2.firstChild.nodeValue == "three") {
    t2.firstChild.nodeValue = "two";
  } else {
    t2.firstChild.nodeValue = "three";
  }
}

// add event listener to table
var el = document.getElementById("outside");
el.addEventListener("click", modifyText, false);

/*output: 
one
two*/
~~~

이 코드에서, `modifyText()` 는 `addEventListener()`를 사용하여 등록된 `click` 이벤트에 대한 리스너입니다. 테이블의 아무곳이나 클릭하더라도, 핸들러에서 버블링되고 `modifyText()` 가 실행됩니다. 

addEventListener 를 사용하면 클릭(첫번째 인자) 후 modifyText()가 실행된다

### Today I Found Out

- 자바스크립트 연산자에 대해 학습했다
- 윈도우 객체와 document 객체에 대해 학습했다
- document에서 속성에 접근하는 여러가지 방법에 대해 학습했다
- `**Array.from()**` 메서드
- `addEventListener()` 에 대해 학습했다
- 그동안 난 뭐를 공부했던 것일까....ㅎㅎㅎ 새롭게 알아가는 것들이 너무 많다. 

## 200808

### react todolist 

- 구현하고 싶은 것 
- 수정하기를 눌렀을 때는 수정하기 상태가 된다. 수정하기 상태가 되면 인풋 창의 버튼은 할일 '추가' 버튼이 아닌 '수정' 버튼으로 바뀐다.
- 수정하기 상태에서 인풋 창에 값을 입력하고 '수정'버튼을 누르면 할일이 추가되고, '수정'버튼은 다시 '추가' 버튼으로 바뀐다.

-  오류

- 수정버튼을 누르면 edit 상태를 true로 바꾸려고 하는데 잘 안된다. setEdit is not a function 이라는 오류 메세지가 뜬다

- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Not_a_function
- 해결중

~~~javascript
/* eslint-disable jsx-a11y/accessible-emoji */
import React, { useCallback } from 'react';
import styled from 'styled-components';
import emptyViewImage from '../assets/images/im-empty-view.png';
import {ToDoSubmitButton} from './ToDoForm.jsx'

const ToDoListView = ({todolist, updateTodolist, deleteTodolist, toggleDoneTodolist, edit, setEdit}) => {

    const handleToggleDoneTodolist = useCallback((id) => () => {
        toggleDoneTodolist(id)
    }, [toggleDoneTodolist])

    const handleDeleteTodolist = useCallback((id) => () => {
        deleteTodolist(id);
    }, [deleteTodolist]);
    
    const handleUpdateTodolist = useCallback((edit) => () => {
      setEdit(true);
  }, [setEdit]);

    if (todolist.length === 0) {
        return <EmptyViewImage src={emptyViewImage} alt="리스트가 비었어요! 등록해주세요!" />
    }

    return (
        <ListContainer>
          {todolist.map(item => {
            if (item.isDelete) {
                return null;
            }
            return  (
                <ListItemStyle key={item.id}>
                    <ListContentGroup>
                        <ListItemIcon>📝</ListItemIcon>
                        <ListItemText isDone={item.isDone}>{item.text}</ListItemText>
                    </ListContentGroup>
                    <ListButtonGroup>
                        <ListDoneButton onClick={handleToggleDoneTodolist(item.id)}>완료</ListDoneButton> 
                        <ListUpdateButton onClick={handleUpdateTodolist(item.id)}>수정</ListUpdateButton>
                        <ListDeleteButton onClick={handleDeleteTodolist(item.id)}>삭제</ListDeleteButton>
                    </ListButtonGroup>
                </ListItemStyle>
            )
          }
         )} 
        </ListContainer>
    )
}

export default ToDoListView;
~~~



## 200809 

### react todolist 

- 수정 버튼 구현
- 어제까지는 수정 상태 일 때, 인풋 창의 추가 버튼을 수정으로 바꿨었는데 오늘은 인풋창의 추가버튼을 그대로 두고, 수정 상태 일 때, 투두 리스트 목록에서 수정하고자 하는 투두 아이템이 텍스트에서 인풋창으로 바뀌도록 했다. 
- 이를 위해 ToDoListView.jsx 에서 if문을 이용해 에딧 상태 일 때는 인풋 컴포넌트를 사용했고, 버튼은 수정 취소, 수정, 삭제 버튼을 보이게 했다. 에딧 상태가 아닐 때에는 텍스트 컴포넌트를 사용했고, 버튼은 완료, 수정, 삭제버튼을 보이게 했다 . 
- 인풋 컴포넌트는 투두폼과 투두리스트뷰 에서 쓰고, onChange 이벤트를 만들어주었다. 처음에는 투두폼에서 만든 onChange를 그대로 이용했는데 그 결과, 투두리스트뷰의 인풋창에 값을 입력하는 대로 투두폼의 인풋창에도 같은 값이 나오는 바람에 투두리스트뷰의 onChange 를 다른 이름으로 따로 만들었다. 
-  const updateTodolist 는 사실 isEdit 상태만 true로 바꿔주고 싶었는데 왜 인지 그렇게는 안되었다. 
~~~javascript
const updateTodolist =  useCallback((id, text) => {
  
   // const findIndex = [...todolist].findIndex((item) => item.id === id);
   const findTarget = [...todolist].find(item => item.id ===id);

   if (findTarget) {
     findTarget.isEdit = true;
     
   }
      
   // const list = [...todolist].filter((item) => item.id !== id);
   // list.splice(findIndex, 0, findTarget);
   // setTodolist(list);
 }, [todolist]);
~~~
 - 이렇게 하면 투두리스트 아이템의 수정 버튼을 눌러도 먹통이다. 인풋창으로 바뀌어야하는데 바뀌지 않는다. 따로 에러메세지가 뜨진 않는다.
 ~~~
  const updateTodolist =  useCallback((id, text) => {
   
    const findIndex = [...todolist].findIndex((item) => item.id === id);
    const findTarget = [...todolist].find(item => item.id ===id);

    if (findTarget) {
      findTarget.isEdit = true;
      
    }
       
    const list = [...todolist].filter((item) => item.id !== id);
    list.splice(findIndex, 0, findTarget);
    setTodolist(list);
  }, [todolist]);
 ~~~
  - 이렇게 하면 수정버튼을 클릭했을 때 투두리스트 아이템의 텍스트가 인풋창으로 잘 변한다
  - 수정 상태에서 투두리스트 아이템 인풋창에 값을 입력하고, 수정버튼을 누르면 handleUpdateSubmitTodolist 이벤트가 발생하고, id 와 인풋내용이 인자로 전달된다. 인풋내용을 보내주지 않아서 findTarget.text 를 updatedText로 갱신해줄 수 없었는데 인풋내용을 인자로 전달하면서 해결했다.

  ### Today I Found Out
  - 대부분의 문제는 프롭스를 잘 내려주고, 받는 것의 문제였다. 
  - 그동안은 머리로만 생각하고, 코드를 짜려니 뒤죽박죽 어려웠는데 노트에 해야할 것들을 정리하고, 하나씩 해결해나가니까 그나마 할만 했다. 다음부터는 노트를 이용해야겠다.
  - edit 의 스테이트관리가 어려웠다. 다음 번엔 isEdit을 사용하지 않고, setEdit만으로 구현 가능 한지 알아봐야겠다. 
  - 추가, 삭제 함수를 계속 보면서 거의 베끼기 수준으로 수정 버튼을 구현하는데에도 꽤 오랜 시간이 걸렸다. 그래도 해냈으니 뿌듯하긴하다. 리스트를 추가했다가 모두 삭제했을 때 todolist의 길이가 0일 때 이미지를 띄우려고 했는데 그 부분이 잘 안된다. 다음에는 이 부분을 수정해봐야겠다. 앞으로도 리액트의 끈을 계속 잡고 있어야지..!^^

## 200810

### react todolist 
- 변수명을 지을 떄는 좀 더 시맨틱하게! 변수명을 좀 더 의미가 있도록 바꿔주었다
- 시맨틱: 시맨틱 요소 = 의미있는 요소를 뜻하며, 이 시맨틱 요소는 브라우저와 개발자 모두에게 요소의 의미나 목적을 명확하게 설명해 줄 수 있는 요소이다.
- 푸쉬할 때는 console.log 를 지우자
- **스프레드 문법**
~~~
const updateCancelTodolist = useCallback((id)=> {
  const findTarget = [...todolist].find(item => item.id ===id);

  setTodolist([...todolist])
  console.log("[...todolist]:", [...todolist]);
  console.log("[todolist]: ", [todolist]);
  
  findTarget.isEdit = false;
  
}, [todolist])
~~~

- setTodolist로 todolist의 상태를 관리할 때, 스프레드를 사용하면 얻는 이점은 무엇일까?
- 우선 함수를 살펴보았다. 
- 투두리스트에서 수정취소를 누를 때 실행되는 함수인데, 수정취소를 누르면 수정취소버튼을 누르기 전의 투두리스트 목록이 나타나야 한다. 
- 투두리스트를 그대로 복사해서, todolist 상태를 보여주는 것이 수정취소 버튼을 구현했을 떄 가장 안전하게 todolist 목록을 보여줄 수 있을 것 같다. 내가 생각한 첫번째 장점은 안정성이다. 
- 두번째 장점은 Spread 문법은 간편하게 배열을 복사할 수 있다는 장점이 있다.

> https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Spread_syntax
>
> Spread 문법은 배열을 복사할 때 1 레벨 깊이에서 효과적
>
> https://medium.com/coding-at-dawn/how-to-use-the-spread-operator-in-javascript-b9e4a8b06fab
>
> https://medium.com/javascript-in-plain-english/how-to-add-to-an-array-in-react-state-3d08ddb2e1dc

**리액트 최적화** 

> https://ui.toast.com/weekly-pick/ko_20161021/
성능 - 렌더링
React 애플리케이션은 여러 컴포넌트들이 트리 형태로 구성되어 있다. 특정 컴포넌트의 상태가 변경될 때 하위 컴포넌트들이 연쇄적으로 렌더링 되며 운영되는 구조다.

React는 기본적으로 실제로 변경된 부분만을 가려내어 DOM을 조작하도록 하는 최적화된 렌더링 엔진을 가지고 있다. 공식 사이트에 있는 O(n3)의 복잡도를 O(n)으로 줄이려는 방법문서는 상당히 흥미진진한데 기본적인 가이드 문서만 잘 따르면 자연스럽게 이 알고리즘이 적용돼 서비스에 문제가 없는 성능을 보장한다.

오히려 React 공식 문서에는 어설픈 최적화는 디버깅을 어렵게 할 수 있으니 꼭 필요한 곳에서만 최적화를 적용하라고 가이드하고 있다.

그럼 정말 필요한 경우가 어디에 있을까? 사실 어떠한 상황이 그러하다고 딱 집어 말하기는 어렵다. 다만 이 글에서 제시하는 상황을 생각해 보면 어느 정도 판단이 설 것이다.

앞서 React 애플리케이션의 전체 구조는 컴포넌트의 트리라고 이야기했다. 특정 부모 컴포넌트의 상태가 변경될 때 모든 하위 컴포넌트가 렌더링 되는데 이때 몇몇 컴포넌트는 렌더링 되지 않아도 되거나 (A), 어떤 조건에서만 렌더링 되면 되는 경우(B)가 있다. 이 부분이 바로 최적화 포인트이다.

가장 간단한 예를 들어보면 (A)는 마크업만 포함하는 컴포넌트를 들 수 있다. 물론 오버헤드가 크지 않겠지만 앱의 성능에 문제가 있는 경우 비슷한 컴포넌트 여럿에 적용해서 도움이 될 수도 있다.

반복적인 목록을 렌더링하는 경우 (B) 최적화는 큰 도움이 될 수 있다. 예를 들어 할 일 내용, 마감 시간, 선택 여부를 관리할 수 있는 TODO 목록이 있다고 하자. 3 가지 상태 중 뷰에 나타나는 것은 오직 할 일의 내용과 선택 여부뿐이다. 마감 시간의 변경은 웹 페이지에 나타나지 않아도 된다. 그렇다면 할 일 내용, 선택 여부 두 가지 상태의 변경만 DOM 조작으로 이어지면 된다. 그 조건을 shouldComponentUpdate 에 구현하면 목록의 양에 비례한 엄청난 성능 향상을 이룰 수 있다.

훌륭한 설계자는 조급하게 코드 최적화를 하지 않는다. React의 트리 렌더링 성능 최적화 방식은 이 말에 충실한 계획적 최적화를 가능하게 한다. 개인적으로 React를 선호하는 이유이기도 하다.



## Today I Found Out

  - spread 문법이 주는 장점에 대해 생각해봤다. 간편하다는 점 말고도 다른 장점이 또 장점이 있을 것 같다. 
  - 일단 오늘은 react에서 setState를 할 떄, 스프레드 문법을 사용해 State 관리를 할 수 있다는 것 정도는 기억해야겠다.
  - 리액트의 성능적인 측면에 관한 블로그 글을 읽었다. 리액트는 변경된 부분만 가려내 DOM을 조작하도록 하는 최적화된 렌더링 엔진을 가지고 있다고 한다. 최적화 포인트가 어디가 될 지 잘 감이 오지 않는다. 이 부분에 대해 더 공부해보고 싶다. 

