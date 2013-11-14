이 단계에서는 사용자가 할 일을 완료 또는 미완료 상태로 바꾸고 바뀐 정보를 영구 저장할 수 있도록 애플리케이션을 수정하겠습니다.

할 일을 각각의 컨트롤러로 감쌀 수 있도록 `index.html`에서 `{{each}}` Handlebars 헬퍼에 `itemController` 인자를 추가합니다. 그리고 정적인 `<input type="checkbox">`을 `{{input}}` 헬퍼로 교체합니다.

```handlebars
<!--- ... 다른 줄 생략 ... -->
{{#each itemController="todo"}}
  <li {{bind-attr class="isCompleted:completed"}}>
    {{input type="checkbox" checked=isCompleted class="toggle"}}
    <label>{{title}}</label><button class="destroy"></button>
  </li>
{{/each}}
<!--- ... 다른 줄 생략 ... -->
```

이 `{{input}}`은 렌더링될 때 컨트롤러의 현재 `isCompleted` 속성값을 확인합니다. 사용자가 클릭했을 때 바뀐 체크 여부에 따라 컨트롤러의 `isComplete` 속성을 `true` 또는 `false`로 호출합니다.

각 항목을 위한 컨트롤러를 `itemController` 값에 맞게 `Todos.TodoController`라는 이름으로 구현합니다. `js/controllers/todo_controller.js`를 만들어 이 코드를 넣습니다. 물론 이 스크립트들을 다른 곳에 위치시킬 수도 있습니다. (전부 같은 파일에 넣어도 됩니다.) 하지만 이 안내서에서는 각 파일이 정해진 이름으로 각각 나눠져 있다고 가정합니다.

`js/controllers/todo_controller.js`에 `Todos.TodoController`와 `isCompleted` 속성을 선언합니다.

```javascript
Todos.TodoController = Ember.ObjectController.extend({
  isCompleted: function(key, value){
    var model = this.get('model');

    if (value === undefined) {
      // 속성이 getter로 쓰임
      return model.get('isCompleted');
    } else {
      // 속성이 setter로 쓰임
      model.set('isCompleted', value);
      model.save();
      return value;
    }
  }.property('model.isCompleted')
});
```

템플릿이 `isCompleted` 상태를 출력할 때 호출되면, 안에 감싸져 있는 `model`이 대신 결과를 돌려주도록 위임합니다. 사용자가 체크박스를 눌러 값과 함께 호출된 경우에는 `model`의 `isCompleted` 속성을 전달받은 값(`true` 또는 `false`)으로 설정하고, 모델의 바뀐 점을 영구 저장한 뒤, 체크박스가 올바르게 출력되도록 받은 값을 다시 돌려줍니다.

이 `isCompleted` 함수는 값이 `model.isCompleted`의 값에 의존하는 [계산된 속성(computed property)](/guides/object-model/computed-properties/)이라고 선언되어 있습니다.

`index.html`에서 `js/controllers/todo_controller.js`을 불러옵니다.

```html
<!--- ... 다른 줄 생략 ... -->
   <script src="js/models/todo.js"></script>
   <script src="js/controllers/todos_controller.js"></script>
   <script src="js/controllers/todo_controller.js"></script>
 </body>
<!--- ... 다른 줄 생략 ... -->
```

웹 브라우저를 새로 고침하여 모든 파일이 제대로 불러와지고 오류가 없는지 확인하세요. 이제 할 일의 `isCompleted` 속성을 바꿀 수 있어야 합니다.

### 미리보기
<a class="jsbin-embed" href="http://jsbin.com/UDoPajA/1/embed?live">Ember.js • TodoMVC</a><script src="http://static.jsbin.com/js/embed.js"></script>

### 보충 자료

  * [이 단계에서 바뀐 점 (`diff` 형식)](https://github.com/emberjs/quickstart-code-sample/commit/8d469c04c237f39a58903a3856409a2592cc18a9)
  * [Ember.Checkbox API 문서](/api/classes/Ember.Checkbox.html)
  * [Ember 컨트롤러 안내서](/guides/controllers)
  * [계산된 속성 안내서](/guides/object-model/computed-properties/)
  * [이름 짓기 규칙 안내서](/guides/concepts/naming-conventions)
