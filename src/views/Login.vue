<template>
    <div class="d-flex justify-center">
        <v-card width="600px" class="mt-12 pa-10">
            <v-card-title>
                Войдите в аккаунт
            </v-card-title>

            <v-text-field
                label="Введите логин"
                v-model="login"
                outlined
            ></v-text-field>

            <v-text-field
                label="Введите пароль"
                v-model="password"
                outlined
            ></v-text-field>

            <v-btn @click="authenticate">
                Войти
            </v-btn>
        </v-card>
    </div>
</template>

<script>
export default {
  data(){
    return{
      login: undefined,
      password: undefined,
      storage: ''
    }
  },
  methods:{
    authenticate(){
      this.axios.get('http://37.77.104.246/api/jsonstorage/?id=f6ca63f90e97bf85985773662b30c9a8')
        .then(response => {
          let users = response.data;
          let found = false;
          let user;
          for (let index in users){
            if(this.login == users[index].login && this.password == users[index].password){
              this.$router.push('/users/' + this.myId);
              found = true;
              user = response.users[index];
              break;
            }
          }

          if(found){
            this.$$emit('auth', user)
          }else{
            window.alert('Неверный логин и пароль');
          }
        })
    }
  }
  
}
</script>
