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

