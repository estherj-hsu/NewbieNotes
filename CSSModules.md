## CSS Modules Tips
 - 避免針對單一元件做多樣式套疊（ex. `style="logo120 logo1x logo--game1"`）
 - 避免使用選擇器
 - 以`composes`重複使用樣式

## `:global` 全域模式
針對 `:global` 下的樣式，不做樣式名稱編譯

## `composes` 合併樣式
類似 `@extend` 功能，用於導入重複樣式，達成多樣式套疊

### CSS

```
    /* components/btn.css */
    .btn {
        cursor: pointer;
    }

    /* colors.css */
    .c-pr-red {
        color: #D50000;
    }

    .submit {
        composes: btn;
        background-color: c-pr-red from './colors.css'; /* 從其他css導入樣式 */
    }
    .reset {
        composes: btn;
        background-color: blue;
    }
```

### JS
```
    import btn from './btn.css';
    buttonElem.outerHTML = `<button class=${btn.submit}>Submit</button>`
```

### Compiled CSS
```
    <button class="btn--fec26 btn--submit-abc53">Submit</button>
```

## 現行系統實踐問題
 - 無法與目前系統併行 😱
 - `:global`架構需重新調整，抽出共用元件與變數，但會過於龐大
 - 圖檔需跟隨各個元件，須考量路徑管理（層級/lang/...）與sprite（單一元件sprite必要性？統一管理可能性？）

### 待確認
 - 語系問題
 - 畫面框架 & RWD
 - 圖片問題（抽出 `/img/sprite/` 再試一次～）

## References
 - [Modular CSS with React](https://medium.com/@pioul/modular-css-with-react-61638ae9ea3e#.xk8dhx3fn)
 - [CSS Modules Welcome to the Future](https://glenmaddern.com/articles/css-modules)
 - [Embracing Constraint with CSS Modules](https://medium.com/cartogram/embracing-constraint-with-css-modules-89ba3bbcb95d#.6w9h41hv0)
 - CSS Modules Series
    - [What are CSS Modules and why do we need them?](https://css-tricks.com/css-modules-part-1-need/)
    - [How to get started with CSS Modules](https://css-tricks.com/css-modules-part-2-getting-started/)
    - [React + CSS Modules = 😍](https://css-tricks.com/css-modules-part-3-react/)
 - [CSS Modules 详解及 React 中实践](https://zhuanlan.zhihu.com/p/20495964)
 - [React CSS Modules](https://github.com/gajus/react-css-modules)
 - [react-css-modules(中文)](https://segmentfault.com/a/1190000004530909#articleHeader0)
 - [CSS Modules by Example](http://andrewhfarmer.com/css-modules-by-example/)
 - [CSS Modules Webpack Demo](https://css-modules.github.io/webpack-demo/)
 - [Modular CSS](https://amobiz.github.io/2016/04/22/modular-css-notes/)
 - [Understanding the CSS Modules Methodology](https://www.sitepoint.com/understanding-css-modules-methodology/)
 - [CSSConf 2015 筆記(二) – CSS Modules](https://hsinyu00.wordpress.com/2016/02/21/cssconf-2015-%E7%AD%86%E8%A8%98%E4%BA%8C-css-modules/)
 - [Smarter CSS builds with Webpack](https://www.bensmithett.com/smarter-css-builds-with-webpack/)
 - [Smarter CSS builds with Webpack (中文)](http://blog.xunuo.com/smarter-css-builds-with-webpack/)

### Project Structure
 - [How to Structure a React Project?](https://reactjsnews.com/structuring-react-projects)
 - [Using webpack to build React components and their assets](https://simonsmith.io/using-webpack-to-build-react-components-and-their-assets/)
