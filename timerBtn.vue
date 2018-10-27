/**
 * @file timerBtn.vue
 * @author liumapp
 * @email liumapp.com@gmail.com
 * @homepage http://www.liumapp.com
 * @date 2018/10/27
 */
<template>
  <button v-on:click="start" :disabled="time > 0 || btnDisable">{{ text }}</button>
</template>
<script>
export default {
  name: 'timerBtn',
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
      default: '获取验证码'
    },
    textAfterClick: {
      type: String,
      default: 's 后重新获取'
    }
  },
  data () {
    return {
      time: 0,
      btnDisable: false,
      beforeClickText: '',
      afterClickText: ''
    }
  },
  mounted () {
    this.init();
  },
  methods: {
    init () {
      this.btnDisable = this.disabled;
      this.beforeClickText = this.textBeforeClick;
      this.afterClickText = this.textAfterClick;
    },
    end () {
      this.$emit('end');
    },
    start () {
      this.$emit('start');
      this.time = this.second;
      this.timer();
    },
    stop () {
      this.time = 0;
      this.btnDisable = false;
    },
    setDisabled (val) {
      this.btnDisable = val;
    },
    timer () {
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
    text: function () {
      return this.time > 0 ? this.time + this.afterClickText : this.beforeClickText;
    }
  }
}
</script>
