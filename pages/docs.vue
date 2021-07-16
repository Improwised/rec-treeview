<template>
  <div class="container">
    <div id="doc">
      <div v-html="docs.html"></div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ params }) {
    try {
      console.info(params.slug);
      let docs = await import(`~/content/docs.md`);
      return {
        docs,
      };
    } catch (err) {
      console.debug(err);
      return false;
    }
  },
};
</script>
<style>
#doc {
  display: block;
}
.container {
  color: #000306;
  margin-top: 60px;
}
pre {
  background-color: black;
  padding: 2rem;
  color: #00c785;
}
</style>
