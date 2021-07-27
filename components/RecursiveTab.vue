<template>
  <div class="recursive-nested-collapse">
    <div v-for="recipe in recipes" :key="recipe.name">
      <div v-if="recipe.name">
        <b-button
          pill
          v-b-toggle="componentID(recipe.name)"
          variant="outline-primary"
          class="d-flex mt-2 align-items-center"
          block
        >
          <span
            ><b>{{ recipe.name }}</b></span
          >
        </b-button>
        <b-collapse :id="componentID(recipe.name)">
          <div v-if="recipe.children">
            <recursive-tab :recipes="recipe.children" />
          </div>
        </b-collapse>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "RecursiveTab",
  props: {
    recipes: Array,
  },
  methods: {
    componentID(name) {
      return name.replace(/ /g, "");
    },
  },
};
</script>

<style>
h1,
h2 {
  font-weight: normal;
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

.row {
  margin: 0 !important;
}

.recursive-nested-collapse {
  margin: 5px 0px 0px 3rem;
}

.btn:hover,
button:hover {
  cursor: pointer;
}
</style>
