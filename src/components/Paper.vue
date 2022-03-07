<template>
  <div
    class="w-32 h-32 bg-white rounded-full"
    :class="[{ paper: !showWin, 'win-paper': showWin }, marginClasses]"
  >
    <img src="../assets/icon-paper.svg" class="pl-10 pt-8" />
  </div>
</template>

<script>
export default {
  props: {
    marginClasses: {
      type: String,
      default: "",
    },
    showWin: {
      type: Boolean,
      default: false,
    },
  },
};
</script>

<style scoped>
.paper {
  box-shadow: 0 0 0 19px hsl(230, 89%, 62%);
}

.win-paper {
  box-shadow: inset 0 0 0 19px hsl(230, 89%, 62%),
    0 0 0 24px hsla(214, 47%, 23%, 0.2), 0 0 0 48px hsla(214, 47%, 23%, 0.2),
    0 0 0 72px hsla(214, 47%, 23%, 0.2);
}
</style>
