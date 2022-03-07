<template>
  <div>
    <div class="flex flex-col items-center">
      <Header :score="score" />

      <div class="mt-24 main-part" v-if="!selected">
        <Step1 @selected="selectedObject" />
      </div>

      <div class="mt-24 md:w-2/5 w-full" v-if="selected">
        <Transition name="bounce">
          <Step2
            :selected="selected"
            :house="house"
            @reset="reset"
            :result="result"
          />
        </Transition>
      </div>
    </div>

    <div class="w-full invisible lg:visible" id="fixedbutton">
      <button
        @click="showModal = true"
        class="float-right mr-8 mb-8 text-white border-solid border-2 border-white rounded px-6 py-1"
      >
        RULES
      </button>
    </div>

    <div class="mt-24 w-full visible lg:invisible flex flex-col items-center">
      <button
        @click="showModal = true"
        class="text-white border-solid border-2 border-white rounded px-6 py-1"
      >
        RULES
      </button>
    </div>

    <vue-final-modal
      v-model="showModal"
      :click-to-close="true"
      :esc-to-close="true"
      content-class="flex flex-row items-center justify-center h-full"
    >
      <div class="bg-white w-80 p-6 rounded-md">
        <div class="flex flex-row pb-8 w-full justify-between">
          <h3 class="text-lg font-bold" style="color: hsl(229, 25%, 31%)">
            RULES
          </h3>
          <img
            src="./assets/icon-close.svg"
            class="cursor-pointer h-4 mt-2"
            @click="showModal = false"
          />
        </div>
        <div class="flex flex-col items-center">
          <img src="./assets/image-rules.svg" />
        </div>
      </div>
    </vue-final-modal>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Step1 from "./components/Step1.vue";
import Step2 from "./components/Step2.vue";
import { VueFinalModal } from "vue-final-modal";
import { useCookies } from "vue3-cookies";

export default {
  name: "App",
  components: {
    Header,
    Step1,
    VueFinalModal,
    Step2,
  },
  created() {
    this.cookies = useCookies().cookies;
    const cookiesScore = this.cookies.get("score");
    if (cookiesScore !== null) {
      this.score = parseInt(cookiesScore);
    }
  },
  data() {
    return {
      showModal: false,
      selected: "",
      score: 0,
      house: "",
      result: "",
      cookies: null,
    };
  },
  methods: {
    setHouse() {
      const items = ["paper", "rock", "scissors"];
      this.house = items[Math.floor(Math.random() * items.length)];
      setTimeout(this.selectWinner, 1000);
    },
    selectedObject(object) {
      this.selected = object;
      setTimeout(this.setHouse, 1000);
    },
    reset() {
      this.selected = "";
      this.house = "";
      this.result = "";
    },
    selectWinner() {
      switch (this.selected + this.house) {
        case "rockscissors":
        case "scissorspaper":
        case "paperrock":
          this.result = "win";
          this.score = this.score + 1;
          this.cookies.set("score", this.score, 7200);
          break;
        case "scissorsrock":
        case "paperscissors":
        case "rockpaper":
          this.result = "lose";
          break;
        case "paperpaper":
        case "scissorsscissors":
        case "rockrock":
          this.result = "draw";
          break;
      }

      return this.result;
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Barlow+Semi+Condensed&display=swap");
#app {
  font-family: "Barlow Semi Condensed", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  padding-bottom: 70px;
  padding-top: 35px;
}

.main-part {
  background-image: url("./assets/bg-triangle.svg");
  background-repeat: no-repeat;
  width: 100%;
  max-width: 300px;
  height: 100%;
  height: 276px;
}

.bounce-enter-active {
  animation: bounce-in 0.5s;
}
.bounce-leave-active {
  animation: bounce-in 0.5s reverse;
}
@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.25);
  }
  100% {
    transform: scale(1);
  }
}

#fixedbutton {
  position: fixed;
  bottom: 0px;
  right: 0px;
}
</style>
