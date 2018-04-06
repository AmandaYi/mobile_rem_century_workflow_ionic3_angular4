---
    title: REM时代(mobile_rem_century_workflow_ionic3_angular4)
    desc: 在ionic3.x+和angular4.x+配合下的rem布局时代,亲们觉得好用就star我的吧
    author: 七月
---

## 声明,该REM时代设计思路,可以在任何的地方使用
- scss换成less,或者stylus等
- ionic+angular的项目,换成vue+veex,react等
- 直接在bootstrap+jquery原始项目中使用进行引入使用
 

### 在assets下加入屏幕改变重新计算HTML根节点的fontSize的JS文件
`src/assets/js/screencom.min.js`
### 接着在根目录的index.html中 写入
```html

<meta name="viewport" content=" viewport-fit=cover, width=device-width, initial-scale=1.0, minimum-scale=1.0, maximum-scale=1.0, user-scalable=no">

<script src="assets/js/screencom.min.js"></script>

```
### 在theme下面,添加一个base.scss文件
`src/theme/base.scss`
内容是
```scss
@charset "utf-8";
@function r($px) {
    @return $px /64px * 1rem;
}
```
### 在主题`src/theme/variables.scss`文件引入`base.scss`

```css
@import "ionic.globals";
@import "./base.scss";
```
### 使用
```scss
div{
    margin-left: r(12px);
    font-size: r(12px);
}
```


### 注意强调,如果设计图不是640px的宽度的话需要更改下面的两个文件

- base.scss 里面的分母 改为 尺寸除以10后的值
比如你的设计图是750px宽度的,那么base.scss文件就是如下
```scss
@charset "utf-8";
@function r($px) {
    @return $px /75px * 1rem;
}
```
- screencom.min.js 里面需要更改两个值,改为尺寸设计图的宽度
比如你的设计图是750px宽度的,那么screencom.min.js文件就是如下
```javascript
function i() {
        var t = r.getBoundingClientRect().width,
            i = /(iPhone|iPod|iPad|Android|ios|Windows Phone)/gim.test(navigator.userAgent),
            //需要改动的是这里的两个值
            n = i && t / l > 750 ? t : 750;
        t / l > n && (t = n * l);
        var a = t / 10;
        r.style.fontSize = a + "px", d.rem = e.rem = a
```

## 最后再次声明,该REM时代设计思路,可以在任何的地方使用
- scss换成less,或者stylus等
- ionic+angular的项目,换成vue+veex,react等
- 直接在bootstrap+jquery原始项目中使用进行引入使用
- 等等一些各种地方,比如 Electron
 
