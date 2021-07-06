<template>
  <div class="container">
    <logo />
    <h1>Recursive Component Example</h1>
    <br />

    <recursive-tab
      v-for="recipe in recipes"
      :name="recipe.name"
      :data="recipe"
      :key="recipe.name"
      :paths="['parent', 'children', 'grandchildren']"
    />
  </div>
</template>

<script>
import RecursiveTab from "@/components/RecursiveTab";
import json from "@/data/data.json";

export default {
  computed: {
    recipes() {
      return json.recipes;
    }
  }
};
</script>

<style>
.container {
  text-align: center;
  color: #000306;
  margin-top: 60px;
}
</style>
