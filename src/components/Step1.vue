<template>
  <div class="h-full">
    <div class="flex flex-row justify-between">
      <Paper
        marginClasses="-mt-8 -ml-8"
        class="cursor-pointer"
        @click="selectedObject('paper')"
      />
      <Scissors
        marginClasses="-mr-8 -mt-8"
        class="cursor-pointer"
        @click="selectedObject('scissors')"
      />
    </div>
    <div class="flex flex-col-reverse items-center h-full -mt-20">
      <Rock
        marginClasses="ml-4 mt-1"
        class="cursor-pointer"
        @click="selectedObject('rock')"
      />
    </div>
  </div>
</template>

<script>
import Paper from "./Paper.vue";
import Rock from "./Rock.vue";
import Scissors from "./Scissors.vue";
export default {
  components: {
    Paper,
    Rock,
    Scissors,
  },
  methods: {
    selectedObject(object) {
      console.log("object", object);
      this.$emit("selected", object);
    },
  },
};
</script>
