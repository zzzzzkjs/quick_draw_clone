<template>
  <div class="canvas_view">
    <div class="color_palette">
      <button @click="clear()">지우기</button>
    </div>
    <!-- <canvas
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
      @mousedown="mousedown($event)"
      @mouseup="mouseup()"
      @mousemove="mousemove($event)"
      @touchstart="touchstart($event)"
      @touchend="touchend()"
      @touchmove="touchmove($event)"
      ref="canvas"
    ></canvas> -->
    <canvas
      resize="true"
      width="390"
      height="844"
      style="
        -webkit-user-drag: none;
        user-select: none;
        -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
        width: 390px;
        height: 844px;
      "
      @mousedown="mousedown($event)"
      @mouseup="mouseup()"
      @mousemove="mousemove($event)"
      @touchstart="touchstart($event)"
      @touchend="touchend()"
      @touchmove="touchmove($event)"
      ref="canvas"
    ></canvas>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";

@Options({
  data() {
    return {
      drawing: false,
      canvas: null,
      ctx: null,
      x: 0,
      y: 0,
      touchX: 0,
      touchY: 0,
      lineWidth: 10,
      lineCap: "round",
      strokeStyle: "black",
    };
  },
  mounted() {
    this.canvas = this.$refs.canvas;
    this.ctx = this.canvas.getContext("2d");

    this.ctx.lineWidth = 10;
    this.ctx.lineCap = "round";
    this.ctx.strokeStyle = "black";
  },
  methods: {
    canvasScaleUp() {
      // var scaleX = window.innerWidth / canvas.width;
      // var scaleY = window.innerHeight / canvas.height;
      // var scaleToFit = Math.min(scaleX, scaleY);
      // var scaleToCover = Math.max(scaleX, scaleY);
      // stage.style.transformOrigin = '0 0'; //scale from top left
      // stage.style.transform = 'scale(' + scaleToFit + ')';
    },
    mousedown(e: MouseEvent) {
      const startX = e.offsetX;
      const startY = e.offsetY;

      this.ctx.beginPath();
      this.ctx.moveTo(startX, startY);

      this.drawing = true;
    },
    mouseup() {
      this.drawing = false;
    },
    mousemove(e: MouseEvent) {
      this.x = e.offsetX;
      this.y = e.offsetY;
      if (this.drawing) {
        this.draw(this.x, this.y);
      }
    },
    touchstart(e: TouchEvent) {
      e.preventDefault();
      const startX = e.changedTouches[0].screenX;
      const startY = e.changedTouches[0].screenY;

      this.ctx.beginPath();
      this.ctx.moveTo(startX, startY);

      this.drawing = true;
    },
    touchend() {
      this.drawing = false;
    },
    touchmove(e: TouchEvent) {
      e.preventDefault();
      this.touchX = e.changedTouches[0].screenX;
      this.touchY = e.changedTouches[0].screenY;
      if (this.drawing) {
        this.touchDraw(this.touchX, this.touchY);
      }
    },
    // mouseout() {
    // this.drawing = false;
    // },
    draw(x: number, y: number) {
      this.ctx.lineTo(x, y);
      this.ctx.stroke();
    },
    touchDraw(touchX: number, touchY: number) {
      this.ctx.lineTo(touchX, touchY);
      this.ctx.stroke();
    },
    clear() {
      const width = this.$refs.canvas.width;
      const height = this.$refs.canvas.height;
      this.ctx.clearRect(0, 0, width, height);
      this.drawing = false;
    },
  },
})
export default class HelloWorld extends Vue {}
</script>

<style lang="scss" scoped>
.color_palette {
  margin: 0 auto;
  width: 50vw;
  height: 3vh;
}

canvas {
  border: 1px solid black;
}
</style>
