<template>
  <div class="grid-container">
    <section class="l-preview">
      <Preview :htmlCode="htmlCode" :cssCode="cssCode" :jsCode="jsCode"></Preview>
    </section>
    <div class="l-html">
      <HTMLEditor v-on:code-change="onHTMLCodeChange"></HTMLEditor>
    </div>
    <div class="l-css">
      <CSSEditor v-on:code-change="onCSSCodeChange"></CSSEditor>
    </div>
    <div class="l-js">
      <JSEditor v-on:code-change="onJSCodeChange"></JSEditor>
    </div>
  </div>
</template>

<script>
import Preview from "@/components/Preview.vue";
import HTMLEditor from "@/components/HTMLEditor.vue";
import CSSEditor from "@/components/CSSEditor.vue";
import JSEditor from "@/components/JSEditor.vue";

export default {
  components: {
    Preview,
    HTMLEditor,
    CSSEditor,
    JSEditor
  },
  data() {
    return {
      htmlCode: "",
      cssCode: "",
      jsCode: ""
    };
  },
  methods: {
    onHTMLCodeChange: function(newCode) {
      this.htmlCode = newCode;
    },
    onCSSCodeChange: function(newCode) {
      this.cssCode = newCode;
    },
    onJSCodeChange: function(newCode) {
      this.jsCode = newCode;
    }
  }
};
</script>

<style>
:root {
  box-sizing: border-box;
}

*,
::before,
::after {
  box-sizing: inherit;
}

body {
  margin: 0;
  overflow: hidden;
}

#app {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

.grid-container {
  display: grid;
  height: 100vh;
  grid-gap: 0.5em;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 1fr 1fr;
  grid-template-areas: "preview preview preview" "html css js";
}

.l-preview {
  grid-area: preview;
}

.l-html {
  grid-area: html;
}

.l-css {
  grid-area: css;
}

.l-js {
  grid-area: js;
}
</style>
