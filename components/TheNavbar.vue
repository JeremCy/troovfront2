<template>
    <nav
      class="flex items-center justify-center p-4 bg-white drop-shadow-xl"
    >
      <span class="flex-grow hidden text-base lg:block title 2xl:text-2xl"
        >Jérémie CYRILLE</span
      >
      <div class="flex space-x-4 text-base 2xl:text-2xl text-[#16C172]">
        <button class="flex items-center hover:text-slate-900">
          <nuxt-link to="/">Browse</nuxt-link>
        </button>
        <button class="flex items-center hover:text-slate-900">
          <nuxt-link to="/carrer">About</nuxt-link>
        </button>
        <button class="flex items-center hover:text-slate-900">
          <nuxt-link to="/project">Contact</nuxt-link>
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

</script>

<style>
</style>