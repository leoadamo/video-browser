<template>
  <ul>
    <li v-for="item in data" :key="item.id">
      {{ item.title }}
    </li>
  </ul>
</template>

<script>
export default {
  name: 'VideoList',
  props: {
    data: {
      type: Array,
      default: null
    }
  }
};
</script>

<style></style>
