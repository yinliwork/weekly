# 探究CSS3中的transition和transfrom属性与区别

经常有小伙伴门把 transition,transfrom和translate这者搞混，傻傻分不清，因此有了本期思路来源。

## 单词解释：

- transform 是**转换**，指的是改变所在元素的外观，它有很多种手段（转换函数）来改变外观，例如**位移、缩放、旋转**等，而其中的位移的函数名就叫做**translate**,所以说，translate是transform的一部分
- transition 是过渡，只的事某个CSS属性值如何平滑的进行改变，就是平常说的动效。而transform是没有动画效果，你改变了它的值，元素的样子就唰的改变了，可以理解为动画**animation**初阶
- translate 是transfrom的一部分，函数类型使用。用于旋转角度

## transition过渡

### 基本用法

好，接下来了解下transition的基本用法:

transition [属性名] [持续时间] [曲线速度] [延迟时间]

我们可以很方便的勇者过渡来给某一个属性加上好看的特效。例如，高度属性的值改变时，延迟0.5秒以后以ease曲线进行过渡，持续2秒



我们可以很




## 参考
 https://www.jianshu.com/p/80f6051389bd

