<template>
  <div class="recursive-nested-collapse">
    <b-button
      v-b-toggle="componentID"
      variant="primary"
      class="d-flex align-items-center"
      block
    >
      <span
        ><b>{{ name }}</b></span
      >
    </b-button>

    <!-- Rendered After Click -->
    <b-collapse :id="componentID">
      <div v-if="isNotLastPath()">
        <recursive-tab
          v-for="child in children"
          :name="child.name"
          :data="child"
          :key="child.name"
          :paths="childPaths"
        />
      </div>

      <div v-else>
        <div v-for="child in children">
          <b-card>
            <div
              class="d-flex justify-content-between align-items-center flex-row flex-wrap"
            >
              <span>{{ child.name }}</span>
            </div>
          </b-card>
        </div>
      </div>
    </b-collapse>
  </div>
</template>

<script>

export default {
  name: "RecursiveTab",
  props: {
    name: String,
    data: Object,
    paths: Array
  },
  data() {
    return {
      drawerIsSelected: false,
    };
  },
  computed: {
    pathItem() {
      return ;
    },
    children() {
      return this.data[this.paths[0]];
    },
    childPaths() {
      return this.paths.slice(1);
    },
    componentID() {
      let id = this.name.replace(/ /g,'')
      return `${id}`;
    }
  },
  methods: {
    isNotLastPath() {
      return this.paths.length > 1;
    }
  }
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
  margin: 5px 15px 5px 15px;
}

.btn:hover,
button:hover {
  cursor: pointer;
}
</style>
