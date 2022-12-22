### transform --- 变换

#### 1）属性

##### ① **旋转`rotate`** : rotate (xx deg)(2D)

​	以中心为基点，deg表示旋转的角度，为负数时表示逆时针旋转。

##### ② **扭曲`skew`**: skew (x,y)， skewX (x)， skewY (y)

​	以中心为基点，第一个参数是水平方向扭曲角度，第二个参数是垂直方向扭曲角度

##### ③ 缩放`scale`:scale (x,y)，scaleX (x,1)， scaleY (1,Y)

​	缩放基数为1，如果其值大于1元素就放大，反之其值小于1为缩小

##### ④ **移动`translate`**:  translate (x,y) ，translateX (x) ，translateY (y)

​	以中心为基点按照设定的x,y参数值,对元素进行进行平移

##### ⑤ 矩阵变形`matrix`：matrix(n,n,n,n,n,n) 指定一个2D变换，相当于直接应用一个[a,b,c,d,e,f]变换矩阵

#### 2）`transform`不会触发回流，和重绘。

##### 注：

> ##### ① 基点 transform-origin
>
> ​	所有操作的默认的基点都在中心位置，我们可以使用`transform-origin：(x,y)`来改变元素基点。
>
> ​	x可以取left，center ，right，水平方向取值，默认：left=0%; center=50%; right=100%；
>
> ​	y可以取top，center，bottom，垂直方向取值，默认：top=0%; center=50%; bottom=100%;

> ##### ② 景深 perspective 
>
> 景深就是我们肉眼距离显示器的这段距离，景深越大，元素离我们就越远，效果就不好
>
> 通过 perspective 属性来激活一个 3D 空间，属性值就是景深的大小，一定要避免**景深叠加**问题
>
> 景深的原理:
>
> - 景深越大，灭点越远，元素变形更小
> - 景深越小，灭点越近，元素变形更
>
> `perspective-origin:left,top;` 景深基点 控制视角的位置， 默认：50% 50%。
>
> `transform-style: preserve-3d;`营造有层级的 3D 舞台。不可继承属性，作用于子元素
>
> `backface-visibility: hidden;`用来设置是否显示元素的背面，默认是显示的

> ##### ③ 浏览器兼容
>
> 目前transform只支持IE10+，对IE9不支持，要兼容浏览器需要添加前缀
>
> ```javascript
> {
> 	transform:translate(10,10) // W3c标准
> 	-webkit-transform:translate(10,10) // Safari Chrome
> 	-moz-transform:translate(10,10) // firefox
> 	-ms-transform:translate(10,10) // IE9
> 	-o-transform:translate(10,10) // opera
> }
> ```