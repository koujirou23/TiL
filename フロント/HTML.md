# HTML

### 入れ子になったリスト

[![Image from Gyazo](https://i.gyazo.com/346f15f5e1fb40675933db6bd7e0747a.png)](https://gyazo.com/346f15f5e1fb40675933db6bd7e0747a)

```
  <ul>
    <li>野菜</li>
    <li>お肉
      <ul>
        <li>牛肉</li>
        <il>豚肉</il>
        <il>鶏肉</il>
      </ul>
    </li>
  </ul>
```

### 説明リスト

[![Image from Gyazo](https://i.gyazo.com/9131639189f86ea2da0fda8504fdb1e5.png)](https://gyazo.com/9131639189f86ea2da0fda8504fdb1e5)

```
  <dl>
    <dt>HTML</dt>
    <dd>HTMLの説明です</dd>

    <dt>CSS</dt>
    <dd>CSSの説明です</dd>

    <dt>JavaScript</dt>
    <dd>JavaScriptの説明です</dd>
  </dl>
```

### 著作権表記

[![Image from Gyazo](https://i.gyazo.com/9449a6535704af257dec256b48671890.png)](https://gyazo.com/9449a6535704af257dec256b48671890)

```
<p><small>&copy; company name </small></p>
<p>&copy; company name</p>
```

### コードの自動補完
```
<div id="container"></div> <!-- #container →　tab -->
  <div class="cls"></div> <!-- .cls → tab -->
  <span class="cls"></span> <!-- span.cls → tab -->
  
  <div id="container">      <!-- #container>.cls → tab -->
    <div class="cls"></div>
  </div>

  <div id="container">    <!-- #container>.cls*6 →　tab -->
    <div class="cls"></div>
    <div class="cls"></div>
    <div class="cls"></div>
    <div class="cls"></div>
    <div class="cls"></div>
    <div class="cls"></div>
  </div>

  <div id="container">    <!-- #container>.cls-$*6 →　tab -->
    <div class="cls-1"></div>
    <div class="cls-2"></div>
    <div class="cls-3"></div>
    <div class="cls-4"></div>
    <div class="cls-5"></div>
    <div class="cls-6"></div>
  </div>

  <div id="container">    <!-- #container>.cls-$$*6 →　tab -->
    <div class="cls-01"></div>
    <div class="cls-02"></div>
    <div class="cls-03"></div>
    <div class="cls-04"></div>
    <div class="cls-05"></div>
    <div class="cls-06"></div>
  </div>
```
