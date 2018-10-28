<h1 align="center">timer-btn</h1>

> 限制点击时间的按钮，可用于短信验证码等场景，相关样式持续更新中。

文档正在编写中...

### 特点

* 没有依赖包
* 可以设定等待时间
* 可以手动打断
* 可以手动触发

### 实例

---

## 安装 及 使用

```bash
$ npm install --save lm-sign-area
```


注册组件

```js
import Vue from 'vue'
import timerBtn from 'timer-btn'

Vue.component('timerBtn', timerBtn)
```

使用组件

<template>
    <timer-btn class="ivu-btn ivu-btn-default" v-on:start="sendCode"
         v-on:end="endTime" :second="5"></timer-btn>
</template>

<script>
export default {
  sendCode () {
    console.log('您点击了按钮，按钮将会在您指定的时间之内不可用，并显示倒计时');
  },
  //验证码按钮的一分钟等待时间结束
  endTime () {
    console.log('end');
  }
}
</script>
