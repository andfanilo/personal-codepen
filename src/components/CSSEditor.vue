<template>
    <codemirror ref="cssEditor"
                v-model="cssCode"
                :options="cssOptions"
                @ready="onCmReady"
                @focus="onCmFocus"
                @input="onCmCodeChange">
      </codemirror>
</template>

<script>
import { codemirror } from "vue-codemirror";
import "codemirror/mode/css/css.js";
import "codemirror/theme/paraiso-light.css";
import "codemirror/addon/selection/active-line.js";

export default {
  components: {
    codemirror
  },
  data() {
    return {
      cssCode: `body {
  align-items: center;
  background: #f8c555;
  display: flex;
  justify-content: center;
}

h1 {
  color: white;
  font-size: 72px;
}

span {
  color: red;
  font-size: 80px;
}`,
      cssOptions: {
        tabSize: 4,
        styleActiveLine: true,
        lineNumbers: true,
        line: true,
        mode: "text/css",
        theme: "paraiso-light"
      }
    };
  },
  methods: {
    onCmReady(cm) {
      console.log("the editor is readied!", cm);
      this.$emit("code-change", this.cssCode);
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

