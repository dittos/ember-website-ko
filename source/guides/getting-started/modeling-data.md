이제 할 일 항목을 표현할 모델 클래스를 생성합니다.

`js/models/todo.js` 파일을 만들어 다음 코드를 추가합니다.

```javascript
Todos.Todo = DS.Model.extend({
  title: DS.attr('string'),
  isCompleted: DS.attr('boolean')
});
```

이 코드는 새로운 `Todo` 클래스를 생성해서 애플리케이션의 이름 공간에 넣습니다. 각 항목은 `title`과 `isCompleted` 속성을 가지게 됩니다.

물론 이 스크립트들을 다른 곳에 위치시킬 수도 있습니다. (전부 같은 파일에 넣어도 됩니다.) 하지만 이 안내서에서는 각 파일이 정해진 이름으로 각각 나눠져 있다고 가정합니다.

마지막으로, `index.html`에서 새로 만든 파일을 불러옵니다.

```html
<!-- ... 다른 줄 생략 ... -->
  <script src="js/models/todo.js"></script>
</body>
<!-- ... 다른 줄 생략 ... -->
```

웹 브라우저를 새로 고침하여 모든 파일이 제대로 불러와지고 오류가 없는지 확인하세요.

### 미리보기
<a class="jsbin-embed" href="http://jsbin.com/AJoyOGo/1/embed?live">Ember.js • TodoMVC</a><script src="http://static.jsbin.com/js/embed.js"></script>

### 보충 자료

  * [이 단계에서 바뀐 점 (`diff` 형식)](https://github.com/emberjs/quickstart-code-sample/commit/a1ccdb43df29d316a7729321764c00b8d850fcd1)
  * [스토어 사용 안내서](/guides/models/using-the-store)
  * [모델 정의 안내서](/guides/models/defining-models)
