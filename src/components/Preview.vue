<template>
    <div>
       {{ renderedHTML }}
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
  }
};
</script>
