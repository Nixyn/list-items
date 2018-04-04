<template>
  <div id="app">
    <img src="./assets/logo.png">
    <branchesSelector :repoData="repoData" @selectBranch="getCommits"/>
  </div>
</template>

<script>
import axios from "axios";

import branchesSelector from './components/branchesSelector';

export default {
  name: 'App',
  components: {
    branchesSelector,
  },
  data(){
    return{
      repoData: {
        owner: 'Nixyn',
        repo: 'list-items'
      },
      commits: []
    }
  },
  methods:{
    getCommits(branch){
      let commitsUrl = branch.commit.url;
      alert();
      axios.get(commitsUrl)
      .then(commits =>console.log('inCommits', commits))
      .catch(err => console.error(err));
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
