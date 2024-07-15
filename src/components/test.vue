<template>
  <button type="button" @click="showAlert">버튼1</button>
</template>

<script>
export default {
  name: 'test',
  props: {
    showAlert: undefined,
  }
}
</script>

<style>
</style>