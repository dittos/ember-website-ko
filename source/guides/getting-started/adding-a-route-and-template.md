다음으로, Ember.js 애플리케이션과 `/` 루트(route)를 생성하고 이전 단계에서 만든 정적인 목업을 Handlebars 템플릿으로 바꿀 것입니다.

`js` 디렉토리 안에 애플리케이션을 위한 `js/application.js`와 라우터를 위한 `js/router.js`를 만듭니다. 물론 이 스크립트들을 다른 곳에 위치시킬 수도 있습니다. (전부 같은 파일에 넣어도 됩니다.) 하지만 이 안내서에서는 각 파일이 정해진 이름으로 각각 나눠져 있다고 가정합니다.

`js/application.js`에 다음 코드를 추가합니다.

```javascript
window.Todos = Ember.Application.create();
```

`Ember.Application`의 새로운 인스턴스를 만들어 브라우저의 JavaScript 환경에서 사용할 수 있게 하는 코드입니다.

`js/router.js`에는 다음 코드를 추가합니다.

```javascript
Todos.Router.map(function () {
  this.resource('todos', { path: '/' });
});
```

이렇게 하면 Ember.js는 애플리케이션의 URL이 `'/'`일 경우 `todos` 템플릿을 렌더링하게 됩니다.

다음으로 `index.html`의 `<body>` 안쪽을 Handlebars 스크립트 태그로 감싸고, `js/application.js`와 `js/router.js`를 불러옵니다.

```html
<!-- ... 다른 줄 생략 ... -->
<body>
  <script type="text/x-handlebars" data-template-name="todos">

    <section id="todoapp">
      ... 다른 줄 생략 ...
    </section>

    <footer id="info">
      <p>Double-click to edit a todo</p>
    </footer>
  
  </script>

  <script src="js/libs/jquery.min.js"></script>
  <script src="js/libs/handlebars.js"></script>
  <script src="js/libs/ember.js"></script>
  <script src="js/libs/ember-data.js"></script>
  
  <script src="js/application.js"></script>
  <script src="js/router.js"></script>
<!-- ... 다른 줄 생략 ... -->
```

웹 브라우저를 새로 고침하여 모든 파일이 제대로 불러와지고 오류가 없는지 확인하세요.

### 미리보기
<a class="jsbin-embed" href="http://jsbin.com/OKEMIJi/1/embed?live">Ember.js • TodoMVC</a><script src="http://static.jsbin.com/js/embed.js"></script>

### 보충 자료

  * [이 단계에서 바뀐 점 (`diff` 형식)](https://github.com/emberjs/quickstart-code-sample/commit/8775d1bf4c05eb82adf178be4429e5b868ac145b)
  * [Handlebars 안내서](/guides/templates/handlebars-basics)
  * [Ember.Application 안내서](/guides/application)
  * [Ember.Application API 문서](/api/classes/Ember.Application.html)
