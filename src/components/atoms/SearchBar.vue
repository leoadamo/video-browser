<template>
  <div class="app-searchBar">
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
