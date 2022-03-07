<template>
  <div
    class="w-32 h-32 bg-white rounded-full"
    :class="[{ rock: !showWin, 'win-rock': showWin }, marginClasses]"
  >
    <img src="../assets/icon-rock.svg" class="pl-10 pt-10" />
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
.rock {
  box-shadow: 0 0 0 19px hsl(349, 71%, 52%);
}
.win-rock {
  box-shadow: inset 0 0 0 19px hsl(349, 71%, 52%),
    0 0 0 24px hsla(214, 47%, 23%, 0.2), 0 0 0 48px hsla(214, 47%, 23%, 0.2),
    0 0 0 72px hsla(214, 47%, 23%, 0.2);
}
</style>
