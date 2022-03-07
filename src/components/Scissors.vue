<template>
  <div
    class="w-32 h-32 bg-white rounded-full"
    :class="[{ scissors: !showWin, 'win-scissors': showWin }, marginClasses]"
  >
    <img src="../assets/icon-scissors.svg" class="pl-10 pt-8" />
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
.scissors {
  box-shadow: 0 0 0 19px hsl(39, 89%, 49%);
}
.win-scissors {
  box-shadow: inset 0 0 0 19px hsl(39, 89%, 49%),
    0 0 0 24px hsla(214, 47%, 23%, 0.2), 0 0 0 48px hsla(214, 47%, 23%, 0.2),
    0 0 0 72px hsla(214, 47%, 23%, 0.2);
}
</style>
