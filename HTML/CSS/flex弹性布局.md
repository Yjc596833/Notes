视频查看地址：https://www.bilibili.com/video/BV1Lp4y1S7XM?from=search&seid=7340983328446679044

``` html
//弹性布局
display:flex
//垂直居中
align-items:center;
//水平居中
justify-content:center

<!--行-->
默认排序：flex-direction:row
反转排序：flex-direction:row-reverse
<!--列-->
默认：flex-direction:column
反转：flex-direction:column-reverse

<!--强行等分容器宽度且不换行-->
flex-wrap:nowarp
<!--项目根据自身宽度进行排列,如果超出父容器宽度则自然换行-->
flex-wrap:wrap  

<!--flex-grow-->
取值：默认为0，用于决定项目在有剩余空间的情况下是否放大，默认不放大；注意，即便设置了固定宽度，也会放大。假设默认三个项目中前两个项目都是0，最后一个是1，最后的项目会占满剩余所有空间

<!--flex-shrink-->
取值：默认1，用于决定项目在空间不足时是否缩小，默认项目都是1，即空间不足时大家一起等比缩小；注意，即便设置了固定宽度，也会缩小。但如果某个项目flex-shrink设置为0，则即便空间不够，自身也不缩小。

<!--flex-basis-->
取值：默认为auto,用于设置项目宽度，默认为auto时，项目会保持默认宽度，或者以width为自身的宽度，但如果设置了flex-basis,权重会width属性高，因此会覆盖width属性

```
![avatar](/flex1.jpg)

![avatar](/space-between.jpg)

![avatar](/space-around.jpg)

![avatar](/space-evenly.jpg)

![avatar](/align-itemscenter.jpg)

![avatar](/order.jpg)

<!--单个子项设置对齐 eg：align-self:flex-end-->
![avatar](/align-self.jpg)