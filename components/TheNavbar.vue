<template>
  <nav class="flex items-center justify-center p-4 bg-white drop-shadow-xl">
    <div class="flex-grow">
      <img
        src="/logo-dark.png"
        alt="Troov"
        srcset=""
        class="hidden lg:block h-6"
      />
    </div>
    <div class="flex space-x-4 text-base 2xl:text-2xl text-[#16C172]">
      <button class="flex items-center hover:text-slate-900">
        <nuxt-link to="/">Home</nuxt-link>
      </button>
      <button class="flex items-center hover:text-slate-900">
        <nuxt-link to="/object">Browse</nuxt-link>
      </button>
      <button class="flex items-center hover:text-slate-900">
        <nuxt-link to="/object/add">Add lost item</nuxt-link>
      </button>
      <div v-if="$auth.loggedIn" class="space-x-4">
        <span class="navbar-item">
          {{ loggedInUser.username }}
        </span>
        <a class="navbar-item" @click="logout">Déconnexion</a>
      </div>
      <div v-else class="space-x-4">
        <nuxt-link class="navbar-item" to="/auth/signin">Connexion</nuxt-link>
        <nuxt-link class="navbar-item" to="/auth/signup">Inscription</nuxt-link>
      </div>
    </div>
  </nav>
</template>

  <script>
export default {
  methods: {
    async logout() {
      await this.$auth.logout() // this method will logout the user and make token to false on the local storage of the user browser
    },
  },
  computed: {
    isAuthenticated() {
      return this.$store.getters.isAuthenticated // it check if user isAuthenticated
    },
  },
}
</script>