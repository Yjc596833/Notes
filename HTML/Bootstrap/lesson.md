<!--
 * @Author: your name
 * @Date: 2020-11-23 11:58:00
 * @LastEditTime: 2020-11-25 10:59:58
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \Notes\HTML\Bootstrap\lesson1.md
-->

####  ul>li{导航栏}*8

####  div{$}*4

```
<div class="col-lg-3 col-md-4 col-sm-6 col-xs-12"></div>

```
#### 列嵌套最好加一个行 row ,这样可以取消父元素的padding值 而且高度自动和父级一样高


#### 偏移 
```
<div class="col-md-4 col-md-offset-4"></div>
col-md-offset-4 向右偏移4单位  bootstrap3
offset-md-4 向右偏移4单位  bootstrap3
```

```
    <div class="row">
        <div class="col-lg-4 col-lg-push-8">左侧</div>
        <div class="col-lg-8 col-lg-pull-4">右侧</div>
    </div>

    隐藏：
    .hidden-xs 超小屏
    .hidden-sm 小屏
    .hidden-md 中屏
    .hidden-lg 大屏
```


### 官网bootstrap4（隐藏相关部分代码）
```
https://getbootstrap.com/docs/4.0/utilities/display/#hiding-elements 
```

####  举例：在 >=md 的媒体宽度下可见
```
 <img src="./images/HeaderTitle.png" alt="" class="d-none d-md-block">  
```

#### 举例：在 <md的媒体宽度下可见
```
<span class="d-block d-md-none">BLOG</span>
```

移动端技术选型：

- 流式布局（百分比布局）
- flex弹性布局（推荐）
- rem适配布局（推荐）
- 响应式布局


```
SHIFT + CTRL + 鼠标

SHIFT + ALT  +  F   对齐

```

```
Bootstrap4 中 偏移 直接 offset-md-*
```