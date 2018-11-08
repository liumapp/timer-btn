/**
 * @file timerBtn.vu
 * @author liumapp
 * @email liumapp.com@gmail.com
 * @homepage http://www.liumapp.com
 * @date 2018/10/27
 */
<template>
  <div>
    <a  v-if="type == 'link'" :style="btnStyle" v-on:click="beforeStart" :disabled="time > 0 || btnDisable">{{ text }}</a>
    <Button v-else v-on:click="beforeStart"  :style="btnStyle" :disabled="time > 0 || btnDisable">{{ text }}</Button>
  </div>
</template>
<script>
export default {
  name: "timerBtn",
  props: {
    second: {
      type: Number,
      default: 60
    },
    disabled: {
      type: Boolean,
      default: false
    },
    textBeforeClick: {
      type: String,
      default: "获取验证码"
    },
    textAfterClick: {
      type: String,
      default: "s 后重新获取"
    },
    type: {
      type: String,
      default: "link" //选择按钮的类型，link为a标签按钮，button为button类型按钮
    },
    btnStyle:{   //内部按钮的样式，可以传
      type: Object
    }
  },
  data() {
    return {
      time: 0,
      btnDisable: false,
      beforeClickText: "",
      afterClickText: ""
    };
  },
  mounted() {
    this.init();
  },
  methods: {
    init() {
      this.btnDisable = this.disabled;
      this.beforeClickText = this.textBeforeClick;
      this.afterClickText = this.textAfterClick;
    },
    end() {
      this.$emit("end");
    },
    beforeStart() {
      this.$emit("beforeStart");
    },
    start() {
      this.time = this.second;
      this.timer();
    },
    stop() {
      this.time = 0;
      this.btnDisable = false;
    },
    setDisabled(val) {
      this.btnDisable = val;
    },
    timer() {
      if (this.time > 0) {
        this.time--;
        setTimeout(this.timer, 1000);
      } else {
        this.btnDisable = false;
        this.end();
      }
    }
  },
  computed: {
    text: function() {
      return this.time > 0
        ? this.time + this.afterClickText
        : this.beforeClickText;
    }
  }
};
</script>

<style lang="less" scoped>

</style>

