<script>
import {
  defaultStickPosition,
  defaultStickOpacity,
  activeColor,
  standardColor,
} from "../constant";

export default {
  name: "SaGamepadSvg",

  props: {
    gamepadConfig: {
      type: Object,
      required: true,
      default: () => {},
    },
  },

  data() {
    return {
      defaultStickPosition,
      defaultStickOpacity,
      activeColor,
      standardColor
    };
  },

  computed: {
    leftStickPosition() {
      const [x, y] = this.gamepadConfig.axes;
      const xStart = this.defaultStickPosition.left.x;
      const yStart = this.defaultStickPosition.left.y;
      return this.positionForStick(xStart, yStart, x, y);
    },
    rightStickPosition() {
      const [, , x, y] = this.gamepadConfig.axes;
      const xStart = this.defaultStickPosition.right.x;
      const yStart = this.defaultStickPosition.right.y;
      return this.positionForStick(xStart, yStart, x / 1.3, y);
    },
    leftStickOpacity() {
      const [x, y] = this.gamepadConfig.axes;
      const opacityMult = Math.abs(x) + Math.abs(y);
      const opacity = this.defaultStickOpacity.left + opacityMult / 2;
      return opacity.toFixed(2);
    },
    rightStickOpacity() {
      const [, , x, y] = this.gamepadConfig.axes;
      const opacityMult = Math.abs(x) + Math.abs(y);
      const opacity = this.defaultStickOpacity.left + opacityMult / 2;
      return opacity.toFixed(2);
    },
    buttonsArray() {
      return this.gamepadConfig.buttons.map(b => b.pressed);
    },
  },

  methods: {
    positionForStick(xStart, yStart, x, y) {
      x = xStart + (xStart * x.toFixed(2)) / 22;
      y = yStart + (yStart * y.toFixed(2)) / 34;
      x = x.toFixed(2);
      y = y.toFixed(2);
      return { x, y };
    },
  },
};
</script>

