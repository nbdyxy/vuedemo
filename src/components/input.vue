<template>
  <input @input="updateValue" :value="value">
</template>

<script>
export default {
  props: ['value'],
  methods: {
    updateValue (event) {
      this.$emit('input', event.target.value);
    }
  }
}
</script>
