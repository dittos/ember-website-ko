다음으로, 템플릿에 하드코딩했던 부분을 고쳐서 할 일이 동적으로 출력되게 바꿔보겠습니다.

`js/router.js`에 `TodosRoute` 클래스를 추가합니다. 모든 할 일을 반환하는 `model` 함수를 포함합니다.

```javascript
// ... 다른 줄 생략 ...
Todos.TodosRoute = Ember.Route.extend({
  model: function () {
    return this.store.find('todo');
  }
});
```

전에는 이 클래스를 따로 구현하지 않아서, Ember.js가 [이름 짓기 규칙](/guides/concepts/naming-conventions/)에 따라 `todos` 템플릿을 렌더링하는 `Route`를 알아서 만들어 줬습니다.

이제는 별도의 동작(특정 모델 집합을 반환)이 필요해졌기 때문에 클래스를 직접 구현해서 원하는 동작을 추가한 것입니다.

`index.html`의 고정된 `<li>` 요소를 Handlebars의 `{{each}}` 헬퍼와 각 항목의 동적인 `{{title}}`로 바꿉니다.

```handlebars
<!--- ... 다른 줄 생략 ... -->
<ul id="todo-list">
  {{#each}}
    <li>
      <input type="checkbox" class="toggle">
      <label>{{title}}</label><button class="destroy"></button>
    </li>
  {{/each}}
</ul>
<!--- ... 다른 줄 생략 ... -->
```

이제 이 템플릿은 컨트롤러의 내용을 순회합니다. 여기서의 컨트롤러는 `ArrayController`의 인스턴스로, Ember.js에서 모델들을 담을 수 있도록 알아서 만들어 준 것입니다. 아직 별도의 동작이 필요하지 않기 때문에 프레임워크에서 제공한 기본 객체를 사용할 수 있습니다.

웹 브라우저를 새로 고침하여 모든 파일이 제대로 불러와지고 오류가 없는지 확인하세요.

### 미리보기
<a class="jsbin-embed" href="http://jsbin.com/EJISAne/1/embed?live">Ember.js • TodoMVC</a><script src="http://static.jsbin.com/js/embed.js"></script>
  
### 보충 자료

  * [이 단계에서 바뀐 점 (`diff` 형식)](https://github.com/emberjs/quickstart-code-sample/commit/87bd57700110d9dd0b351c4d4855edf90baac3a8)
  * [템플릿 안내서](/guides/templates/handlebars-basics)
  * [컨트롤러 안내서](/guides/controllers)
  * [이름 짓기 규칙 안내서](/guides/concepts/naming-conventions)
