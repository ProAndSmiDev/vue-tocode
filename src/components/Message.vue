<template>
  <div class="message">
    <p>{{ message }}</p>
  </div>
</template>

<script>
export default {
  name: "Message",
  props: {
    message: {
      type: String,
      required: true,
      default: '',
    },
  },
};
</script>

<style lang="scss" scoped>
  .message {
    color: red;
    text-align: center;
  }
</style>
