<template>
  <div class="container">
    <div class="header">
      <slot name="header"></slot>
    </div>
    <div class="main">
      <slot></slot>
    </div>
    <div class="footer">
      <slot name="footer"></slot>
    </div>
  </div>
</template>

<script>
export default {
  mounted () {
    var footer = this.$slots.footer;
    console.log(footer);
    console.log(footer[0].elm.innerHTML);
  }
}
</script>

<style lang="css">
</style>
