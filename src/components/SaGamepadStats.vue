<script>
export default {
  name: "SaGamepadStats",

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
  <div class="grid grid-cols-1 auto-rows-min gap-4">
    <ul class="grid grid-cols-6">
      <li
        v-for="(btn, index) in gamepadConfig.buttons"
        :key="index"
        class="pr-1 flex flex-col"
      >
        <label>B{{ index }}:</label>
        <span>{{ btn.pressed }}</span>
      </li>
    </ul>

    <ul class="grid grid-cols-4">
      <li
        v-for="(axes, index) in gamepadConfig.axes"
        :key="index"
        class="pr-1 flex flex-col"
      >
        <label>Axes {{ index }}</label>
        <span>{{ axes.toFixed(4) }}</span>
      </li>
    </ul>

    <span class="row-start-3">
      Time timestamp {{ gamepadConfig.timestamp.toFixed(3) }}
    </span>
  </div>
</template>
