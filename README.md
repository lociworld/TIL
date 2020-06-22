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

