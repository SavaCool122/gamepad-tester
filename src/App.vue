<template>
  <div>
    <SaHeader />

    <div class="p-6 max-w-md mx-auto m-3 bg-white rounded-xl shadow-md">
      <div>
        <p class="text-gray-500">
          So far, Chrome is the only browser that supports almost all properties
          of Gamepad API
        </p>
      </div>
    </div>

    <div class="container mx-auto px-4 md:min-h-40 m-10">
      <SaGamepadList />
    </div>
  </div>
</template>

<script>
import SaGamepadList from "./components/SaGamepadList.vue";
import SaHeader from "./components/SaHeader.vue";

export default {
  name: "App",

  components: {
    SaGamepadList,
    SaHeader,
  },
};
</script>