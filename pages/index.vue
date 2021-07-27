<template>
  <div class="container">
    <logo />
    <h1 class="mb-5">Recursive Component Example</h1>
    <b-row>
      <b-col>
        <v-jsoneditor
          v-model="recipes"
          :plus="false"
          height="30rem"
        />
      </b-col>
      <b-col>
        <recursive-tab :name="recipes.name" :recipes="recipes" />
      </b-col>
    </b-row>
  </div>
</template>

<script>
import json from "@/data/data.json";

export default {
  data() {
    return {
      recipes: json.recipes
    };
  },
};
</script>

<style>
.container {
  text-align: center;
  color: #000306;
  margin-top: 60px;
  margin-bottom: 80px;
}
</style>
