<template>
  <BankLayout>
    <div align="center">
      <login-form @submit="onSubmit"/>
    </div>
  </BankLayout>
</template>

<script>
/* eslint-disable no-unused-vars */
import BankLayout from '../components/BankLayout'
import LoginForm from '@/components/LoginForm.vue'
import { mapActions } from 'vuex'

export default {
  name: 'LoginPage',
  components: {
    LoginForm
  },
  methods: {
    onSubmit (payload) {
      console.log('loginPage onSubmit()')
      this.login(payload).then(res => {
        alert('Login Success')
        this.$router.push({ name: 'Bank' })
      }).catch(err => {
        // alert(err.response.data.message)
        alert('Something Fail: ', err)
      })
    },
    ...mapActions(['login'])
  }
}
</script>
