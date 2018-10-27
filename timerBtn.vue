/**
 * @file timerBtn.vue
 * @author liumapp
 * @email liumapp.com@gmail.com
 * @homepage http://www.liumapp.com
 * @date 2018/10/27
 */
<template>
  <button v-on:click="run" :disabled="btnDisable || time > 0">{{ text }}</button>
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
    }
  },
  data () {
    return {
      time: 0,
      btnDisable: false
    }
  },
  mounted () {
    this.btnDisable = this.disabled;
  },
  methods: {
    run: function () {
      this.$emit('run');
    },
    start: function() {
      this.time = this.second;
      this.timer();
    },
    stop: function() {
      this.time = 0;
      this.btnDisable = false;
    },
    setDisabled: function(val) {
      this.btnDisable = val;
    },
    timer: function () {
      if (this.time > 0) {
        this.time--;
        setTimeout(this.timer, 1000);
      }else{
        this.btnDisable = false;
      }
    }

  },
  computed: {
    text: function () {
      return this.time > 0 ? this.time + 's 后重获取' : '获取验证码';
    }
  }
}
</script>
