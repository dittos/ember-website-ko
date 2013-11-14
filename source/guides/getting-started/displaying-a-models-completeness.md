TodoMVC에서는 완료된 할 일의 `<li>` 요소에 `completed` CSS 클래스를 적용해서 취소선을 긋습니다. 할 일의 `isCompleted` 속성이 참일 때 CSS 클래스를 적용하도록 `index.html`을 수정합니다.

```handlebars
<!--- ... 다른 줄 생략 ... -->
<li {{bind-attr class="isCompleted:completed"}}>
  <input type="checkbox" class="toggle">
  <label>{{title}}</label><button class="destroy"></button>
</li>
<!--- ... 다른 줄 생략 ... -->
```

이 코드는 할 일의 `isCompleted` 속성이 참이면 `completed` CSS 클래스를 추가하고, 속성이 거짓으로 바뀌면 클래스를 뗍니다.

픽스처의 첫번째 할 일의 `isCompleted` 속성값은 `true`였습니다. 애플리케이션을 새로 고침하면 첫번째 항목에 취소선이 그어져서 완료되었다는 것을 알 수 있습니다.

### 미리보기
<a class="jsbin-embed" href="http://jsbin.com/oKuwomo/1/embed?live">Ember.js • TodoMVC</a><script src="http://static.jsbin.com/js/embed.js"></script>
  
### 보충 자료

  * [이 단계에서 바뀐 점 (`diff` 형식)](https://github.com/emberjs/quickstart-code-sample/commit/b15e5deffc41cf5ba4161808c7f46a283dc2277f)
  * [bind-attr API 문서](/api/classes/Ember.Handlebars.helpers.html#method_bind-attr)
  * [bind and bind-attr (Peter Wagenet 작성)](http://www.emberist.com/2012/04/06/bind-and-bindattr.html)
