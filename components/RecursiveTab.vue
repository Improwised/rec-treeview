<template>
  <div class="recursive-nested-collapse">
    <div v-for="recipe in recipes" :key="recipe.name">
      <div v-if="recipe.name">
        <span class="d-flex mt-2 align-items-center"
          ><b v-if="!start" class="branch "></b
          ><b-icon
            :icon="close"
            v-if="recipe.children"
            v-b-toggle="componentID(recipe.name)"
            variant="success"
          ></b-icon>
          <b>{{ recipe.name }}</b></span
        >
        <b-collapse style="margin-left: 0.4rem;" :id="componentID(recipe.name)">
          <div
            style="border-left:rgb(59, 126, 185) solid;margin-top: -0.4rem;
padding-top: 4px;"
            v-if="recipe.children"
          >
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
  data() {
    return {
      open: "dash-circle-fill",
      close: "plus-circle-fill",
    };
  },
  props: {
    recipes: { type: Array, default: {} },
    start: { type: Boolean, default: false },
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
.branch {
  content: "";
  display: block;
  width: 3rem;
  border-top: 3px solid rgb(59, 126, 185);
  margin-top: -2px;
  position: absolute;
  margin-left: -3rem;
  margin-top: -1px;
}
</style>
