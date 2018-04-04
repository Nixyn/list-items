<template>
  <div class="list">
    <h1>Lista de cosas por hacer</h1>
    <h2> Repositorio de {{info.owner}}: {{ info.repo }} @ {{ info.branch }} </h2>
    <ul>
        <li v-for="commit in commits"><commititem :commit="commit"/></li>
    </ul>
  </div>
</template>
<script>
import commititem from './commit-item';
import axios from 'axios';
export default {
  name: 'list',
  props: ['info'],
  data() {
    return {
        commits:[{
          id:'0',
          name: 'christi',
          user: 'cris0',
          date: Date.now()
        }]
    }
  },
  watch: {
      'info.sha': function () {
          console.log('info: ',this.info);
          
            this.commits=[];
            axios
            .get(`https://api.github.com/repos/${this.info.owner}/${this.info.repo}/commits?sha=${this.info.sha}`)
            .then(commits => {
                
                
                commits.data.forEach(element => {
                    var objetito = {
                        name:element.message,
                        user:element.author,
                        id: element.sha,
                        date: element.commit.author.date
                    }
                    this.commits.push(objetito);
                });
                console.log('commits',this.commits);
            })
            .catch(err => console.error(err));
      }
  },
  components: {
    commititem,
  }
}
</script>
<style>
</style>