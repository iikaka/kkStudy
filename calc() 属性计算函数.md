# calc

#### 语法

calc()函数允许在我们属性值之间进行加减乘除四则运算，可以使用百分比、px、em、rem等单位

比如，<length>，<frequency>，<angle>，<time>，<number> 或者 <integer> 数据类型。

calc() 函数可以嵌套。在函数里边，会被视为简单的括号表达式，所以直接写括号就行

```javascript
/* property: calc(expression) */ 
.foo{
    width: calc(50vw - 3rem);
    padding: calc(20% + 10px);
    transform: rorate( calc(1turn + 28deg) );
    background: hsl(100, calc(3 * 20%) ,40%);
    font-size: calc(50vw / 3);
    height: calc( 100vw / calc(20% + 10px) ); //嵌套calc
    height: calc( 100vw / (20% + 10px) ); //嵌套calc
}
```

> 其中：
>
> expression参数是一个数学表达式，结果将采用运算后的返回值
>
> 加法和减法的运算符号两边必须有空格
>
> 乘法两个值之间必须有一个为数字，除法左边必须为数字，乘除法的两个值之间只能有一个有单位

##### 在less中使用calc函数需要注意：less的计算方式跟calc方法有重叠，两者在一起有冲突

```javascript
@containerHeight: 500px;
@inputHeight: 50px;
.foo{
    position: absolute;
    //写法一
    top: ~"calc(@{containerHeight}/2 - @{inputHeight}/2 + 10px)";
    //写法二
    left: calc(~"@{containerHeight}/2 - @{inputHeight}/2 + 10px");
}
```

> 注意：
>
> - 变量一定要用`@{}`包裹起来。
> - 两种方法中`""`和`~`的使用位置。

#### 使用 calc()

##### Example 1 - 居中元素

在元素需要绝对定位或者固定定位的时候，不能使用flex的时候，可以采用这种方式

不使用calc

```javascript
.foo {
    position:absolute;
    top:50%;
    left:50%;
    margin-top:-100px;
    margin-left:-100px; // 移动自身宽高的一半
}
```

使用calc

```javascript
.foo {
    position:absolute;
    top:calc(50% - 100px);
    left:calc(50% - 100px);
}
```

##### Example 2 - 创建根栅格尺寸

使用 rem，设置根元素的字体大小为视口宽度的一部分。使用calc()函数创建一个基于视口的栅格。

```javascript
html{
	font-size:clac(100vw / 30);
}
```

现在 1rem 为视口宽度的 1/30。

##### Example 3 - 自动调整表单域的大小以适应其容器的大小

calc()用来确保一个表单域的大小适合当前的可用空间，而不会在保持合适的外边距的同时，因挤压超出其容器的边缘。

```javascript
input {
  padding: 2px;
  display: block;
  width: calc(100% - 1em);
}
.box {
  width: calc(100% / 6);
  border: 1px solid black;
  padding: 4px;
}
```

这个例子中，form 元素自身使用了窗口可用宽度的 1/6，然后，为了让 form 元素内部的 input 元素保持合适的大小，我们再一次使用了 `calc()`，让它的宽度为其容器的宽度减 1em。

- ##### Example 4 - 使用 CSS 变量嵌套使用 calc()

```javascript
.foo {
  --widthA: 100px;
  --widthB: calc(var(--widthA) / 2);
  --widthC: calc(var(--widthB) / 2);
  width: var(--widthC);
}
```

这个 `width` 属性的值就直接相当于 `calc( ( 100px / 2) / 2)` 