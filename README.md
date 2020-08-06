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

- 원시 타입 (primitive data type)
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

한줄 주석은 `//` 다음에 작성하며 여러 줄 주석은 `/*`과 `*/`의 사이에 작성한다. 

다른 언어와 달리 자바스크립트에서는 블록 유효범위(Block-level scope)를 생성하지 않는다. 함수 단위의 유효범위(Function-level scope)만이 생성된다.

 원시 타입(Primitives)을 제외한 나머지 값들(함수, 배열, 정규표현식 등)은 모두 객체이다.

오늘은 자바스트립트의 개념과 기본 문법에 대해 학습했다.

다음 공부가 기대된다.

