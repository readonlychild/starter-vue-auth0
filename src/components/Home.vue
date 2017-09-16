<template>
  <div>
    <h4 v-if="authenticated">
        You are logged in! <strong>{{ profile.name }}</strong> <br/><br/>
        <img :src="profile.picture" />
    </h4>
    <h4 v-if="!authenticated">
      You are not logged in! Please <a @click="auth.login()">Log In</a> to continue.
    </h4>
  </div>
</template>

<script>
  export default {
    name: 'home',
    props: ['auth', 'authenticated'],
    computed: {
      profile () {
        return JSON.parse(localStorage.getItem('profile'))
      }
    },
    mounted () {
      try {
        this.auth.handleAuthentication()
      } catch (ex) { }
    }
  }
</script>

<style>
  a {
    cursor: pointer;
  }
</style>

