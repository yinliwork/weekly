# 那些年面试频繁被问到的animations动画详解

## 背景

**CSS animations** 使得可以将从一个CSS样式配置转换到另一个CSS样式配置。动画包括两个部分:描述动画的样式规则和用于指定动画开始、结束以及中间点样式的关键帧。

相较于传统的脚本实现动画技术，使用CSS动画有三个主要优点：

1. 能够非常容易地创建简单动画，你甚至不需要了解JavaScript就能创建动画。

2. 动画运行效果良好，甚至在低性能的系统上。渲染引擎会使用跳帧或者其他技术以保证动画表现尽可能的流畅。而使用JavaScript实现的动画通常表现不佳（除非经过很好的设计）。

3. 让浏览器控制动画序列，允许浏览器优化性能和效果，如降低位于隐藏选项卡中的动画更新频率。

   

## 常用属性

animation-name:设置动画关键帧名称，名称为@keyframes name。可设置多参数

animation-delay: 设置动画延迟执行时间，可设置多参数，与name数量对应。如不对应name则取最大值生效

animation-direction:设置动画在每次运行完成后是反向运行还是重新回到开始位置重复执行

animation-duraction:设置动画执行时间，可设置多参数，与name数量对应。如不对应name则取最大值生效

animation-iteration-count:设置动画重复次数，可以指定infinite无限次重复动画

animation-titming-function:设置动画速度，既通过建立加速度曲线，设置动画在关键帧之间是如何变化。

animation-fill-mode:指定动画执行前后如何为目标元素应用样式。



## 使用keyframes定义动画关键帧

一旦完成动画的时间设置， 接下来就需要定义动画的表现。通过使用[`@keyframes`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@keyframes)建立两个或两个以上关键帧来实现。每一个关键帧都描述了动画元素在给定的时间点上应该如何渲染。

因为动画的时间设置是通过CSS样式定义的，关键帧使用[`percentage`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/percentage)来指定动画发生的时间点。`0%`表示动画的第一时刻，`100%`表示动画的最终时刻。因为这两个时间点十分重要，所以还有特殊的别名：`from`和`to`。这两个都是可选的，若`from/0%`或`to/100%`未指定，则浏览器使用计算值开始或结束动画。

通常情况下，0%不用设置，默认初始化状态。

示例1：

```css
element {
  animation-duration: 3s;
  animation-name: toRight;
}

@keyframes toRight {
  from {
    margin-left: 10pxx;
  }
  to {
    margin-left: 100px;
  }
}
```

示例2：

```css
element {
  animation-duration: 3s;
  animation-name: toRight,toBottom;
}

@keyframes slidein {
  from {
    margin-left: 10pxx;
  }
  to {
    margin-left: 100px;
  }
}
/*与上面国画效果相同*/
@keyframes toBottom{
  0% {
    margin-top: 10px;
  }
  100% {
    margin-top: 100px;
  }
}
```

