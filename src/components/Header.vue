<template>
  <div class="header min-h-32 md:w-1/2 w-full">
    <div class="flex flex-row w-full h-full justify-between flex-wrap">
      <div class="float-left p-6 md:h-36 h-28 md:w-48 w-36">
        <img src="../assets/logo.svg" class="w-full h-full" />
      </div>

      <div
        class="w-32 bg-white m-4 rounded-md flex flex-row items-center justify-center"
      >
        <div class="flex flex-col items-center">
          <p class="score-text font-semibold text-sm">SCORE</p>
          <p class="dark-text font-bold text-5xl">{{ score }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    score: {
      type: Number,
      default: 0,
    },
  },
};
</script>

<style>
.header {
  border-style: solid;
  border-color: hsl(217, 16%, 45%);
  border-width: 1.5px;
  border-radius: 7px;
}

.score-text {
  color: hsl(229, 64%, 46%);
}

.dark-text {
  color: hsl(229, 25%, 31%);
}
</style>
