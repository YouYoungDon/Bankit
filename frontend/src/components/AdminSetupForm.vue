<template>
  <v-app id="inspire"><br>
    <h1 class="font-weight-light">Sign up</h1>
    <form @submit.prevent="submit">
      <justify-center>
        <v-col cols="12" md="2"><v-text-field
        type="text"
        v-model="userId"
        label="ID"
        required
        ></v-text-field></v-col>
        <v-col cols="12" md="2"><v-text-field
        type="text"
        v-model="userPw"
        label="Password"
        required
        ></v-text-field></v-col>
        <v-col cols="12" md="2"><v-text-field
        type="text"
        v-model="userName"
        label="Admin Name"
        required
        ></v-text-field></v-col>
        <v-btn
          color="error"
          class="mr-4"
          @click="reset"
          type="submit"
        >
          Register
        </v-btn>
        <router-link :to="{ name: 'Bank' }">
          Cancel
        </router-link>
      </justify-center>

      <div>

      </div>
    </form>
  </v-app>
</template>

<script>
export default {
  name: 'AdminSetupForm',
  data () {
    return {
      userId: '',
      userName: '',
      userPw: ''
    }
  },
  methods: {
    submit () {
      console.log('this: ' + this.userId +
                  ', ' + this.userName +
                  ', ' + this.userPw)
      const { userId, userName, userPw } = this
      this.$emit('submit', { userId, userName, userPw })
    }
  }
}
</script>
