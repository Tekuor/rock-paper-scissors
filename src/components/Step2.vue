<template>
  <div class="w-full">
    <div class="flex flex-row justify-between">
      <div>
        <p class="invisible lg:visible text-white font-bold ml-7">YOU PICKED</p>
        <Paper
          marginClasses="mt-10"
          v-if="selected === 'paper'"
          :showWin="result === 'win'"
        />
        <Rock
          marginClasses="mt-10"
          v-if="selected === 'rock'"
          :showWin="result === 'win'"
        />
        <Scissors
          marginClasses="mt-10"
          v-if="selected === 'scissors'"
          :showWin="result === 'win'"
        />

        <p class="visible lg:invisible text-white font-bold mt-10 ml-1">
          YOU PICKED
        </p>
      </div>
      <div v-if="result" class="invisible lg:visible">
        <p
          v-if="result === 'win'"
          class="text-center text-white text-2xl font-bold pb-2 mt-16"
        >
          YOU WIN
        </p>
        <p
          v-else-if="result === 'lose'"
          class="text-center text-white text-2xl font-bold pb-2 mt-16"
        >
          YOU LOSE
        </p>
        <p
          v-else-if="result === 'draw'"
          class="text-center text-white text-2xl font-bold pb-2 mt-16"
        >
          DRAW
        </p>
        <button
          @click="playAgain"
          class="bg-white rounded-md px-6 py-1 dark-text"
        >
          PLAY AGAIN
        </button>
      </div>
      <div>
        <p class="invisible lg:visible text-white font-bold">
          THE HOUSE PICKED
        </p>
        <NotSelected marginClasses="mt-10" v-if="!house" />
        <Paper
          marginClasses="mt-10"
          v-if="house === 'paper'"
          :showWin="result === 'lose'"
        />
        <Rock
          marginClasses="mt-10"
          v-if="house === 'rock'"
          :showWin="result === 'lose'"
        />
        <Scissors
          marginClasses="mt-10"
          v-if="house === 'scissors'"
          :showWin="result === 'lose'"
        />

        <p class="visible lg:invisible text-white font-bold mt-10">
          THE HOUSE PICKED
        </p>
      </div>
    </div>

    <div v-if="result" class="visible lg:invisible flex flex-col items-center">
      <p
        v-if="result === 'win'"
        class="text-center text-white text-2xl font-bold pb-2 mt-16"
      >
        YOU WIN
      </p>
      <p
        v-else-if="result === 'lose'"
        class="text-center text-white text-2xl font-bold pb-2 mt-16"
      >
        YOU LOSE
      </p>
      <p
        v-else-if="result === 'draw'"
        class="text-center text-white text-2xl font-bold pb-2 mt-16"
      >
        DRAW
      </p>
      <button
        @click="playAgain"
        class="bg-white rounded-md px-6 py-1 dark-text"
      >
        PLAY AGAIN
      </button>
    </div>
  </div>
</template>

<script>
import Paper from "./Paper.vue";
import Rock from "./Rock.vue";
import Scissors from "./Scissors.vue";
import NotSelected from "./NotSelected.vue";

export default {
  created() {
    console.log(";nbb", this.house);
  },
  props: {
    selected: {
      type: String,
      default: "",
    },
    house: {
      type: String,
      default: "",
    },
    result: {
      type: String,
      default: "",
    },
  },
  components: {
    Paper,
    Rock,
    Scissors,
    NotSelected,
  },
  methods: {
    playAgain() {
      this.$emit("reset");
    },
  },
};
</script>
