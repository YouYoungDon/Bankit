<template>
  <BankLayout>
    <template #menubar>
      <div id="header" v-if="isAuthorized">
        <button id="login" @click="onClickLogout"><v-icon>mdi-exit-to-app</v-icon></button>
      </div>
      <div id="header" v-else>
        <button id="login" @click="$router.push('LoginPage')">
          <v-icon>mdi-account</v-icon>
        </button>
        <h1></h1>
        <button id="login" @click="$router.push('AdminSetupPage')">
          <v-icon>mdi-account-edit</v-icon>
        </button>
      </div>
    </template>
  </BankLayout>
</template>
<script>
/* eslint-disable no-unused-vars */
import BankLayout from '../components/BankLayout'
import { mapState, mapGetters, mapActions } from 'vuex'
import axios from 'axios'
import BoardListPageForm from '@/components/BoardListPageForm.vue'

export default {
  components: { BankLayout },
  computed: {
    ...mapState(['myinfo']),
    ...mapGetters(['isAuthorized']),
    ...mapState({
      lists: state => state.lists
    })
  },
  methods: {
    onClickLogout () {
      this.logout()
      alert('Success Logout')
      this.$router.push({ name: 'Bank' })
    },
    ...mapActions(['logout'])
  }
}
</script>
