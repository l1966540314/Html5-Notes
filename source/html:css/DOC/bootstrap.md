####Bootstrap
Bootstrap 是最受欢迎的 HTML、CSS 和 JS 框架，用于开发响应式布局、移动设备优先的 WEB 项目。

特色：
1. 响应式布局
2. 基于flex的栅格系统
3. 丰富的组件和工具方法
4. 常见交互使用

官网：
https://getbootstrap.com/

版心
 `<div class="container"></div>`

通栏
`<div class="container-fluid"></div>`

```html
/**
默认等分行
row:行 默认每行12列
col:列
w-100:换行
*/
        <div class="row">
            <div class="col">aaaaa</div>
            <div class="col">bbbbb</div>
            <div class="w-100"></div>
            <div class="col">ccccc</div>
        </div>
 /**
 sm:宽小于sm换行显示
 sm:576px
 md:768px
 lg:992px
 xl:1200px
 */   
        <div class="row">
            <div class="col-sm">ddddd</div>
            <div class="col-sm">eeeee</div>
            <div class="col-sm">fffff</div>
        </div>
/*
col-5:占row12份的5份
3个5份超过12份，最后一个换行
*/
        <div class="row">
            <div class="col-5">ddddd</div>
            <div class="col-5">eeeee</div>
            <div class="col-5">fffff</div>
        </div>
/*
col-auto:根据内容适应宽度
*/
        <div class="row">
            <div class="col-auto">ddddd</div>
            <div class="col-auto">eeeee</div>
            <div class="col-auto">fffff</div>
        </div>
/*
col-md-6 col-lg-4 col-xl-3:
md时一行显示2个（12/6），lg时一行显示3个（12/4），xl一行显示4个（12/3）
*/
        <div class="row">
            <div class="col-md-6 col-lg-4 col-xl-3">ddddd</div>
            <div class="col-md-6 col-lg-4 col-xl-3">eeeee</div>
            <div class="col-md-6 col-lg-4 col-xl-3">fffff</div>
            <div class="col-md-6 col-lg-4 col-xl-3">ddddd</div>
            <div class="col-md-6 col-lg-4 col-xl-3">eeeee</div>
            <div class="col-md-6 col-lg-4 col-xl-3">fffff</div>
            <div class="col-md-6 col-lg-4 col-xl-3">ddddd</div>
            <div class="col-md-6 col-lg-4 col-xl-3">eeeee</div>
            <div class="col-md-6 col-lg-4 col-xl-3">fffff</div>
        </div>
/**
no-gutters:去掉默认空隙
*/
        <div class="row no-gutters">
            <div class="col">aaaaa</div>
            <div class="col">bbbbb</div>
            <div class="col">ccccc</div>
        </div>
/**
justify-content-end:和flex一样设置行排列
align-items-center:设置item项目分布
*/
        <div class="row justify-content-end align-items-center" style="height:100px; border:1px red solid;">
            <div class="col-4" style="height:30px;">11111</div>
            <div class="col-4 align-self-end" style="height:30px;">22222</div>
        </div>
/**
    mr-auto : margin-right : auto;
    mt-5 : margin-top : 5rem;
    mt-md-5 : margin-top : 5rem; md响应式范围内添加
    mx-5 : margin-left : 5rem; margin-right : 5rem;
    my-5 : margin-top : 5rem; margin-bottom : 5rem;
    mt-n5 : margin-top : -5rem;
    py-5 : padding-top : 5rem; padding-bottom : 5rem;
*/
```