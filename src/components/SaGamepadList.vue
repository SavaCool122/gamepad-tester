<script>
import SaGamepad from "./SaGamepad.vue";

export default {
  name: "SaGamepadList",

  components: {
    SaGamepad,
  },

  data() {
    return {
      gamepadList: [],
    };
  },
  
  methods: {
    gamepadConnectHandler(e) {
      this.tick();
    },
    tick() {
      this.gamepadList = navigator.getGamepads();
      window.requestAnimationFrame(this.tick);
    },
  },

  mounted() {
    window.addEventListener("gamepadconnected", e => {
      this.gamepadList = navigator.getGamepads();
      
      console.log(this.gamepadList); // to see gamepads info
      this.tick();
    });
  },

  beforeUnmount() {
    window.removeEventListener("gamepadconnected");
  },
};
</script>

<template>
  <div>
    <div v-if="gamepadList.length > 0">
      <div v-if="gamepadList">
        <div v-for="(gamepad, index) in gamepadList" class="m-5" :key="index">
          <SaGamepad v-if="gamepad" :gamepadConfig="gamepad" />
        </div>
      </div>
    </div>
    <div v-else class="bg-gray-50 text-center grid gap-3 p-5 rounded-lg ">
      <h2 class="text-3xl">No gamepads detected</h2>
      <p class="">Press any button on gamepad to start</p>
      <div class="w-auto justify-self-center">
        <img src="../svg/oval.svg" />
      </div>
    </div>
  </div>
</template>