<template>
    <codemirror ref="jsEditor"
                v-model="jsCode"
                :options="jsOptions"
                @ready="onCmReady"
                @focus="onCmFocus"
                @input="onCmCodeChange">
      </codemirror>
</template>

<script>
import { codemirror } from "vue-codemirror";
import "codemirror/mode/javascript/javascript.js";
import "codemirror/theme/base16-dark.css";
import "codemirror/lib/codemirror.css";

export default {
  components: {
    codemirror
  },
  data() {
    return {
      jsCode: `var hello = document.querySelector("h1");
hello.innerHTML += " with JS! <span>❤</span>";`,
      jsOptions: {
        tabSize: 4,
        mode: "text/javascript",
        theme: "base16-dark",
        lineNumbers: true,
        line: true
      }
    };
  },
  methods: {
    onCmReady(cm) {
      console.log("the editor is readied!", cm);
      this.$emit("code-change", this.jsCode);
    },
    onCmFocus(cm) {
      console.log("the editor is focus!", cm);
    },
    onCmCodeChange(newCode) {
      console.log("this is new code", newCode);
      this.$emit("code-change", newCode);
    }
  }
};
</script>

