### transition  -- 过渡

写法：**transition**：transition-property||transition-duration||transition-timing-function||transition-delay

#### 1）组成

1. `transition-property`:参与过渡的属性，例如：width、height、background...
2. `transition-duration`:过渡的持续时间，单位秒s或毫秒ms
3. `transition-timing-function`：过渡的动画类型
4. `transition-delay`：延迟过渡的时间，单位秒s或毫秒ms，如果提供多个属性值，以逗号进行分隔

#### 2）**transition-timing-function**

`transition-timing-function`是动画运动的曲线，它一共有6个值。

- `ease` -平滑过渡： 指定一个缓慢开始，然后快速，然后慢慢结束的过渡效果(这是默认值)
- `linear` - 线性过渡：指定从开始到结束以相同速度的转换效果
- `ease-in` - 由慢到快：指定缓慢启动的过渡效果
- `ease-out` - 由快到慢：指定一个缓慢结束的过渡效果
- `ease-in-out` - 由慢到快再倒慢：指定开始和结束缓慢的过渡效果
- `cubic-bezier(n,n,n,n)` - 特定的贝塞尔曲线类型，4个数值需在[0, 1]区间内
