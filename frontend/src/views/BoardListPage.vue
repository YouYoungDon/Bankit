<template>
  <v-app id="inspire">
    <div id="board">
      <h2>Board List</h2>
      <router-link :to="{ name: 'BoardRegisterPage' }">
        Create New Board
      </router-link>
      <board-list :boards="boards"/>
    </div>
  </v-app>
</template>

<script>
import BoardList from '@/components/BoardList'
import { mapState, mapActions } from 'vuex'

export default {
  name: 'BoardListPage',
  components: {
    BoardList
  },
  computed: {
    ...mapState(['boards'])
  },
  mounted () {
    this.fetchBoardList()
  },
  methods: {
    ...mapActions(['fetchBoardList'])
  }
}

</script>
