

# 基础篇：弹性盒子（Flex）布局



## 背景

布局的传统解决方案，基于盒状模型，依赖display属性+postions+flat属性。它对于那些特殊布局非常不方便。比如垂直居中不太容易时间。2009，W3C提出了一种新的方案--flex布局，可以简便、完整、响应式地实现各种网页布局。目前，它已经得到了所有浏览器的支持，这意味着，现在就能很安全的使用这项功能

```
注意，设为 Flex 布局以后，子元素的`float`、`clear`和`vertical-align`属性将失效。
```

**浏览器支持如下：**

![image-20210708140713971](https://yinli-work.oss-cn-beijing.aliyuncs.com/github/image-20210708140713971.png)

基本概念

![image-20210708144946371](C:/Users/cheny/AppData/Roaming/Typora/typora-user-images/image-20210708144946371.png)

## 关键属性

```
display:flex //开启弹性盒子
```

- ### flex-direction

  设置主轴方向

  ```css
  .box {
    flex-direction: row | row-reverse | column | column-reverse;
  }
  ```

![image-20210708145051705](https://yinli-work.oss-cn-beijing.aliyuncs.com/github/image-20210708145051705.png)

​	它可能有4个值。

> - `row`（默认值）：主轴为水平方向，起点在左端。
> - `row-reverse`：主轴为水平方向，起点在右端。
> - `column`：主轴为垂直方向，起点在上沿。
> - `column-reverse`：主轴为垂直方向，起点在下沿。

- ### flex-wrap

  设置超出部分是否换行

  ### ![image-20210708145549991](https://yinli-work.oss-cn-beijing.aliyuncs.com/github/image-20210708145549991.png)

  ```css
  .box{
    flex-wrap: nowrap | wrap | wrap-reverse;
  }
  ```

  1. ​	nowrap （默认）：不换行。自动挤满整行

     ![image-20210708150116802](https://yinli-work.oss-cn-beijing.aliyuncs.com/github/image-20210708150116802.png)

  2. ​	wrap ：换行，从上往下排列，子元素超出部分自动换至下一行

     ![image-20210708150126828](https://yinli-work.oss-cn-beijing.aliyuncs.com/github/image-20210708150126828.png)

  3. ​	wrap-reverse：换行，但从下往上排列

     ![image-20210708150138767](https://yinli-work.oss-cn-beijing.aliyuncs.com/github/image-20210708150138767.png)

     

- ### flex-flow

  flex-direction与flex-wrap集合属性

  ```css
  .box {
    flex-flow: <flex-direction> || <flex-wrap>;
  }
  ```

  

- ### justily-content

  定义子元素在主轴分布位置

  ```css
  .box {
    justify-content: flex-start | flex-end | center | space-between | space-around;
  }
  ```

  ![image-20210708150844392](https://yinli-work.oss-cn-beijing.aliyuncs.com/github/image-20210708150844392.png)

  它有5个值

  - `flex-start`（默认值）：左对齐
  - `flex-end`：右对齐
  - `center`： 居中
  - `space-between`：两端对齐，项目之间的间隔都相等。
  - `space-around`：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍。

- ### align-content

  align-content 属性定义了多跟轴线（多行）的对齐方式。如果项目只有一根轴线，该属性不期作用

  ```css
  .box {
    align-content: flex-start | flex-end | center | space-between | space-around | stretch;
  }
  ```

  ![image-20210708163346117](https://yinli-work.oss-cn-beijing.aliyuncs.com/github/image-20210708163346117.png)

  该属性可能取6个值。

  - `flex-start`：与交叉轴的起点对齐。
  - `flex-end`：与交叉轴的终点对齐。
  - `center`：与交叉轴的中点对齐。
  - `space-between`：与交叉轴两端对齐，轴线之间的间隔平均分布。
  - `space-around`：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。
  - `stretch`（默认值）：轴线占满整个交叉轴。

   

- ### align-items

  交叉轴对齐方式，属性同justily_content一致

  ```
  .box {
    align-items: flex-start | flex-end | center | space-between | space-around;
  }
  ```

  ![image-20210708163631205](https://yinli-work.oss-cn-beijing.aliyuncs.com/github/image-20210708163631205.png)

它可能取5个值。具体的对齐方式与交叉轴的方向有关，下面假设交叉轴从上到下。

- `flex-start`：交叉轴的起点对齐。
- `flex-end`：交叉轴的终点对齐。
- `center`：交叉轴的中点对齐。
- `baseline`: 项目的第一行文字的基线对齐。
- `stretch`（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。



### 子元素属性

### order

定义项目排序

```css
.item {
  order: <integer>;
}
```



默认排序

![image-20210708165747675](https://yinli-work.oss-cn-beijing.aliyuncs.com/github/image-20210708165747675.png)

改写后排序

```
<style>
        .box{
            background-color: seagreen;
            margin: auto;
            display: flex;
            align-items: center;
            width: 600px;
            height: 600px;
        }
        .item{
            color: #fff;
            background-color: red;
            font-size: 5rem;
            border: 1px solid black;
            width: 100px;
        }
        .item:nth-child(2){
            /* 修改子元素排序 */
            order: -1; 
        }

    </style>
    
    <div class="box">
        <div class="item">1</div>
        <div class="item">2</div>
        <div class="item">3</div>
    </div>
```

![image-20210708165939472](https://yinli-work.oss-cn-beijing.aliyuncs.com/github/image-20210708165939472.png)

### align-self

单独设置子元素交叉轴对齐方式，参数同align-items;

```css
.item:nth-child(2){
        /* 设置向上对齐 */
        /* align-self: auto | flex-start | flex-end | center | baseline | stretch;*/
   	align-self:flex-start
 }
```

![image-20210708170850397](https://yinli-work.oss-cn-beijing.aliyuncs.com/github/image-20210708170850397.png)

## flex

设置子元素所占比例，它是三个属性的合集

- flex-grow：设置子元素放大比例: 默认值：0

  代码：

  ```css
  .item:nth-child(3){
      /*类似于分蛋糕，设置第三个子元素沾满剩余空间*/
     	flex-grow:1;
   }
  ```

  展示效果：

  ![image-20210708171732468](https://yinli-work.oss-cn-beijing.aliyuncs.com/github/image-20210708171732468.png)

  

- flex-shrink：设置子元素缩小比例，默认值：1

  代码：

  ![image-20210708172351785](https://yinli-work.oss-cn-beijing.aliyuncs.com/github/image-20210708172351785.png)



​	效果：

![image-20210708172410805](https://yinli-work.oss-cn-beijing.aliyuncs.com/github/image-20210708172410805.png)

- flex-basis：设置子元素宽，默认值：auto。当至0时，子元素宽度随内容而变化；**特别注意：basis会覆盖width属性，使其失效**

  ```css
  .item:nth-child(3){
    flex-basis: <length> |0|auto; /* default auto */
  }
  ```

![image-20210708173204970](https://yinli-work.oss-cn-beijing.aliyuncs.com/github/image-20210708173204970.png)

## 敲重点

**flex简写值（面试中经常问到）**

```css
.item {flex: none;} 
/*相同设置*/
.item {flex-grow: 0; flex-shrink: 0;flex-basis: auto; }
```

```css
.item {flex: 0;} 
/*相同设置*/
.item {flex-grow: 0; flex-shrink: 0;flex-basis: 0; }
```

```css
.item {flex: 1;} 
/*相同设置*/
.item {flex-grow: 1; flex-shrink: 0;flex-basis: 0%; }
```

```css
.item {flex: auto;} 
/*相同设置*/
.item {flex-grow: 1; flex-shrink: 1;flex-basis: auto; }
```

```css
.item-1 {flex: 0%;} 
.item-1 {    flex-grow: 1;    flex-shrink: 1;    flex-basis: 0%; } 
/* 当 flex 取值为一个长度或百分比，则视为 flex-basis 值，flex-grow 取 1，flex-shrink 取 1，有如下等同情况（注意 0% 是一个百分比而不是一个非负数字）*/
.item-2 {flex: 24px;} 
.item-2 {    flex-grow: 1;    flex-shrink: 1;    flex-basis: 24px; }
```

```css
/*当设置两个值的时候结果如下*/
.item {flex: 2 3;} 
.item {    flex-grow: 2;    flex-shrink: 3;    flex-basis: 0%; }
```

```css
/*当设置两个值的时候，并且有设置长度单位时，效果如下*/
.item {flex: 2333 3222px;} 
.item {    flex-grow: 2333;    flex-shrink: 1;    flex-basis: 3222px; }
```



参考文章

https://www.ruanyifeng.com/blog/2015/07/flex-grammar.html

https://www.cnblogs.com/wenqiangit/p/11664524.html
