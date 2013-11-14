이제 픽스처(fixture) 데이터를 추가합니다. 아직 애플리케이션에 영구 저장 기능이 들어가지 않았을 때 픽스처로 샘플 데이터를 넣을 수 있습니다.

먼저 `js/application.js`를 수정하여 `ApplicationAdapter`가 `DS.FixtureAdapter`를 확장하도록 선언합니다. 어댑터(adapter)는 애플리케이션의 데이터 출처와 통신하는 일을 담당합니다. 대부분의 경우 웹 서비스 API가 되겠지만, 지금은 픽스처 데이터를 불러오는 어댑터를 사용합니다.

```javascript
window.Todos = Ember.Application.create();

Todos.ApplicationAdapter = DS.FixtureAdapter.extend();
```


그리고 `js/models/todo.js`에 다음 코드를 추가해서 픽스처 데이터를 넣습니다.

```javascript
// ... 다른 줄 생략 ...
Todos.Todo.FIXTURES = [
 {
   id: 1,
   title: 'Learn Ember.js',
   isCompleted: true
 },
 {
   id: 2,
   title: '...',
   isCompleted: false
 },
 {
   id: 3,
   title: 'Profit!',
   isCompleted: false
 }
];
```

웹 브라우저를 새로 고침하여 모든 파일이 제대로 불러와지고 오류가 없는지 확인하세요.

### 미리보기
<a class="jsbin-embed" href="http://jsbin.com/Ovuw/1/embed?live">Ember.js • TodoMVC</a><script src="http://static.jsbin.com/js/embed.js"></script>

### 보충 자료

  * [이 단계에서 바뀐 점 (`diff` 형식)](https://github.com/emberjs/quickstart-code-sample/commit/a586fc9de92cad626ea816e9bb29445525678098)
