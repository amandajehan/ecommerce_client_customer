<template>
  <div id="app">
    <div id="sidenav">
      <img
        src="./assets/duck.jpg"
        alt="logo"
        style="width: 100px; margin-top: 15px"
      />
      <h1 style="font-size: 26px; background-color: #f7d794; margin-top: 0px; text-align: center; font-family: Assistant">Bookoo Shop</h1>
      <div class="nav-links">
        <router-link
          class="nav-icon"
          to="/"
          uk-icon="icon: home; ratio: 1.5"
          uk-tooltip="title: Home; pos: right; delay: 150"
        ></router-link>
        <router-link
          class="nav-icon"
          to="/cart"
          uk-icon="icon: cart; ratio: 1.5"
          uk-tooltip="title: Shopping Cart; pos: right; delay: 150"
        ></router-link>
        <router-link
          v-if="loginStatus"
          class="nav-icon"
          to="/purchase-history"
          uk-icon="icon: history; ratio: 1.5"
          uk-tooltip="title: Purchase History; pos: right; delay: 150"
        ></router-link>
        <router-link
          v-if="!loginStatus"
          class="nav-icon"
          to="/login"
          uk-icon="icon: sign-in; ratio: 1.5"
          uk-tooltip="title: Login; pos: right; delay: 150"
        ></router-link>
        <button
          @click="logout"
          v-if="loginStatus"
          class="nav-icon"
          to="/"
          uk-icon="icon: sign-out; ratio: 1.5"
          uk-tooltip="title: Logout; pos: right"
        ></button>
      </div>
    </div>
    <router-view />
  </div>
</template>

<script>
export default {
  name: 'App',
  computed: {
    loginStatus () {
      return this.$store.state.loginStatus
    }
  },
  methods: {
    logout () {
      localStorage.clear()
      console.log('user is logged out now')
      this.$store.commit('setLoginStatus', false)
      this.$router.push({ name: 'Login' })
    }
  }
}
</script>
