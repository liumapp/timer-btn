<h1 align="center">timer-btn</h1>

> 限制点击时间的按钮，可用于短信验证码等场景，相关样式持续更新中。

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
import signArea from 'lm-sign-area'

Vue.component('signArea', signArea)
```

使用组件

```vue
<template>
  <div style="height: 500px; width: 500px; border: 1px solid red; position: relative;">
    <sign-area :w="200" :h="100" v-on:dragging="onDrag" v-on:resizing="onResize" :parent="true" :resizable="false">
        X: {{ x }} / Y: {{ y }} - Width: {{ width }} / Height: {{ height }}</p>
    </sign-area>
  </div>
</template>

<script>
import signArea from 'lm-sign-area'

export default {
  data: function () {
    return {
      width: 0,
      height: 0,
      x: 0,
      y: 0
    }
  },
  components: {
    signArea
  },
  methods: {
    onResize: function (x, y, width, height) {
      this.x = x
      this.y = y
      this.width = width
      this.height = height
    },
    onDrag: function (x, y) {
      this.x = x
      this.y = y
    }
  }
}
</script>
```

### 参数

#### draggable
类型: `Boolean` 或 `Number`<br>
必要性: `false`<br>
默认值: `true`

定义组件是否可以拖动.

| 参数值       | 效果         |
| ----------- |:-------------:|
|true | 组件可以在x轴,y轴方向自由拖动 |
|false | 组件无法拖动 |
|0 | 组件无法拖动 |
|1 | 组件可以在x轴,y轴方向自由拖动 |
|2 | 组件可以在x轴方向自由拖动 |
|3 | 组件可以在y轴方向自由拖动 |

```html
<sign-area :draggable="false">
```

#### resizable
类型: `Boolean` 或 `Number`<br>
必要性: `false`<br>
默认值: `true`

定义组件是否可以调整大小.

| 参数值       | 效果         |
| ----------- |:-------------:|
|true | 组件可以在x轴,y轴方向调整大小 |
|false | 组件无法拖动 |
|0 | 组件无法拖动 |
|1 | 组件可以在x轴,y轴方向调整大小 |
|2 | 组件可以在x轴方向调整大小 |
|3 | 组件可以在y轴方向调整大小 |

```html
<sign-area :resizable="false">
```

#### w
类型: `Number`<br>
必要性: `false`<br>
默认值: `200`

定义组件的初始宽度.

```html
<sign-area :w="200">
```

#### h
类型: `Number`<br>
必要性: `false`<br>
默认值: `200`

定义组件的初始高度.

```html
<sign-area :h="200">
```

#### minw
类型: `Number`<br>
必要性: `false`<br>
默认值: `50`

定义组件的最小宽度.

```html
<sign-area :minw="50">
```

#### minh
类型: `Number`<br>
必要性: `false`<br>
默认值: `50`

定义组件的最小高度.

```html
<sign-area :minh="50">
```

#### x
类型: `Number`<br>
必要性: `false`<br>
默认值: `0`

定义组件初始横轴坐标.

```html
<sign-area :x="0">
```

#### y
类型: `Number`<br>
必要性: `false`<br>
默认值: `0`

定义组件初始纵轴坐标.

```html
<sign-area :y="0">
```

#### grid
类型: `Array`<br>
必要性: `false`<br>
默认值: `[1,1]`

定义组件网格.

```html
<sign-area :grid="[1,1]">
```

#### restrain
类型: `Number`<br>
必要性: `false`<br>
默认值: `0`

约束元素宽高只能是restrain的倍数.

```html
<sign-area :restrain="100">
```

---

#### parent
类型: `Boolean`<br>
必要性: `false`<br>
默认值: `false`

限制元素只能在父元素内拖动

```html
<sign-area :parent="true">
```

---

### Events

#### activated

必要性: `false`<br>
Parameters: `-`

组件被初始化事件.

```html
<sign-area @activated="onActivated">
```

#### deactivated

必要性: `false`<br>
Parameters: `-`

组件被销毁事件.

```html
<sign-area @deactivated="onDeactivated">
```

#### resizing

必要性: `false`<br>
Parameters:
* `left` 组件 X 轴坐标
* `top` 组件 Y 轴坐标
* `width` 组件宽度
* `height` 组件高度

组件大小改变事件.

```html
<sign-area @resizing="onResizing">
```

#### resizestop

必要性: `false`<br>
Parameters:
* `left` 组件 X 轴坐标
* `top` 组件 Y 轴坐标
* `width` 组件宽度
* `height` 组件高度

组件大小改变结束事件.

```html
<sign-area @resizestop="onResizstop">
```

#### dragging

必要性: `false`<br>
Parameters:
* `left` 组件 X 轴坐标
* `top` 组件 Y 轴坐标

组件拖动事件.

```html
<sign-area @dragging="onDragging">
```

#### dragstop

必要性: `false`<br>
Parameters:
* `left` 组件 X 轴坐标
* `top` 组件 Y 轴坐标

组件拖动结束事件.

#### keydown

必要性: `false`<br>
Parameters:
* `event` 键值

按键事件.

```html
<sign-area @dragstop="onDragstop">
```

