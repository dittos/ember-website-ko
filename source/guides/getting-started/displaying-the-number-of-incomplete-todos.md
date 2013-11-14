다음으로 하드코딩된 완료 할 일 갯수 대신 실제 갯수가 반영되도록 만들어 보겠습니다. `index.html`이 두가지 속성을 사용하게 합니다.

```handlebars
<!--- ... 다른 줄 생략 ... -->
<span id="todo-count">
  <strong>{{remaining}}</strong> {{inflection}} left
</span>
<!--- ... 다른 줄 생략 ... -->
```

이 속성들을 해당 템플릿의 컨트롤러 `Todos.TodosController`에 구현합니다.

```javascript
// 귀띔: 다음 코드는 'actions' 객체에 넣으면 안됩니다.

// ... 다른 줄 생략 ...
remaining: function () {
  return this.filterBy('isCompleted', false).get('length');
}.property('@each.isCompleted'),

inflection: function () {
  var remaining = this.get('remaining');
  return remaining === 1 ? 'item' : 'items';
}.property('remaining'),
// ... 다른 줄 생략 ...
```

`remaining` 속성은 `isCompleted` 속성값이 거짓인 할 일의 수를 돌려줍니다. 만약 어떤 할 일의 `isCompleted` 속성이 바뀌면 이 속성도 다시 계산됩니다. 이 속성값이 바뀌면, 템플릿에서 갯수를 출력하는 부분이 자동으로 새로운 값을 반영합니다.

`inflection` 속성은 목록에 있는 할 일의 수에 따라 단어 "item"의 복수 또는 단수형을 돌려줍니다. 이 속성값이 바뀌면, 템플릿에서 갯수를 출력하는 부분이 자동으로 새로운 값을 반영합니다.

웹 브라우저를 새로 고침하여 모든 파일이 제대로 불러와지고 오류가 없는지 확인하세요. 이제 남은 할 일 갯수가 정확히 나타나야 합니다.

### 미리보기
<a class="jsbin-embed" href="http://jsbin.com/onOCIrA/1/embed?live">Ember.js • TodoMVC</a><script src="http://static.jsbin.com/js/embed.js"></script>
  
### 보충 자료

  * [이 단계에서 바뀐 점 (`diff` 형식)](https://github.com/emberjs/quickstart-code-sample/commit/b418407ed9666714c82d894d6b70f785674f7a45)
  * [계산된 속성 안내서](/guides/object-model/computed-properties/)
