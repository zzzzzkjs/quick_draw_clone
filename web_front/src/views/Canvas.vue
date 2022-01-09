<template>
  <div class="canvas_view">
    <div class="color_palette">
      <button @click="clear()">지우기</button>
    </div>
    <canvas
      resize="true"
      width="1278"
      height="1279"
      style="
        -webkit-user-drag: none;
        user-select: none;
        -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
        width: 1278x;
        height: 1279px;
      "
      @mousedown="mousedown($event)"
      @mouseup="mouseup()"
      @mousemove="mousemove($event)"
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
      // 핸드폰 터치 이벤트 추가할것
      this.x = e.offsetX;
      this.y = e.offsetY;
      if (this.drawing) {
        this.draw(this.x, this.y);
      }
    },
    clear() {
      const width = this.$refs.canvas.width;
      const height = this.$refs.canvas.height;
      this.ctx.clearRect(0, 0, width, height);
      this.drawing = false;
    },
    // mouseout() {
    // this.drawing = false;
    // },
    draw(x: number, y: number) {
      this.ctx.lineTo(x, y);
      this.ctx.stroke();
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
