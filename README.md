# 动画容器-animatebox

基于animate.css的动画容器


## 示例

```html
<animate-box
    @animationStart="animationStart"
    @animationIteration="animationIteration"
    @animationEnd="animationEnd"
    animateClassName="fadeInLeft"

    >任意内容</animate-box
>
 ```



## 参数

### animateClassName[String]

动画类名，可以是animate.css也可以自定义类名

### delay[Number]

动画延迟，默认 0

### duration[Number]

动画持续时间



## 事件

### animationStart

动画开始

### animationIteration

动画重复运动

### animationEnd

动画结束
