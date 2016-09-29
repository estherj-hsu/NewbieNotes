## CSS Modules 使用建議
 - 避免針對單一元件做多樣式套疊
 - 避免使用選擇器
 - 以`composes`重複使用樣式

## `:global` 全域模式
針對 `:global` 下的樣式不做樣式名稱編譯

## `composes` 合併樣式
類似 @extend 功能，導入基本樣式

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
-
    import btn from './btn.css';
    buttonElem.outerHTML = `<button class=${btn.submit}>Submit</button>`
-
    <button class="btn--fec26 btn--submit-abc53">Submit</button>

## References
 - [Modular CSS with React](https://medium.com/@pioul/modular-css-with-react-61638ae9ea3e#.xk8dhx3fn)
 - [CSS Modules 详解及 React 中实践](https://zhuanlan.zhihu.com/p/20495964)
 - [React CSS Modules](https://github.com/gajus/react-css-modules)
 - [react-css-modules(中文)](https://segmentfault.com/a/1190000004530909#articleHeader0)