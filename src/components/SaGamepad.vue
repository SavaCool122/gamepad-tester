<script>
import SaGamepadSvg from "./SaGamepadSvg.vue";
import SaGamepadStats from "./SaGamepadStats.vue";
import SaGamepadVibrationButton from "./SaGamepadVibrationButton.vue";

export default {
  name: "SaGamepad",

  components: {
    SaGamepadSvg,
    SaGamepadStats,
    SaGamepadVibrationButton,
  },

  props: {
    gamepadConfig: {
      type: Object,
      required: true,
      default: () => {},
    },
  },
};
</script>

<template>
  <div
    class="container grid grid-cols-2 justify-items-center rounded-lg bg-gray-50 shadow-md"
  >
    <div class="grid grid-cols-1 auto-rows-min gap-4 p-5">
      <h2 class="col-span-full text-xl font-semibold antialiased">
        {{ gamepadConfig.id }}
      </h2>
      <SaGamepadVibrationButton :gamepadConfig="gamepadConfig" />
      <SaGamepadStats :gamepadConfig="gamepadConfig" />
    </div>
    <SaGamepadSvg class="max-w-md p-4" :gamepadConfig="gamepadConfig" />
  </div>
</template>
