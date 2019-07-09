<template>
  <div>
    <h1>Register</h1>
    <input
        type="email"
        name="email"
        v-model="email"
        placeholder="Enter email"/>
    <br>
    <input
        type="password"
        name="password"
        v-model="password"
        placeholder="Enter password"/>
    <br>
    <button
    @click="register">Register</button>
  </div>
</template>

<script>

import AuthenticationService from '@/services/AuthenticationService'

export default {
  data () {
    return {
        email: 'abc',
        password: 'mypassword'
    }
  },
  watch: {
      email() {
          console.log('Email has changed')
      },
      password() {
          console.log('Password has changed')
      }
  },

  mounted () {
      setTimeout(() => {
          this.email = "I'm back bitch"
      }, 2000)
  },

  methods: {
      async register () {
          const response = await AuthenticationService.register({
              email: this.email,
              password: this.password
          })
      }
  }
}
</script>

<style scoped>
</style>