<template>
  <svg
    xmlns:inkscape="http://www.inkscape.org/namespaces/inkscape"
    xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"
    xmlns="http://www.w3.org/2000/svg"
    xmlns:cc="http://creativecommons.org/ns#"
    xmlns:dc="http://purl.org/dc/elements/1.1/"
    xmlns:sodipodi="http://sodipodi.sourceforge.net/DTD/sodipodi-0.dtd"
    xmlns:svg="http://www.w3.org/2000/svg"
    xmlns:ns1="http://sozi.baierouge.fr"
    xmlns:xlink="http://www.w3.org/1999/xlink"
    id="svg2"
    sodipodi:docname="playstation3-gamepad.svg"
    viewBox="0 0 242.36 151.02"
    sodipodi:version="0.32"
    version="1.0"
    inkscape:output_extension="org.inkscape.output.svg.inkscape"
    inkscape:version="0.46"
  >
    <g
      id="layer1"
      inkscape:label="Layer 1"
      inkscape:groupmode="layer"
      transform="translate(-260.34 -473.69)"
    >
      <path
        id="rect3225"
        style="
          stroke-linejoin: round;
          fill-rule: evenodd;
          stroke: #000000;
          stroke-linecap: round;
          fill: #3f3f3f;
        "
        sodipodi:nodetypes="ccccccccccccc"
        d="m60.281 24.156c-1.536 0-2.75 1.246-2.75 2.782v73.152c0 1.54 1.214 2.75 2.75 2.75h121.78c1.54 0 2.78-1.21 2.78-2.75v-73.152c0-1.536-1.24-2.782-2.78-2.782h-52.81c-0.27 0.449-0.77 0.75-1.34 0.75h-14.31c-0.57 0-1.04-0.303-1.31-0.75h-52.009z"
        transform="translate(260.34 473.69)"
      />
      <rect
        id="rect3318"
        style="fill-rule: evenodd; fill: #262626"
        rx="2.7723"
        ry="2.6797"
        height="68.484"
        width="114.69"
        y="504.14"
        x="324.17"
      />
      <path
        id="path3206"
        sodipodi:nodetypes="csscc"
        style="fill-rule: evenodd; stroke: #000000; fill: #262626"
        d="m272.94 520.34c-5.49 30.06-9.07 62.22-11.76 76.34-4.23 22.13 32.77 40.74 46.79 15.16 10.65-19.42 22.75-44.18 22.75-44.18l-57.78-47.32z"
      />
      <path
        id="path3258"
        sodipodi:nodetypes="ccscsc"
        style="fill-rule: evenodd; stroke: #000000; fill: #7a7a7a"
        :style="{
          stroke: this.gamepadConfig.buttons[5].pressed ? activeColor : standardColor,
        }"
        d="m435.52 483.74h33.15l-2.6-4.27c-1.7-2.8-6.13-4.88-13.98-4.88-7.84 0-12.27 2.08-13.98 4.88l-2.59 4.27z"
      />
      <path
        id="path3234"
        sodipodi:nodetypes="ccscsc"
        style="fill-rule: evenodd; stroke: #000000; fill: #7a7a7a"
        :style="{
          stroke: this.gamepadConfig.buttons[4].pressed ? activeColor : standardColor,
        }"
        d="m293.16 483.74h33.15l-2.59-4.27c-1.71-2.8-6.14-4.88-13.98-4.88-7.85 0-12.28 2.08-13.98 4.88l-2.6 4.27z"
      />
      <path
        id="path3229"
        sodipodi:nodetypes="cscsc"
        style="fill-rule: evenodd; stroke: #000000; fill: #262626"
        d="m330.59 503.61c-1.7-10.98-2.49-16.47-3.27-20.53-0.78-4.05-7.71-6.14-17.58-6.14s-16.8 2.09-17.58 6.14c-0.79 4.06-1.57 9.55-3.27 20.53"
      />
      <path
        id="path2416"
        sodipodi:rx="37.64706"
        sodipodi:ry="37.64706"
        style="
          stroke-linejoin: round;
          fill-rule: evenodd;
          stroke: #000000;
          stroke-linecap: round;
          stroke-width: 0.9931;
          fill: #333333;
        "
        sodipodi:type="arc"
        d="m341.44 528.96a37.647 37.647 0 1 1 -75.3 0 37.647 37.647 0 1 1 75.3 0z"
        transform="matrix(1.0069 0 0 1.0069 3.9034 -2.889)"
        sodipodi:cy="528.9635"
        sodipodi:cx="303.79086"
      />
      <path
        id="path3260"
        sodipodi:nodetypes="cscsc"
        style="fill-rule: evenodd; stroke: #000000; fill: #262626"
        d="m472.94 503.61c-1.7-10.98-2.48-16.47-3.27-20.53-0.78-4.05-7.71-6.14-17.58-6.14s-16.8 2.09-17.58 6.14c-0.78 4.06-1.57 9.55-3.27 20.53"
      />
      <path
        id="path3208"
        sodipodi:rx="37.64706"
        sodipodi:ry="37.64706"
        style="
          stroke-linejoin: round;
          fill-rule: evenodd;
          stroke: #000000;
          stroke-linecap: round;
          stroke-width: 1.5652;
          fill: #333333;
        "
        sodipodi:type="arc"
        d="m341.44 528.96a37.647 37.647 0 1 1 -75.3 0 37.647 37.647 0 1 1 75.3 0z"
        transform="matrix(.63889 0 0 .63889 152.06 228.66)"
        sodipodi:cy="528.9635"
        sodipodi:cx="303.79086"
      />
      <path
        id="path3212"
        sodipodi:rx="37.64706"
        sodipodi:ry="37.64706"
        style="
          stroke-linejoin: round;
          fill-rule: evenodd;
          fill-opacity: 0.51852;
          stroke: #000000;
          stroke-linecap: round;
          stroke-width: 2.0282;
          fill: #000000;
        "
        sodipodi:type="arc"
        d="m341.44 528.96a37.647 37.647 0 1 1 -75.3 0 37.647 37.647 0 1 1 75.3 0z"
        transform="matrix(.49306 0 0 .49306 196.36 305.8)"
        sodipodi:cy="528.9635"
        sodipodi:cx="303.79086"
      />
      <path
        id="path3210"
        sodipodi:rx="37.64706"
        sodipodi:ry="37.64706"
        style="
          stroke-linejoin: round;
          fill-rule: evenodd;

          stroke: #000000;
          stroke-linecap: round;
          stroke-width: 2.3226;
          fill: #4d4d4d;
        "
        :style="{
          'fill-opacity': leftStickOpacity,
          stroke: this.gamepadConfig.buttons[10].pressed ? activeColor : standardColor,
        }"
        sodipodi:type="arc"
        d="m341.44 528.96a37.647 37.647 0 1 1 -75.3 0 37.647 37.647 0 1 1 75.3 0z"
        :transform="`matrix(.43056 0 0 .43056 ${leftStickPosition.x} ${leftStickPosition.y})`"
        sodipodi:cy="528.9635"
        sodipodi:cx="303.79086"
      />
      <path
        id="path3223"
        sodipodi:nodetypes="csscc"
        style="fill-rule: evenodd; stroke: #000000; fill: #262626"
        d="m490.08 520.34c5.49 30.06 9.07 62.75 11.76 76.34 4.38 22.1-32.77 40.74-46.8 15.16-10.64-19.42-22.74-44.18-22.74-44.18l57.78-47.32z"
      />
      <path
        id="path3221"
        sodipodi:rx="37.64706"
        sodipodi:ry="37.64706"
        style="
          stroke-linejoin: round;
          fill-rule: evenodd;
          stroke: #000000;
          stroke-linecap: round;
          stroke-width: 0.9931;
          fill: #333333;
        "
        sodipodi:type="arc"
        d="m341.44 528.96a37.647 37.647 0 1 1 -75.3 0 37.647 37.647 0 1 1 75.3 0z"
        transform="matrix(-1.0069 0 0 1.0069 759.11 -2.889)"
        sodipodi:cy="528.9635"
        sodipodi:cx="303.79086"
      />
      <path
        id="path3219"
        style="fill-rule: evenodd; fill: #262626"
        d="m445.43 501.73c-1.53 0-2.78 1.25-2.78 2.78v14.66h-14.69c-1.53 0-2.75 1.25-2.75 2.78v15.59c0 1.54 1.22 2.79 2.75 2.79h14.69v14.65c0 1.54 1.25 2.78 2.78 2.78h15.6c1.53 0 2.75-1.24 2.75-2.78v-14.65h14.68c1.54 0 2.75-1.25 2.75-2.79v-15.59c0-1.53-1.21-2.78-2.75-2.78h-14.68v-14.66c0-1.53-1.22-2.78-2.75-2.78h-15.6z"
      />
      <rect
        id="rect3236"
        style="
          stroke-linejoin: round;
          fill-rule: evenodd;
          stroke: #000000;
          stroke-linecap: round;
          fill: #595959;
        "
        :style="{
          stroke: this.gamepadConfig.buttons[8].pressed ? activeColor : standardColor,
        }"
        rx="1.5686"
        ry="1.5686"
        height="6.6667"
        width="11.634"
        y="530.28"
        x="353.46"
      />
      <path
        id="rect3238"
        sodipodi:nodetypes="csccsc"
        style="
          stroke-linejoin: round;
          fill-rule: evenodd;
          stroke: #000000;
          stroke-linecap: round;
          fill: #595959;
        "
        :style="{
          stroke: this.gamepadConfig.buttons[9].pressed ? activeColor : standardColor,
        }"
        d="m407.19 533.61l-8.5 3.33c-0.81 0.32-1.57-0.7-1.57-1.57v-3.53c0-0.86 0.76-1.88 1.57-1.56l8.5 3.33z"
      />
      <path
        id="path3242"
        sodipodi:rx="5.7516341"
        sodipodi:ry="5.7516341"
        style="
          stroke-linejoin: round;
          fill-rule: evenodd;
          stroke: #000000;
          stroke-linecap: round;
          fill: #595959;
        "
        sodipodi:type="arc"
        d="m380 545.83a5.7516 5.7516 0 1 1 -11.5 0 5.7516 5.7516 0 1 1 11.5 0z"
        transform="matrix(1.3796 0 0 1.3796 -133.81 -201.68)"
        sodipodi:cy="545.82623"
        sodipodi:cx="374.24835"
      />
      <path
        id="path3244"
        sodipodi:rx="8.2352943"
        sodipodi:ry="8.2352943"
        style="
          fill-opacity: 1;
          stroke-linejoin: round;
          fill-rule: evenodd;
          stroke: #454545;
          stroke-linecap: round;
          fill: #5a5a5a;
        "
        :style="{
          stroke: this.gamepadConfig.buttons[3].pressed ? activeColor : standardColor,
        }"
        sodipodi:type="arc"
        d="m461.57 510.66a8.2353 8.2353 0 1 1 -16.47 0 8.2353 8.2353 0 1 1 16.47 0z"
        transform="translate(-.11915 1.4379)"
        sodipodi:cy="510.66284"
        sodipodi:cx="453.33334"
      />
      <path
        id="path3246"
        sodipodi:rx="8.2352943"
        sodipodi:ry="8.2352943"
        style="
          stroke-linejoin: round;
          fill-rule: evenodd;
          stroke: #454545;
          stroke-linecap: round;
          fill: #5a5a5a;
        "
        :style="{
          stroke: this.gamepadConfig.buttons[0].pressed ? activeColor : standardColor,
        }"
        sodipodi:type="arc"
        d="m461.57 510.66a8.2353 8.2353 0 1 1 -16.47 0 8.2353 8.2353 0 1 1 16.47 0z"
        transform="translate(-.11915 36.863)"
        sodipodi:cy="510.66284"
        sodipodi:cx="453.33334"
      />
      <path
        id="path3248"
        sodipodi:rx="8.2352943"
        sodipodi:ry="8.2352943"
        style="
          stroke-linejoin: round;
          fill-rule: evenodd;
          stroke: #454545;
          stroke-linecap: round;
          fill: #5a5a5a;
        "
        :style="{
          stroke: this.gamepadConfig.buttons[1].pressed ? activeColor : standardColor,
        }"
        sodipodi:type="arc"
        d="m461.57 510.66a8.2353 8.2353 0 1 1 -16.47 0 8.2353 8.2353 0 1 1 16.47 0z"
        transform="matrix(-1 0 0 -1 924.26 1040.5)"
        sodipodi:cy="510.66284"
        sodipodi:cx="453.33334"
      />
      <path
        id="path3250"
        sodipodi:rx="8.2352943"
        sodipodi:ry="8.2352943"
        style="
          stroke-linejoin: round;
          fill-rule: evenodd;
          stroke: #454545;
          stroke-linecap: round;
          fill: #5a5a5a;
        "
        :style="{
          stroke: this.gamepadConfig.buttons[2].pressed ? activeColor : standardColor,
        }"
        sodipodi:type="arc"
        d="m461.57 510.66a8.2353 8.2353 0 1 1 -16.47 0 8.2353 8.2353 0 1 1 16.47 0z"
        transform="matrix(-1 0 0 -1 888.84 1040.5)"
        sodipodi:cy="510.66284"
        sodipodi:cx="453.33334"
      />
      <path
        id="rect3214"
        style="fill-rule: evenodd; fill: #262626"
        d="m301.84 501.25c-1.53 0-2.78 1.25-2.78 2.78v14.66h-14.68c-1.54 0-2.76 1.24-2.76 2.78v15.59c0 1.54 1.22 2.78 2.76 2.78h14.68v14.66c0 1.54 1.25 2.78 2.78 2.78h15.6c1.53 0 2.75-1.24 2.75-2.78v-14.66h14.69c1.53 0 2.74-1.24 2.74-2.78v-15.59c0-1.54-1.21-2.78-2.74-2.78h-14.69v-14.66c0-1.53-1.22-2.78-2.75-2.78h-15.6z"
      />
      <path
        id="path3289"
        sodipodi:rx="37.64706"
        sodipodi:ry="37.64706"
        style="
          stroke-linejoin: round;
          fill-rule: evenodd;
          stroke: #000000;
          stroke-linecap: round;
          stroke-width: 1.5652;
          fill: #333333;
        "
        sodipodi:type="arc"
        d="m341.44 528.96a37.647 37.647 0 1 1 -75.3 0 37.647 37.647 0 1 1 75.3 0z"
        transform="matrix(.63889 0 0 .63889 222.12 228.66)"
        sodipodi:cy="528.9635"
        sodipodi:cx="303.79086"
      />
      <path
        id="path3291"
        sodipodi:rx="37.64706"
        sodipodi:ry="37.64706"
        style="
          stroke-linejoin: round;
          fill-rule: evenodd;
          fill-opacity: 0.51852;
          stroke: #000000;
          stroke-linecap: round;
          stroke-width: 2.0282;
          fill: #000000;
        "
        sodipodi:type="arc"
        d="m341.44 528.96a37.647 37.647 0 1 1 -75.3 0 37.647 37.647 0 1 1 75.3 0z"
        transform="matrix(.49306 0 0 .49306 266.42 305.8)"
        sodipodi:cy="528.9635"
        sodipodi:cx="303.79086"
      />
      <path
        id="path3293"
        sodipodi:rx="37.64706"
        sodipodi:ry="37.64706"
        style="
          stroke-linejoin: round;
          fill-rule: evenodd;
          stroke: #000000;
          stroke-linecap: round;
          stroke-width: 2.3226;
          fill: #4d4d4d;
        "
        :style="{
          'fill-opacity': rightStickOpacity,
          stroke: this.gamepadConfig.buttons[11].pressed ? activeColor : standardColor,
        }"
        sodipodi:type="arc"
        d="m341.44 528.96a37.647 37.647 0 1 1 -75.3 0 37.647 37.647 0 1 1 75.3 0z"
        :transform="`matrix(.43056 0 0 .43056 ${rightStickPosition.x} ${rightStickPosition.y})`"
        sodipodi:cy="528.9635"
        sodipodi:cx="303.79086"
      />
      <g id="g5204" style="stroke: #454545; fill: #5a5a5a">
        <path
          id="path3322"
          style="
            stroke-linejoin: round;
            fill-rule: evenodd;
            stroke: #454545;
            stroke-linecap: round;
            fill: #5a5a5a;
          "
          :style="{
            stroke: this.gamepadConfig.buttons[15].pressed ? activeColor : standardColor,
          }"
          sodipodi:type="inkscape:offset"
          d="m318.59 523.28c-0.33 0.03-0.64 0.2-0.84 0.47l-3.5 4.44c-0.33 0.42-0.33 1.01 0 1.43l3.5 4.47c0.22 0.3 0.57 0.47 0.94 0.47l8.12 0.03c0.32 0.01 0.62-0.12 0.84-0.34 0.23-0.22 0.35-0.53 0.35-0.84v-8.79c0-0.64-0.51-1.17-1.16-1.18l-8.12-0.16h-0.13z"
          inkscape:original="M 318.6875 524.46875 L 315.1875 528.90625 L 318.6875 533.375 L 326.8125 533.40625 L 326.8125 524.625 L 318.6875 524.46875 z "
          transform="translate(.35102 .37335)"
          inkscape:radius="1.1788157"
        />
        <path
          id="path3324"
          style="
            stroke-linejoin: round;
            fill-rule: evenodd;
            stroke: #454545;
            stroke-linecap: round;
            fill: #5a5a5a;
          "
          :style="{
            stroke: this.gamepadConfig.buttons[14].pressed ? activeColor : standardColor,
          }"
          sodipodi:type="inkscape:offset"
          d="m318.59 523.28c-0.33 0.03-0.64 0.2-0.84 0.47l-3.5 4.44c-0.33 0.42-0.33 1.01 0 1.43l3.5 4.47c0.22 0.3 0.57 0.47 0.94 0.47l8.12 0.03c0.32 0.01 0.62-0.12 0.84-0.34 0.23-0.22 0.35-0.53 0.35-0.84v-8.79c0-0.64-0.51-1.17-1.16-1.18l-8.12-0.16h-0.13z"
          inkscape:original="M 318.6875 524.46875 L 315.1875 528.90625 L 318.6875 533.375 L 326.8125 533.40625 L 326.8125 524.625 L 318.6875 524.46875 z "
          transform="matrix(-1 0 0 1 618.9 .28450)"
          inkscape:radius="1.1788157"
        />
        <path
          id="path3332"
          style="
            stroke-linejoin: round;
            fill-rule: evenodd;
            stroke: #454545;
            stroke-linecap: round;
            fill: #5a5a5a;
          "
          :style="{
            stroke: this.gamepadConfig.buttons[13].pressed ? activeColor : standardColor,
          }"
          sodipodi:type="inkscape:offset"
          d="m318.59 523.28c-0.33 0.03-0.64 0.2-0.84 0.47l-3.5 4.44c-0.33 0.42-0.33 1.01 0 1.43l3.5 4.47c0.22 0.3 0.57 0.47 0.94 0.47l8.12 0.03c0.32 0.01 0.62-0.12 0.84-0.34 0.23-0.22 0.35-0.53 0.35-0.84v-8.79c0-0.64-0.51-1.17-1.16-1.18l-8.12-0.16h-0.13z"
          inkscape:original="M 318.6875 524.46875 L 315.1875 528.90625 L 318.6875 533.375 L 326.8125 533.40625 L 326.8125 524.625 L 318.6875 524.46875 z "
          transform="matrix(0 1 -1 0 838.52 219.99)"
          inkscape:radius="1.1788157"
        />
        <path
          id="path3334"
          style="
            stroke-linejoin: round;
            fill-rule: evenodd;
            stroke: #454545;
            stroke-linecap: round;
            fill: #5a5a5a;
          "
          :style="{
            stroke: this.gamepadConfig.buttons[12].pressed ? activeColor : standardColor,
          }"
          sodipodi:type="inkscape:offset"
          d="m318.59 523.28c-0.33 0.03-0.64 0.2-0.84 0.47l-3.5 4.44c-0.33 0.42-0.33 1.01 0 1.43l3.5 4.47c0.22 0.3 0.57 0.47 0.94 0.47l8.12 0.03c0.32 0.01 0.62-0.12 0.84-0.34 0.23-0.22 0.35-0.53 0.35-0.84v-8.79c0-0.64-0.51-1.17-1.16-1.18l-8.12-0.16h-0.13z"
          inkscape:original="M 318.6875 524.46875 L 315.1875 528.90625 L 318.6875 533.375 L 326.8125 533.40625 L 326.8125 524.625 L 318.6875 524.46875 z "
          transform="matrix(0 -1 -1 0 838.61 838.54)"
          inkscape:radius="1.1788157"
        />
      </g>
      <path
        id="text2434"
        style="fill: #e6e6e6"
        d="m353.63 524.56v0.44c-0.17-0.08-0.34-0.14-0.49-0.18s-0.29-0.06-0.44-0.06c-0.24 0-0.43 0.04-0.56 0.14-0.14 0.09-0.2 0.23-0.2 0.4 0 0.15 0.04 0.26 0.13 0.34 0.09 0.07 0.26 0.13 0.5 0.18l0.27 0.05c0.34 0.07 0.59 0.18 0.75 0.34s0.24 0.38 0.24 0.65c0 0.32-0.11 0.57-0.33 0.73-0.21 0.17-0.53 0.25-0.95 0.25-0.15 0-0.32-0.02-0.5-0.05-0.18-0.04-0.36-0.09-0.55-0.16v-0.46c0.18 0.1 0.36 0.18 0.54 0.23 0.17 0.05 0.34 0.08 0.51 0.08 0.26 0 0.46-0.05 0.6-0.15 0.14-0.11 0.21-0.25 0.21-0.44 0-0.16-0.05-0.29-0.15-0.38s-0.27-0.16-0.5-0.21l-0.27-0.05c-0.34-0.07-0.58-0.17-0.73-0.32-0.15-0.14-0.23-0.34-0.23-0.59 0-0.3 0.11-0.53 0.31-0.7 0.21-0.17 0.5-0.25 0.86-0.25 0.16 0 0.32 0.01 0.48 0.04s0.33 0.07 0.5 0.13m0.9-0.11h2.1v0.38h-1.65v0.98h1.59v0.38h-1.59v1.21h1.69v0.38h-2.14v-3.33m2.89 0h0.45v2.95h1.62v0.38h-2.07v-3.33m2.54 0h2.1v0.38h-1.65v0.98h1.59v0.38h-1.59v1.21h1.7v0.38h-2.15v-3.33m5.38 0.26v0.47c-0.15-0.14-0.31-0.25-0.48-0.32s-0.36-0.1-0.55-0.1c-0.38 0-0.67 0.12-0.87 0.35-0.21 0.23-0.31 0.57-0.31 1.01s0.1 0.77 0.31 1c0.2 0.24 0.49 0.35 0.87 0.35 0.19 0 0.38-0.03 0.55-0.1s0.33-0.18 0.48-0.32v0.47c-0.16 0.11-0.32 0.19-0.5 0.24-0.17 0.06-0.36 0.08-0.56 0.08-0.5 0-0.9-0.15-1.19-0.46s-0.43-0.73-0.43-1.26c0-0.54 0.14-0.96 0.43-1.27s0.69-0.46 1.19-0.46c0.2 0 0.39 0.03 0.56 0.08 0.18 0.05 0.35 0.13 0.5 0.24m0.24-0.26h2.82v0.38h-1.19v2.95h-0.45v-2.95h-1.18v-0.38"
      />
      <path
        id="text2438"
        style="fill: #e6e6e6"
        d="m396.51 524.56v0.44c-0.17-0.08-0.33-0.14-0.48-0.18-0.16-0.04-0.3-0.06-0.44-0.06-0.25 0-0.44 0.04-0.57 0.14-0.13 0.09-0.2 0.23-0.2 0.4 0 0.15 0.04 0.26 0.13 0.34 0.09 0.07 0.26 0.13 0.5 0.18l0.28 0.05c0.33 0.07 0.58 0.18 0.74 0.34s0.24 0.38 0.24 0.65c0 0.32-0.11 0.57-0.33 0.73-0.21 0.17-0.53 0.25-0.95 0.25-0.15 0-0.32-0.02-0.5-0.05-0.18-0.04-0.36-0.09-0.55-0.16v-0.46c0.18 0.1 0.36 0.18 0.54 0.23 0.17 0.05 0.34 0.08 0.51 0.08 0.26 0 0.46-0.05 0.6-0.15 0.14-0.11 0.21-0.25 0.21-0.44 0-0.16-0.05-0.29-0.15-0.38s-0.27-0.16-0.5-0.21l-0.27-0.05c-0.34-0.07-0.58-0.17-0.73-0.32-0.15-0.14-0.22-0.34-0.22-0.59 0-0.3 0.1-0.53 0.31-0.7 0.2-0.17 0.49-0.25 0.85-0.25 0.16 0 0.32 0.01 0.48 0.04s0.33 0.07 0.5 0.13m0.44-0.11h2.82v0.38h-1.19v2.95h-0.45v-2.95h-1.18v-0.38m4.01 0.44l-0.61 1.66h1.22l-0.61-1.66m-0.26-0.44h0.51l1.27 3.33h-0.46l-0.31-0.86h-1.5l-0.3 0.86h-0.48l1.27-3.33m3.85 1.77c0.09 0.03 0.19 0.1 0.28 0.21 0.09 0.1 0.18 0.25 0.27 0.44l0.46 0.91h-0.48l-0.43-0.86c-0.11-0.22-0.22-0.37-0.32-0.44s-0.24-0.11-0.42-0.11h-0.49v1.41h-0.45v-3.33h1.01c0.38 0 0.67 0.08 0.86 0.24 0.18 0.16 0.28 0.4 0.28 0.72 0 0.21-0.05 0.38-0.15 0.52s-0.24 0.23-0.42 0.29m-1.13-1.4v1.18h0.56c0.22 0 0.38-0.05 0.49-0.15 0.12-0.1 0.17-0.25 0.17-0.44 0-0.2-0.05-0.34-0.17-0.44-0.11-0.1-0.27-0.15-0.49-0.15h-0.56m1.93-0.37h2.82v0.38h-1.19v2.95h-0.45v-2.95h-1.18v-0.38"
      />
    </g>
  </svg>
</template>

<style></style>
