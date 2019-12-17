####postcss

PostCSS 本身是一个功能比较单一的工具。它提供了一种方式用 JavaScript 代码来处理 CSS。利用PostCSS可以实现一些工程化的操作，如：自动添加浏览器前缀，代码合并，代码压缩等。
      官方网址：https://postcss.org/

安装：
	1. 安装node环境
	2. npm  install  postcss-cli –g
	3. -o 、-w
	4. postcss.config.js 配置到css文件夹同级

```css
/*	
 安装postcss:
 npm  install  postcss-cli
 
 转换文件：
 postcss src/layout.css -o dist/layout.css 
 持续监听转换文件：
 postcss src/layout.css -o dist/layout.css -w

 浏览器兼容：
 npm i autoprefixer

 css文件合并：
 npm i postcss-import

 css压缩：
 npm i cssnano

 css降级兼容低版本：
 npm i postcss-cssnext

 语法格式规则规范：
 npm i stylelint

 合并成雪碧图：
 npm i postcss-sprites
 */
 
 /* @import './release.css';
div{
    width: 100px; height: 200px;
    transform: rotate(45deg);
} */

:root{
    --color : red;
}

div{
    background: var(--color);
    color: var(--color);
    border: 1px var(--color) solid;
}

p{
    color: #fff;
}

.box1{
    background: url('./icon/2.jpg');
}
.box2{
    background: url('./icon/1.jpg');
}

```

配置文件

```js
const autoprefixer = require('autoprefixer');
const macimport = require('postcss-import');
const cssnano = require('cssnano');
const cssnext = require('postcss-cssnext');
const stylelint = require('stylelint');
const sprites = require('postcss-sprites');

module.exports = {
    plugins : [
        // autoprefixer({
        //     browsers : [' > 0% ']
        // }),
        // macimport,
        // cssnano
        cssnext,
        stylelint({
            "rules" : {
                "color-no-invalid-hex" : true
            }
        }),
        sprites({
            spritePath : './dist'
        })
    ]
};
```