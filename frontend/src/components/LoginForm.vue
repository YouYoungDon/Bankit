<template align="center">
  <v-app id="inspire"><br>
    <h1 class="font-weight-light">Login</h1>
    <form @submit.prevent="submit">
      <v-col cols="12" md="2"><v-text-field
      type="text"
      v-model="userid"
      label="ID"
      required
      ></v-text-field></v-col>
      <v-col cols="12" md="2"><v-text-field
      type="text"
      v-model="password"
      label="Password"
      required
      ></v-text-field></v-col>
      <v-btn
       type="submit"
       color="red"
       class="mr-4"
      >
       Login</v-btn>
       <router-link :to="{ name: 'Bank' }">
         Cancel
       </router-link>
    </form>
  </v-app>
</template>

<script>
export default {
  name: 'LoginForm',
  data () {
    return {
      userid: '',
      password: ''
    }
  },
  methods: {
    submit () {
      console.log('LoginForm submit()')
      const { userid, password } = this
      this.$emit('submit', { userid, password })
    }
  }
}
</script>
