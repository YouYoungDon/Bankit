<template>
  <v-app id="inspire">
    <div align="center">
      <h2>Board Modification</h2>
      <board-modify-form v-if="board" :board="board" @submit="onSubmit"/>
      <p v-else>Loading ...</p>
    </div>
  </v-app>
</template>

<script>
import BoardModifyForm from '@/components/BoardModifyForm'
import { mapState, mapActions } from 'vuex'
import axios from 'axios'

export default {
  name: 'BoardModifyPage',
  components: {
    BoardModifyForm
  },
  props: {
    boardNo: {
      type: String,
      required: true
    }
  },
  computed: {
    ...mapState(['board'])
  },
  created () {
    console.log('BoardModifyPage created()')
    this.fetchBoard(this.boardNo)
      .catch(err => {
        alert(err.response.data.message)
        this.$router.back()
      })
  },
  methods: {
    onSubmit (payload) {
      const { title, content } = payload
      console.log('BoardModifyPage payload: ' + payload)
      axios.put(`http://localhost:7777/boards/${this.boardNo}`, { title, content })
        .then(res => {
          alert('Modify Success')
          console.log('res: ' + res.data)
          this.$router.push({
            name: 'Bank',
            params: { boardNo: res.data.boardNo.toString() }
          })
        })
        .catch(err => {
          alert(err.response.data.message)
        })
    },
    ...mapActions([
      'fetchBoard'
    ])
  }
}
</script>
