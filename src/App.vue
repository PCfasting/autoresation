<template>
  <v-content>
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link v-if="user == ''" to="/login">Вход</router-link>
      <router-link v-else :to="'/user/' + user.login">{{ user.name }}</router-link> | 
      <router-link to="/registration">Регистрация</router-link>
    </div>
    <v-container fluid>
      <router-view v-bind:value="user" @auth="authStart" />
    </v-container>
  </v-content>
</template>

<script>
export default {
  data(){
    return{
      user: ''
    }
  },
  methods: {
    authStart($data) {
      this.user = $data;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
