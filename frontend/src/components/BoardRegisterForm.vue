<template>
  <form @submit.prevent="onSubmit">
    <h3>Board Register Form</h3>
    <form>
      <v-col cols="12" md="5"><v-text-field
      type="text"
      v-model="title"
      label="title"
      required
      ></v-text-field></v-col>
      <v-col cols="12" md="5"><v-text-field
      type="text"
      v-model="writer"
      label="writer"
      required
      ></v-text-field></v-col>
      <v-col cols="12" md="5" rows="7"><v-text-field
      type="text"
      v-model="content"
      label="content"
      required
      ></v-text-field></v-col>
    </form>

    <div>
      <v-btn depressed color="primary" type="submit">Register</v-btn>
      <router-link :to="{ name: 'Bank' }">
        Cancel
      </router-link>
    </div>
  </form>
</template>

<script>
export default {
  name: 'BoardRegisterForm',
  data () {
    return {
      title: '',
      writer: '',
      content: ''
    }
  },
  methods: {
    onSubmit () {
      const { title, writer, content } = this
      this.$emit('submit', { title, writer, content })
    }
  }
}
</script>
