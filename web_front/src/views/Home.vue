<template>
  <div id="home">
    <div id="splashview-hero" class="small">
      <div class="banner-usage small2" />
    </div>
    <HelloWorld msg="Welcome to My Vue.js + TypeScript App" />
    <TTS />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import HelloWorld from "@/components/HelloWorld.vue"; // @ is an alias to /src
import TTS from "@/components/TTS.vue";

@Options({
  components: {
    HelloWorld,
    TTS,
  },
})
export default class Home extends Vue {}
</script>

<style lang="scss">
#home {
  width: 100%;
  height: 100%;
  text-align: center;
  position: absolute;
  display: flex;
  flex-direction: column;
  align-items: center;
  // justify-content: space-around;
}

#home #splashview-hero {
  width: 90%;
  max-width: 1000px;
  max-height: 800px;
  min-height: 70px;
  margin-top: 10px;
  margin-left: 10px;
  margin-right: 10px;
  flex-grow: 20;
  background-position: center;
  background-size: contain;
  // background-image: url(../assets/sprite.svg#hero-usage);
  background-repeat: no-repeat;
  position: relative;
}

.banner-usage {
  width: 100%;
  height: 100%;
  position: absolute;
  background-position: center;
  background-size: contain;
  background-repeat: no-repeat;
  background-image: url(../assets/sprite.svg#banner-usage);
}

@media screen and (min-height: 700px) {
  .small {
    width: 90%;
    max-width: 1000px;
    max-height: 300px;
    min-height: 70px;
    margin-top: 10px;
    margin-left: 10px;
    margin-right: 10px;
    flex-grow: 20;
    background-position: center;
    background-size: contain;
    background-image: url(../assets/sprite.svg#hero-usage);
    background-repeat: no-repeat;
    position: relative;
  }

  .small2 {
    width: 100%;
    height: 100%;
    position: absolute;
    background-position: center;
    background-size: contain;
    background-repeat: no-repeat;
    background-image: url(../assets/sprite.svg#banner-usage);
  }
}

</style>
