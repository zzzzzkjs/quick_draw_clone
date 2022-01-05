<template>
  <!-- <div class="canvas"> -->
  <canvas
    id="drawingCanvas"
    resize="true"
    width="1278"
    height="1279"
    style="
      -webkit-user-drag: none;
      user-select: none;
      -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
      width: 1278px;
      height: 1279px;
    "
    @mousedown="mousedown()"
    @mouseup="mouseup()"
    @mousemove="mousemove($event)"
    ref="canvas"
  ></canvas>
  <!-- </div> -->
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";

@Options({
  data() {
    return {
      drawing: false,
    };
  },
  methods: {
    mousedown() {
      console.log("1");
      this.drawing = true;
    },
    mouseup() {
      console.log("2");
      this.drawing = false;
    },
    mousemove(e) {
      if (this.drawing) {
        console.log("3");
        this.draw(e);
      }
    },
    draw(e) {
      const canvas = this.$refs.canvas;
      const ctx = canvas.getContext("2d");

      const x = e.offsetX;
      const y = e.offsetY;

      ctx.lineWidth = 10;
      ctx.lineCap = "round";
      ctx.strokeStyle = "black";

      if (!this.drawing) return;
      ctx.beginPath();
      ctx.moveTo(x, y);
      ctx.lineTo(x, y);
      ctx.stroke();
    },
  },
})
export default class HelloWorld extends Vue {}
</script>

<style lang="scss">
canvas {
  border: 1px solid black;
}
</style>
