### css动画-animation

使用 CSS 动画，必须首先为动画指定一些关键帧。关键帧包含元素在特定时间所拥有的样式。

**animation: name duration timing-function delay iteration-count direction;**

- `animation-name `:设置应用的动画名称，必须与规则keyframes配合使用。
- `animation-duration` :设置动画的持续时间，以秒或毫秒计。
- `animation-timing-function` :设置动画的过渡类型（同上transition-timing-function）。
- `animation-delay`: 设置动画的延迟时间。
- `animation-iteration-count` :设置动画循环次数。**infinite**：无限循环 || 具体次数
- `animation-direction`: 设置动画是否在循环中反向。**normal**：正常方向 || **alternate**：正常与反向交替

#### @keyframes 规则

###### 在 `@keyframes` 规则中指定 CSS 样式，动画将在特定时间逐渐从当前样式更改为新样式。

from是指动画开始的CSS样式，to是指动画结束的CSS样式。代表 0％开始和 100％完成

```javascript
@keyframes custom_animation_name{
	from {font-size: 50px;}
	to {font-size: 300px;}
}
```

通过使用百分比，您可以根据需要添加任意多个样式更改

```javascript
@keyframes custom_animation_name {
  0%   {background-color: red;}
  25%  {background-color: yellow;}
  50%  {background-color: blue;}
  100% {background-color: green;}
}
```

###### 将动画效果应用在指定的标签上

animation:动画效果的名称 时间（默认0s）

```javascript
h1{
	animation:custom_animation_name 6s;
}
```

