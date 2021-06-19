<template>

<div>
    <div class="containerBusca" id="busca">

        <h1>Github <span>Search</span></h1>
        <form class="form-container">
            <input id="search" type="text" class="form-busca" @keyup="getUsers" required>
            <button id="button">
                <img src='../assets/search.svg'/>
            </button>
        </form>

    </div>

    <div>
        <div class="containerResultado mt-3">
            <div>
                 <Resultado :user="user" />
            </div>

            <div class="col-md-8" style="width: 75%">
                <Repo v-for="repo in repos" :key="repo" :repo="repo" />
            </div>

        </div>
    </div>
</div>
</template>

<script>

import Resultado from '../components/Resultado.vue'
import Repo from '../components/Repo.vue'

import axios from 'axios';

export default {
    components: { 
        Resultado, 
        Repo
    },
    data() {
    return {
      github: {
        url: "https://api.github.com/users",
        client_id: "4780645eb36854704b1e", 
        client_secret: "39928741d3fa896a933296e3337d2af1c7bc9d69",
        count: 6,
        sort: "created: desc"
      },
      user: [],
      repos: [],
    }
  },

  methods: {
      getUsers(e){
          const user = e.target.value;
          const { url, client_id, client_secret, count, sort } = this.github;
          
          axios.get(`${url}/${user}?client_id=${client_id}&client_secret=${client_secret}`
          ).then(({ data }) => this.user = data);

          axios.get(`${url}/${user}/repos?per_page=${count}&sort=${sort}&client_id=${client_id}
          &client_secret=${client_secret}`
          ).then(({ data }) => this.repos = data);
    },
  },
};
</script>
<style>
.containerBusca {
    display: flex;
    flex-direction: row; 
    justify-content: space-between;
    align-items: center;
    margin-top: 30px;
    margin-right: 30px;
    margin-left: 30px;
}
.containerBusca span{
    font-style: italic;
}
.form-container{
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
}

.form-busca {
    width: 400px;
    height: 30px;
    border-color: black;
    border-radius: none;
}

#button {
    background-color: black;
    color: white;
    border: none;
    width: 55px;
    height: 30px;
}
span {
    font-weight: normal;
    color: black;
}
.containerResultado{
    display: flex;
    flex-direction: row;
    align-items: center;
    padding-left: 50px;
    justify-content: space-around; 
    width: 100% 
}
</style>