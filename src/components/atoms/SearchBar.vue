<template>
  <div>
    <input type="text" @input="onInput" />
  </div>
</template>

<script>
export default {
  name: 'SearchBar',
  methods: {
    onInput({ target }) {
      this.$emit('termChange', target.value);
    }
  }
};
</script>

<style lang="scss">
input {
  border: 0.1px solid #1c1c1c;
}
</style>
