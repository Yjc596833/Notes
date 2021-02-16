https://bennettfeely.com/clippy/

##### 图片处理：
``` html
Css
filter:
<!--调低图片亮度 从1设为0.4 -->
filter:brightness(0.4)
<!--把图片的灰度 从0设为1 -->
filter:grayscale(1)
<!--把图片的透明度 从1设为0.3 -->
filter:opacity(0.3)
<!--设置图片的模糊度,把图片模糊两个像素-->
filter:blur(2px)
<!--反转图片的颜色 从0设为1-->
filter:invert(1)
<!-- clip-path 遮罩效果的属性 控制只显示图片的某些区域-->
<!--五角星-->
clip-path:polygon(50% 0%,61% 35%,98% 35%,68% 57%,79% 91%,50% 70%,21% 91%,32% 57%,
2% 35%,39% 35%)
<!--假如我们给文字设置 mix-blend-mode 为 screen-->
mix-blend-mode:screen; //文字就可以变透明显示背景图片的内容了
```
