<template>
  <div id="app">
    <img src="./assets/logo.png">
    <branchesSelector :repoData="repoData" @selectBranch="getRepoInfo"/>
    <list :info="repoData"/>
  </div>
</template>

<script>
import axios from "axios";

import branchesSelector from "./components/branchesSelector";
import list from "./components/list";

export default {
  name: "App",
  components: {
    branchesSelector,
    list
  },
  data() {
    return {
      repoData: {
        owner: "Nixyn",
        repo: "list-items",
        sha: ""
      },
      repoToGetCommits: {}
    };
  },
  methods: {
    getRepoInfo(branch) {
      this.repoData.sha = branch.commit.sha;
      console.log(this.repoData);
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
