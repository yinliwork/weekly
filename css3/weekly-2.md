# CSS3面试中的transition和transfrom属性与区别

经常有小伙伴门把 transition,transfrom和translate这者搞混，傻傻分不清，因此有了本期思路来源。

## 单词解释：

- transform 是**转换**，指的是改变所在元素的外观，它有很多种手段（转换函数）来改变外观，例如**位移、缩放、旋转、倾斜**等，而其中的位移的函数名就叫做**translate**,所以说，translate是transform的一部分
- transition 是过渡，只的事某个CSS属性值如何平滑的进行改变，就是平常说的动效。而transform是没有动画效果，你改变了它的值，元素的样子就唰的改变了，可以理解为动画**animation**初阶
- translate 是transfrom的一部分，函数类型使用。用于旋转角度

## transition过渡

![image-20210707193039208](https://yinli-work.oss-cn-beijing.aliyuncs.com/github/image-20210707193039208.png)

### 基本用法

好，接下来了解下transition的基本用法:

transition [属性名] [持续时间] [曲线速度] [延迟时间]

我们可以很方便的勇者过渡来给某一个属性加上好看的特效。例如，高度属性的值改变时，延迟0.5秒以后以ease曲线进行过渡，持续2秒

### 基本属性

- transition-property：

​	指定哪个或哪些CSS属性用于过渡，只有指定的属性才会在过渡中发生动画，其他属性任如通常那样瞬间变化。

​	例如：

```
transition-property：width
```

- transition-duration

​	指定过渡的时长，或者为所有属性指定一个值，或者指定多个值，为每个属性指定不同的时长。

​	例如：

```
transition-duration:0.5s transition-duration 1s
```

- transition-timing-function



​	指定一个函数，定义属性值怎么变化。缓动函数Timing-functions定义如何计算。多数timing_functions由四点定义一个bezier曲线（相关函数cubic-bezier()）。也可以从[Easing Functions Cheat Sheet](https://easings.net/)选择缓动效果。bezier官网https://cubic-bezier.com/

![image-20210707111021929](https://yinli-work.oss-cn-beijing.aliyuncs.com/github/image-20210707111021929.png)

例如（常用属性）：

```
transition-timing-function: ease    //执行时间：缓慢-快-缓慢
transition-timing-function: ease-in //执行时间：缓慢-正常
transition-timing-function: ease-in-out //执行时间：正常-缓慢
transition-timing-function: linear   //线性输出：匀速执行
transition-timing-function: cubic-bezier(0.4,0.3,1,0.5) //曲线时间执行
```

常用参数：

![image-20210707112422149](https://yinli-work.oss-cn-beijing.aliyuncs.com/github/image-20210707112422149.png)

- transition-delay

指定延迟，既属性开始变化时与过度开始发生时之间的时长

例如：

```
transition-delay:0.5s 
```

- 简写语法

div {
    transition: <property> <duration> <timing-function> <delay>;
}

例如：

```
transition:width 1s ease
```



### 使用场景

如积分抽奖大转盘，鼠标悬停渐变，菜单下路展示。通过transition过渡可有效缓解组件闪现情况



## transfroms变形

通过改变坐标空间，CSS transforms可以在不影响正常文档流的情况下改变作用内容的位置。通过一系列CSS属性实现，通过使用这些属性，可以对HTML元素进行限行访射变形。也可以进行的变形包括 旋转，倾斜，缩放及位移，这些变形同时适用于平面(2d)与三维空间(3d)

```
只有使用盒模型来定位的元素可以被变换transformed。根据一般经验，拥有display:block的元素是由盒模型定位的
```

CSS transforms属性

有两个主要的属性被用来定义CSS tranforms:transform 和transform-origin

transforms-origin

​	指定原点位置，默认值为元素的中心，可以被移动。很多变形需要用到这个属性，比如旋转，缩放和倾斜。他们都需要一个指定的点作为参数

​	例如：

```
transforms-orgin：left top
transforms-orgin：center
```



transforms

​	指定作用在元素上的变形，取值为空格分隔的一系列变形的列表，他们会像被组合操作请求一样被分别执行。

参数

- 旋转：rotate(90deg)
- 倾斜:skewx(10deg) 或skew(10deg，10deg) 
- 位移:translatex(150px)或translate(150px,150px)
- 缩放(比例)：scale（1.2）

例如

```
transform: rotate(90deg) skewx(10deg) translatex(150px) scale(1.2);
```

## 适用于三维的属性

在三维空间使用CSS变形会稍微复杂一点。你必须先设置一个透视点(perspective)以便配置3D空间，再去定义2D元素在空间中的行为。

例如

```
.pers250 {
  perspective: 250px;
}
```

效果：

![image-20210707115026822](https://yinli-work.oss-cn-beijing.aliyuncs.com/github/image-20210707115026822.png)






## 参考
 https://www.jianshu.com/p/80f6051389bd

https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions

https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Transforms/Using_CSS_transforms
