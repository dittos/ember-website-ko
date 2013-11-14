코드를 짜기 전에 만들 애플리케이션의 구성을 대략 스케치해 보겠습니다. 텍스트 편집기에서 `index.html`을 만듭니다. 이 파일에는 완성될 애플리케이션의 HTML 템플릿이 들어가며, 추가적인 이미지, 스타일시트, JavaScript 리소스를 불러오는 역할을 합니다.

일단 다음 내용을 `index.html`에 넣습니다.

```html
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Ember.js • TodoMVC</title>
    <link rel="stylesheet" href="style.css">
  </head>
  <body>
    <section id="todoapp">
      <header id="header">
        <h1>todos</h1>
        <input type="text" id="new-todo" placeholder="What needs to be done?" />
      </header>

      <section id="main">
        <ul id="todo-list">
          <li class="completed">
            <input type="checkbox" class="toggle">
            <label>Learn Ember.js</label><button class="destroy"></button>
          </li>
          <li>
            <input type="checkbox" class="toggle">
            <label>...</label><button class="destroy"></button>
          </li>
          <li>
            <input type="checkbox" class="toggle">
            <label>Profit!</label><button class="destroy"></button>
          </li>
        </ul>

        <input type="checkbox" id="toggle-all">
      </section>

      <footer id="footer">
        <span id="todo-count">
          <strong>2</strong> todos left
        </span>
        <ul id="filters">
          <li>
            <a href="all" class="selected">All</a>
          </li>
          <li>
            <a href="active">Active</a>
          </li>
          <li>
            <a href="completed">Completed</a>
          </li>
        </ul>

        <button id="clear-completed">
          Clear completed (1)
        </button>
      </footer>
    </section>

    <footer id="info">
      <p>Double-click to edit a todo</p>
    </footer>
  </body>
</html>
```

[스타일시트](http://emberjs.com.s3.amazonaws.com/getting-started/style.css)와 [배경 이미지](http://emberjs.com.s3.amazonaws.com/getting-started/bg.png)를 다운로드 받아 `index.html`과 같은 디렉토리에 두세요.

`index.html`을 웹 브라우저에서 열어 모든 요소가 제대로 불러와지는지 확인하세요. 하드코딩된 `<li>` 요소 세 개가 들어간 TodoMVC 애플리케이션이 보여야 합니다.

### 미리보기
<a class="jsbin-embed" href="http://jsbin.com/uduyip/2/embed?live">Ember.js • TodoMVC</a><script src="http://static.jsbin.com/js/embed.js"></script> 

### 보충 자료

  * [이 단계에서 바뀐 점 (`diff` 형식)](https://github.com/emberjs/quickstart-code-sample/commit/4d91f9fa1f6be4f4675b54babd3074550095c930)
  * [TodoMVC 스타일시트](http://emberjs.com.s3.amazonaws.com/getting-started/style.css)
  * [TodoMVC 배경 이미지](http://emberjs.com.s3.amazonaws.com/getting-started/bg.png)
  
