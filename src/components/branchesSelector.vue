<template>
  <div class="branchesSelector">
    <div class="branchSelector" v-for="branch in branches" :key="branch.name">
      <input type="radio" name="branch" :value="branch.name" v-model="branchSelected" @change="$emit('selectBranch', branch)"> {{branch.name}}
      {{branchSelected}}
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "branchesSelector",
  props: ["repoData"],
  data() {
    return {
      urlBase: "https://api.github.com/",
      branches: [],
      branchSelected: ''
    };
  },
  created() {
    axios
      // .get(`${this.urlBase}repos/Nixyn/list-items/branches`)
      .get(`${this.urlBase}repos/${this.repoData.owner}/${this.repoData.repo}/branches`)
      .then(branches => this.branches = branches.data)
      .catch(err => console.error(err));
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
