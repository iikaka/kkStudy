### css变量

#### 语法

CSS 变量当前有两种形式：

- 变量，就是拥有合法标识符和合法的值。可以被使用在任意的地方。可以使用var()函数使用变量。例如：var(--example-variable)会返回--example-variable所对应的值
- 自定义属性。这些属性使用--*where*的特殊格式作为名字。例如--example-variable: 20px;即使一个css声明语句。意思是将20px赋值给--example-varibale变量。

#### 基本用法

在css中，变量是一种特殊的样式，可以在css中设置一个变量，可以在子元素中获取到这个值。

```javascript
//声明变量
.root {
  --color: red;
}
//使用变量
.son {
  color: var(--color);
}
```

> 以上的代码，就是在root中定义了一个变量，变量名为--color，变量值为red。
> 在子元素中，可以通过var(--color)来获取这个变量的值。

#### 用途

- 方便的管理统一的属性
- js统一控制

使用js可以方便的获取到元素上到css变量的值，并且可以统一控制。

```javascript
// 获取一个 Dom 节点上的 CSS 变量
element.style.getPropertyValue("--my-var");

// 获取任意 Dom 节点上的 CSS 变量
getComputedStyle(element).getPropertyValue("--my-var");

// 修改一个 Dom 节点上的 CSS 变量
element.style.setProperty("--my-var", jsVar + 4);
```

#### 示例

使用CSS变量来实现一个元素的样式随着滚动改变，只改变CSS变量的值，然后来计算样式。

```javascript
let navScale = 0;
let scrollProcess=document.body.scrollTop + window.innerHeight;
navScale = ( scrollProcess - this.outer_Start_Height ) /  window.innerHeight;
// 把navScale限制在0-1内
navScale = Math.min(this.max, Math.max(0, navScale));
this.$refs.stickyouter.style.setProperty('--scroll-height',navScale)
```

以上代码，改变了–scroll-height的CSS变量，他会在0-1之间
然后，我们在CSS中使用他

```javascript
.sticky1{
    opacity: var(--scroll-height);
}
.sticky2{
    transform: translateX(calc(1000px - calc(var(--scroll-height) * 1000px)));
}
```