![动画2](https://yinli-work.oss-cn-beijing.aliyuncs.com/github/动画2.gif)



## 属性值

### animation-delay:属性定义动画于何时开始，即从动画应用在元素上到动画开始的这段时间的长度。

```css
animation-delay:1s; /*默认为0*/
```

![动画3](https://yinli-work.oss-cn-beijing.aliyuncs.com/github/动画3.gif)

注意：当animation-delay:1s;

### animation-iteration-count: 定义动画在结束前运行的次数 可以是1次 无限循环

animation-iteration-count: 0;

animation-iteration-count: 2;

animation-iteration-count: 1.5;

**语法**

```
/* 值为关键字 */
animation-iteration-count: infinite;

/* 值为数字 */
animation-iteration-count: 3;
animation-iteration-count: 2.4;

/* 指定多个值 */
animation-iteration-count: 2, 0, infinite;
```

### animation-direction：属性指示动画是否反向播放，它通常在简写属性中设定

语法

single-animation-direction= normal [|](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Value_definition_syntax#single_bar) reverse [|](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Value_definition_syntax#single_bar) alternate [|](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Value_definition_syntax#single_bar) alternate-reverse

```css
animation-direction: normal
animation-direction: reverse
animation-direction: alternate
animation-direction: alternate-reverse
animation-direction: normal, reverse
animation-direction: alternate, reverse, normal
```

### animation-duration属性指定一个动画周期的时长。

语法

```css
animation-duration: 6s
animation-duration: 120ms
animation-duration: 1s, 15s
animation-duration: 10s, 30s, 230ms
```

### animation-play-state 属性定义一个动画是否运行或者暂停。可以通过查询它来确定动画是否正在运行。另外，它的值可以被设置为暂停和恢复的动画的重放。

```css
/* Single animation */
animation-play-state: running; /*初始值*/
animation-play-state: paused;

/* Multiple animations */
animation-play-state: paused, running, running;

/* Global values */
animation-play-state: inherit;
animation-play-state: initial;
animation-play-state: unset;
```

### [值](https://developer.mozilla.org/zh-CN/docs/Web/CSS/animation-play-state#值)

- `running`

  当前动画正在运行。

- `paused`

  当前动画已被停止。

### animation-timing-function:`属性定义CSS动画在每一动画周期中执行的节奏。`可能值为一或多个

语法

```css
/* Keyword values */
animation-timing-function: ease;
animation-timing-function: ease-in;
animation-timing-function: ease-out;
animation-timing-function: ease-in-out;
animation-timing-function: linear;
animation-timing-function: step-start;
animation-timing-function: step-end;

/* Function values */
animation-timing-function: cubic-bezier(0.1, 0.7, 1.0, 0.1);
animation-timing-function: steps(4, end);
animation-timing-function: frames(10);

/* Multiple animations */
animation-timing-function: ease, step-start, cubic-bezier(0.1, 0.7, 1.0, 0.1);

/* Global values */
animation-timing-function: inherit;
animation-timing-function: initial;
animation-timing-function: unset;
```



### animation-fill-mode:设置CSS动画在执行之前和之后如何将样式应用于其目标。

```css
/* Single animation */
animation-fill-mode: none;
animation-fill-mode: forwards;
animation-fill-mode: backwards;
animation-fill-mode: both;

/* Multiple animations */
animation-fill-mode: none, backwards;
animation-fill-mode: both, forwards, none;
```

**值**

**none**:当动画未执行时，动画将不会将任何样式应用于目标，而是已经赋予给该元素的 CSS 规则来显示该元素。这是默认值。

**forwards**

目标将保留由执行期间遇到的最后一个[关键帧](https://developer.mozilla.org/en-US/docs/Web/CSS/@keyframes)计算值。 最后一个关键帧取决于[`animation-direction`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/animation-direction)和[`animation-iteration-count`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/animation-iteration-count)的值：

| `animation-direction` | `animation-iteration-count` | last keyframe encountered |
| :-------------------- | :-------------------------- | :------------------------ |
| `normal`              | even or odd                 | `100%` or `to`            |
| `reverse`             | even or odd                 | `0%` or `from`            |
| `alternate`           | even                        | `0%` or `from`            |
| `alternate`           | odd                         | `100%` or `to`            |
| `alternate-reverse`   | even                        | `100%` or `to`            |
| `alternate-reverse`   | odd                         | `0%` or `from`            |

**backwards**

动画将在应用于目标时立即应用第一个关键帧中定义的值，并在[`animation-delay`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/animation-delay)期间保留此值。 第一个关键帧取决于[`animation-direction`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/animation-direction)的值：

| `animation-direction`            | first relevant keyframe |
| :------------------------------- | :---------------------- |
| `normal` or `alternate`          | `0%` or `from`          |
| `reverse` or `alternate-reverse` | `100%` or `to`          |





## 小足球

![动画5](https://yinli-work.oss-cn-beijing.aliyuncs.com/github/动画5.gif)

代码地址：https://codepen.io/chenyuzhi/pen/MWmbYRG



## 爱之心

![动画6](https://yinli-work.oss-cn-beijing.aliyuncs.com/github/动画6.gif)

https://codepen.io/chenyuzhi/pen/ExmNyvN
