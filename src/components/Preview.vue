<template>
    <div>
      <iframe class="preview" ref="preview"></iframe>
    </div>
</template>

<script>
export default {
  props: {
    htmlCode: String,
    cssCode: String,
    jsCode: String
  },
  computed: {
    renderedHTML: function() {
      return `
        ${this.htmlCode}
        <style>${this.cssCode}</style>
        <script>${this.jsCode}<\/script>
      `;
    }
  },
  watch: {
    renderedHTML: function(val) {
      var iframeComponent = this.$refs.preview.contentWindow.document;
      iframeComponent.open();
      iframeComponent.writeln(val);
      iframeComponent.close();
    }
  }
};
</script>

<style scoped>
.preview {
  width: 100%;
  border: none;
}
</style>
