<template>
<div class="container">
<div id="doc">
  <div v-html="readme"></div>
  </div>
  </div>
</template>

<script>
  import readme from '@/static/README.md'

  export default {
    computed: {
      readme() {
        return readme
      }
    }
  }
</script>
<style>
#doc{
    display: block;
}.container {
  color: #000306;
  margin-top: 60px;
}
pre {
    background-color: black;
    padding: 2rem;
    color: #00c785;
}
</style>