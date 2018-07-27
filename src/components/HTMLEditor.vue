<template>
    <codemirror ref="htmlEditor"
                v-model="htmlCode"
                :options="htmlOptions"
                @ready="onCmReady"
                @focus="onCmFocus"
                @input="onCmCodeChange">
      </codemirror>
</template>

<script>
import { codemirror } from "vue-codemirror";
import "codemirror/mode/xml/xml.js";
import "codemirror/theme/ambiance.css";
import "codemirror/addon/selection/active-line.js";
import "codemirror/addon/edit/closetag.js";

export default {
  components: {
    codemirror
  },
  data() {
    return {
      htmlCode: `<h1>Hello world</h1>`,
      htmlOptions: {
        tabSize: 4,
        styleActiveLine: true,
        lineNumbers: true,
        autoCloseTags: true,
        line: true,
        mode: "text/html",
        theme: "ambiance"
      }
    };
  },
  methods: {
    onCmReady(cm) {
      console.log("the editor is readied!", cm);
      this.$emit("code-change", this.htmlCode);
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

