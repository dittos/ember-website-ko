다음으로 정적인 HTML `<input>`을 대신해서 더욱 복잡한 동작을 추가할 수 있는 Ember 뷰(view)로 교체합니다. `index.html`을 수정해서 `<input>`을 `{{input}}` 헬퍼로 바꿉니다.

```handlebars
<!--- ... 다른 줄 생략 ... -->
<h1>todos</h1>
{{input type="text" id="new-todo" placeholder="What needs to be done?" 
              value=newTitle action="createTodo"}}
<!--- ... 다른 줄 생략 ... -->
```

이렇게 하면 해당 위치에 기존과 같은 `id` 및 `placeholder`이 적용된 `<input>` 요소가 들어갑니다. 또한 이 템플릿의 컨트롤러의 `newTitle` 속성과 `<input>`의 `value` 속성이 연결됩니다. 둘 중 하나가 바뀌면 나머지 속성값도 자동으로 바뀌어서, 두 속성이 항상 동기화됩니다.

그리고 사용자와의 상호작용(엔터 키 입력)을 이 템플릿의 컨트롤러의 `createTodo` 메소드와 연결했습니다.

여태까지는 별도의 컨트롤러 동작이 필요하지 않았기 때문에 Ember.js에서 제공한 기본 컨트롤러 객체를 사용했습니다. 새로운 동작을 처리하기 위해, Ember.js가 [이름 짓기 규칙](/guides/concepts/naming-conventions)에 따라 찾을 수 있는 이름으로 컨트롤러를 구현하고 원하는 동작을 추가합니다. 이름 규칙에 따라 이 컨트롤러와 템플릿은 자동으로 연결됩니다.

`js/controllers/todos_controller.js` 파일을 추가합니다. 물론 이 스크립트들을 다른 곳에 위치시킬 수도 있습니다. (전부 같은 파일에 넣어도 됩니다.) 하지만 이 안내서에서는 각 파일이 정해진 이름으로 각각 나눠져 있다고 가정합니다.

`js/controllers/todos_controller.js`에는 Ember.js가 [이름 짓기 규칙](/guides/concepts/naming-conventions)에 따라 찾을 수 있는 이름으로 컨트롤러를 구현합니다.

```javascript
Todos.TodosController = Ember.ArrayController.extend({
  actions: {
    createTodo: function () {
      // "New Todo" 텍스트 필드에서 할 일 제목 가져오기
      var title = this.get('newTitle');
      if (!title.trim()) { return; }

      // 새로운 Todo 모델 생성
      var todo = this.store.createRecord('todo', {
        title: title,
        isCompleted: false
      });

      // "New Todo" 텍스트 필드 비우기
      this.set('newTitle', '');

      // 새 모델 저장
      todo.save();
    }
  }
});
```

이제 이 컨트롤러는 사용자 동작에 반응하여 `newTitle` 속성값을 제목으로 하고 `isComplete` 속성이 거짓인 할 일을 만듭니다. 그런 다음 `newTitle` 속성을 비우면, 템플릿과 동기화되어 텍스트 필드가 초기화됩니다. 마지막으로 할 일에서 아직 저장되지 않은 내용을 영구적으로 저장합니다.

`index.html`에서 `js/controllers/todos_controller.js`을 불러옵니다.

```html
<!--- ... 다른 줄 생략 ... -->
   <script src="js/models/todo.js"></script>
   <script src="js/controllers/todos_controller.js"></script>
 </body>
<!--- ... 다른 줄 생략 ... -->
```

웹 브라우저를 새로 고침하여 모든 파일이 제대로 불러와지고 오류가 없는지 확인하세요. 이제 `<input>`에 제목을 입력하고 엔터 키를 눌러서 할 일을 더 추가할 수 있어야 합니다.

### 미리보기
<a class="jsbin-embed" href="http://jsbin.com/ImukUZO/1/embed?live">Ember.js • TodoMVC</a><script src="http://static.jsbin.com/js/embed.js"></script>

### 보충 자료

  * [이 단계에서 바뀐 점 (`diff` 형식)](https://github.com/emberjs/quickstart-code-sample/commit/60feb5f369c8eecd9df3f561fbd01595353ce803)
  * [Ember.TextField API 문서](/api/classes/Ember.TextField.html)
  * [Ember 컨트롤러 안내서](/guides/controllers)
  * [이름 짓기 규칙 안내서](/guides/concepts/naming-conventions)
