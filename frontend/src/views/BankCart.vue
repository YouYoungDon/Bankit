<template>
  <BankCartLayout>
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
    <template #content>
      <v-simple-table>
        <template v-slot:default>
          <thead>
            <tr>
              <th class="text-left">List</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="list of checkedCards" :key="list">
              <td><a @click="clickNews(list)">{{ list }}</a></td>
            </tr>
          </tbody>
        </template>
      </v-simple-table>
    </template>
  </BankCartLayout>
</template>
<script>
/* eslint-disable no-unused-vars */
import BankCartLayout from '../components/BankCartLayout'
import { mapState, mapGetters, mapActions } from 'vuex'
import axios from 'axios'
import BoardListPageForm from '@/components/BoardListPageForm.vue'

export default {
  components: { BankCartLayout },
  computed: {
    ...mapState(['myinfo'], ['checkedCards']),
    ...mapGetters(['isAuthorized'], ['checkedCards']),
    ...mapState({
      checkedCards: state => state.checkedCards
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
