<script>
export default {
  mame: "SaGamepadVibrationButton",

  props: {
    gamepadConfig: {
      type: Object,
      required: true,
      default: () => {},
    },
  },

  methods: {
    startVibrationTest(duration) {
      this.gamepadConfig.vibrationActuator.playEffect("dual-rumble", {
        strongMagnitude: 1.0,
        weakMagnitude: 0.5,
        duration: duration,
      });
    },
  },
};
</script>

<template>
  <button
    class="align-start place-self-start border-grey-600 border-2 p-2"
    @click="startVibrationTest(1000)"
  >
    Test Vibration
  </button>
</template>
