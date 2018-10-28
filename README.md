<h1 align="center">timer-btn</h1>

> 限制点击时间的按钮，可用于短信验证码等场景，相关样式持续更新中。

### 特点

* 没有依赖包（但仅支持Vue2版本以上）
* 可以设定等待时间
* 可以手动打断
* 可以手动触发

### 实例

---

## 安装 及 使用

```bash
$ npm install --save timer-btn
```


注册组件

```js
import Vue from 'vue'
import timerBtn from 'timer-btn'

Vue.component('timerBtn', timerBtn)
```

使用组件

```
<template>
    //按钮的样式根据您所选用的ui框架选择class
    <timer-btn class="ivu-btn ivu-btn-default" v-on:start="start"
                               v-on:end="end" second="10" textBeforeClick="发送验证码" textAfterClick="秒后重新获取"></timer-btn>
</template>

<script>
export default {
  start () {
    console.log('您点击了按钮，按钮将会在您指定的时间之内不可用，并显示倒计时');
  },
  //验证码按钮的等待时间结束
  end () {
    console.log('end');
  }
}
</script>
```

### 参数

#### second

类型: `Number`
必要性: `false`
默认值: 60

定义按钮点击后，所需要等待的时间，单位秒

#### disabled

类型: `Boolean`
必要性: `false`
默认值: `false`

按钮点击后，处于disabled状态，此时按钮不可点击

#### textBeforeClick

类型: `String`
必要性: `false`
默认值: `获取验证码`

按钮点击之前显示的文本

#### textAfterClick

类型: `String`
必要性: `false`
默认值: `s 后重新获取`

按钮点击之后显示的文本，second的倒计时会在文本最前面显示，所以一般会加一个"秒"或者"s"

## 后续计划

* 添加更cool的倒计时样式

* 添加更完善的响应事件



