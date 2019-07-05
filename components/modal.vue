<template>
  <div id="box">
    <div class="mask">
      <h4> {{title}} </h4>
      <p> {{content}} </p>
      <p> {{text}} </p>
      <a href="javascript:;">{{cancel}}</a>
      <a href="javascript:;" @click="sendMsg">{{conFirm}}</a>
    </div>
  </div>
</template>
<script>
  export default {
    name: "modal",
    props: {
      title: {
        type: String,
        default: '提示'
      },
      content: {
        type: String,
        default: '默认提示内容'
      },
      cancel: {
        type: String,
        default: '取消'
      },
      conFirm: {
        type: String,
        default: '确定'
      }
    },
    data() {
      return {
        isTrue: true,
        text: ''
      }
    },
    methods: {
      sendMsg() {
        //发布自定义事件.
        this.$emit('send', this.isTrue);
      }
    },
    created() {
      this.$root.$on('bro', msg => {
        this.text = msg;
      })
    }
  }
</script>
<style scoped>
  .mask {
    width: 600px;
    height: 300px;
    margin: 30px auto;
    position: relative;
    border: #e3e3e3 1px solid;
  }

  .mask h4 {
    width: 100%;
    height: 50px;
    line-height: 50px;
    border-bottom: #e3e3e3 1px solid;
    text-align: center;
  }

  .mask p {
    width: 100%;
    height: 100px;
    line-height: 100px;
    text-align: center;
  }

  .mask a {
    display: block;
    position: absolute;
    width: 80px;
    height: 40px;
    bottom: 5px;
    line-height: 40px;
    text-align: center;
    background: #ececec;
    color: #000;
    text-decoration: none;
  }

  .mask a:hover {
    color: #c00;
  }

  .mask a:first-child {
    right: 100px;
  }

  .mask a:last-child {
    right: 0;
  }
</style>
