<template>
  <div class="tts">
    <select id="select-lang" ref="selectLang">
      <option value="ko-KR">한국어</option>
      <option value="ja-JP" selected>일본어</option>
      <option value="en-US">영어</option>
    </select>
    <textarea id="text" rows="5" cols="20" ref="text"></textarea>
    <button id="btn-read" @click="read(this.$refs.text.value)">읽기</button>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";

@Options({
  methods: {
    speak(text: string, opt_prop: any) {
      if (
        typeof SpeechSynthesisUtterance === "undefined" ||
        typeof window.speechSynthesis === "undefined"
      ) {
        alert("이 브라우저는 음성 합성을 지원하지 않습니다.");
        return;
      }

      window.speechSynthesis.cancel(); // 현재 읽고있다면 초기화

      const prop = opt_prop || {};

      const speechMsg = new SpeechSynthesisUtterance();
      speechMsg.rate = prop.rate || 1; // 속도: 0.1 ~ 10
      speechMsg.pitch = prop.pitch || 1; // 음높이: 0 ~ 2
      speechMsg.lang = prop.lang || "ko-KR";
      speechMsg.text = text;

      // SpeechSynthesisUtterance에 설정한 값으로 음성 출력
      window.speechSynthesis.speak(speechMsg);
    },
    read(text: string) {
      let speakOption = {
        rate: 1,
        pitch: 1.2,
        lang: this.$refs.selectLang.options[this.$refs.selectLang.selectedIndex]
          .value,
      };
      this.speak(text, speakOption);
    },
  },
})
export default class TTS extends Vue {}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
