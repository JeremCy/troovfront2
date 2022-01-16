<template>
    <div class="px-4 pt-6 mx-auto text-white lg:w-4/12 center">
      <div
        class="relative flex flex-col w-full min-w-0 mb-6 break-words border-0 rounded-lg shadow-lg bg-[#466060]"
      >
        <div class="flex-auto px-4 py-10 pt-0 space-y-4 lg:px-10">
          <h1 class="mt-4 mb-3 text-4xl font-bold text-center">Sign up</h1>
          <b-notification v-if="error" type="is-warning">
            {{ error }}
          </b-notification>
          <form @submit.prevent="userSignUp">
            <div class="relative w-full mb-3">
              <label
                class="block mb-2 text-xs font-bold uppercase text-blueGray-600"
                for="grid-password"
                >Username</label
              ><input
                id="username"
                type="text"
                class="w-full px-3 py-3 text-sm transition-all duration-150 ease-linear bg-white border-0 rounded shadow text-slate-800 placeholder-blueGray-300 focus:outline-none focus:ring"
                placeholder="Username"
                v-model="username"
              />
            </div>
            <div class="relative w-full mb-3">
              <label
                class="block mb-2 text-xs font-bold uppercase text-blueGray-600"
                for="grid-password"
                >Email</label
              >
              <input
                id="Email"
                type="text"
                class="w-full px-3 py-3 text-sm transition-all duration-150 ease-linear bg-white border-0 rounded shadow text-slate-800 placeholder-blueGray-300 text-blueGray-600 focus:outline-none focus:ring"
                placeholder="Email"
                v-model="email"
              />
            </div>
            <div class="relative w-full mb-3">
              <label
                class="block mb-2 text-xs font-bold uppercase text-blueGray-600"
                for="grid-password"
                >Password</label
              ><input
                id="password"
                type="password"
                class="w-full px-3 py-3 text-sm transition-all duration-150 ease-linear bg-white border-0 rounded shadow text-slate-800 placeholder-blueGray-300 text-blueGray-600 focus:outline-none focus:ring"
                placeholder="Password"
                v-model="password"
              />
              <input
                id="password_comfirm"
                type="password"
                class="w-full px-3 py-3 mt-6 text-sm transition-all duration-150 ease-linear bg-white border-0 rounded shadow text-slate-800 placeholder-blueGray-300 text-blueGray-600 focus:outline-none focus:ring"
                placeholder="Re-enter Password"
                v-model="password_confirm"
              />
            </div>
            <div class="mt-6 text-center">
              <button
                class="w-full px-6 py-3 mb-1 mr-1 text-sm font-bold text-white uppercase transition-all duration-150 ease-linear rounded shadow outline-none bg-slate-800 active:bg-blueGray-600 hover:shadow-lg focus:outline-none"
                type="submit"
              >
                Sign In
              </button>
              <nuxt-link to="/auth/signin"
                >Already have a account? Signin</nuxt-link
              >
            </div>
          </form>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  auth: false,
  data() {
    return {
      username: '',
      email: '',
      password: '',
      password_confirm: '',
      error: '',
    }
  },
  methods: {
    async userSignUp() {
      if (this.password === this.password_confirm) {
        try {
          await this.$axios.$post('/auth/signup', {
            username: this.username,
            email: this.email,
            password: this.password,
          })
          await this.$auth.logginWith('local', {
            username: this.username,
            password: this.password,
          })
          this.$router.push('/')
        } catch (e) {
          this.error = e.response.data.message
        }
      }else{
          this.error = 'Le mot de passe de correspond pas'
      }
    },
  },
}
</script>

<style>

</style>