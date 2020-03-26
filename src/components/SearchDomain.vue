<template>
  <div id="SearchDomain" class="container">
    <h1>{{ msg }}</h1>
    <form id="form">
      <div class="form-group mt-3">
        <label class="mt-5" for="domainInput">Domain</label>
        <input type="text" class="form-control mt-5" id="domainInput" v-model="input" placeholder="Enter domain">
        <span id="emailHelp" class="form-text text-muted mt-5">Search truora.com and see what happens</span >
      </div>
      <button type="button" class="btn btn-success mt-5" v-on:click="getDomainData" >Diagnose</button>
    </form>
   <p v-if="loading">Loading...</p>
    <div v-else class="mt-5"> 
        <h4>
          {{all_users}}
        </h4>
    </div>
    <div>
        <button type="button" class="btn btn-success mt-5" v-on:click="getSearchList" >List all searchs</button>
        <div class="mt-5">
          <h5>
            {{all_searchs}}
          </h5>
        </div>
    </div>
    </div>

</template>

<script>
const axios = require('axios');

export default {
  name: 'SearchDomain',
  data () {
    return {
      loading: false,
      all_users: null,
      all_searchs: null,
      input:null
    }
  },
    methods: {
    getDomainData: function () {      
      if (this.input != null) {
        this.loading = true;
        axios
          .get('http://localhost:8082/' + this.input)
          .then(response => (this.all_users = response.data))
          .catch(error => console.log(error))
          .finally(() => this.loading = false)
      }
    },
        getSearchList: function () {
        this.loading = true;
        axios
          .get('http://localhost:8082/searchs')
          .then(response => (this.all_searchs = response.data))
          .catch(error => console.log(error))
          .finally(() => this.loading = false)
    }
  },
  props: {
    msg: String,
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
</style>
