TodoMVC 예제는 몇가지 라이브러리에 의존합니다.
  
  * [jQuery](http://code.jquery.com/jquery-1.10.2.min.js)
  * [Handlebars](http://builds.handlebarsjs.com.s3.amazonaws.com/handlebars-1.0.0.js)
  * [Ember.js 1.0](http://builds.emberjs.com/tags/v1.0.0/ember.js)
  * [Ember Data 1.0 beta](http://builds.emberjs.com/tags/v1.0.0-beta.3/ember-data.js)

이 예제에서 위의 모든 파일은 `index.html`과 같은 디렉토리의 `js/libs` 폴더에 있어야 합니다. 다음 순서대로 `index.html`의 `</body>` 태그 전에 `<script>` 태그를 추가하여 라이브러리를 불러옵니다.

```html
<!-- ... 다른 줄 생략 ... -->
  <script src="js/libs/jquery-1.10.2.min.js"></script>
  <script src="js/libs/handlebars-1.0.0.js"></script>
  <script src="js/libs/ember.js"></script>
  <script src="js/libs/ember-data.js"></script>
</body>
<!-- ... 다른 줄 생략 ... -->
```

웹 브라우저를 새로 고침하여 모든 파일이 제대로 불러와지고 오류가 없는지 확인하세요.

### 미리보기
<a class="jsbin-embed" href="http://jsbin.com/ijefig/2/embed?live">Ember.js • TodoMVC</a><script src="http://static.jsbin.com/js/embed.js"></script>
 
### 보충 자료

  * [이 단계에서 바뀐 점 (`diff` 형식)](https://github.com/emberjs/quickstart-code-sample/commit/0880d6e21b83d916a02fd17163f58686a37b5b2c)
