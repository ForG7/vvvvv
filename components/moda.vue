<template>
    <div id="div">
      <h3 @click="send"> 这里是兄弟组件 AAA, 点击这里可以发送数据到另一个兄弟组件中 </h3>
      <slot name="once"></slot>
      <slot name="two"></slot>
    </div>
</template>

<script>
  export default {
    name: "moda",
    data(){
      return {
        msg: '这里是兄弟组件AAA的数据'
      }
    },
    methods:{
      send(){
        this.$root.$emit('bro', this.msg);
      }
    }
  }
</script>

<style scoped>

</style>
