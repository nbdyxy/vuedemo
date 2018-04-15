<template>
  <div>
    <v-title title="Vue组件化"></v-title>
    <v-button @click="handleClick">点击按钮</v-button>
  </div>
</template>
<script>
  import vTitle from './components/title.vue';
  import vButton from './components/button.vue';

  export default {
    components: {
      vTitle,
      vButton
    },
    methods: {
      handleClick (e) {
        console.log(e);
      }
    },
    data () {
      return {
        color: '#f60'
      }
    }
  }
</script>
<style scoped>
  div{
    color: #f60;
    font-size: 24px;
  }
</style>
