<template>
  <div
    class="w-32 h-32 rounded-full"
    style="background-color: rgba(31, 40, 69, 255)"
    :class="marginClasses"
  ></div>
</template>

<script>
export default {
  props: {
    marginClasses: {
      type: String,
      default: "",
    },
  },
};
</script>

<style scoped></style>
