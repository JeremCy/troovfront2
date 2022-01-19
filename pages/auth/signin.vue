<template>
    <div class="w-full px-4 pt-6 mx-auto text-white lg:w-4/12 center">
      <div
        class="relative flex flex-col w-full min-w-0 mb-6 break-words border-0 rounded-lg shadow-lg bg-[#466060]"
      >
        <div class="flex-auto px-4 py-10 pt-0 lg:px-10">
          <h1 class="mt-4 mb-3 text-4xl font-bold text-center">Sign in</h1>
          <b-notification v-if="error" type="is-warning">
            {{ error }}
          </b-notification>
          <form @submit.prevent="userSignIn">
            <div class="relative w-full mb-3">
              <label
                class="block mb-2 text-xs font-bold uppercase"
                for="grid-password"
                >Username</label
              ><input
                id="username"
                type="text"
                class="w-full px-3 py-3 text-sm transition-all duration-150 ease-linear bg-white border-0 rounded shadow placeholder-slate-500  focus:outline-none focus:ring text-slate-800"
                placeholder="Username"
                v-model="user.username"
              />
            </div>
            <div class="relative w-full mb-3">
              <label
                class="block mb-2 text-xs font-bold uppercase"
                for="grid-password"
                >Password</label
              ><input
                id="password"
                type="password"
                class="w-full px-3 py-3 text-sm transition-all duration-150 ease-linear bg-white border-0 rounded shadow placeholder-slate-500 text-slate-800 focus:outline-none focus:ring"
                placeholder="Password"
                v-model="user.password"
              />
            </div>
            <div class="mt-6 text-center">
              <button
                class="w-full px-6 py-3 mb-1 mr-1 text-sm font-bold text-white uppercase transition-all duration-150 ease-linear rounded shadow outline-none bg-slate-800 active:bg-white hover:shadow-lg focus:outline-none"
                type="submit"
              >
                Sign In
              </button>
              <nuxt-link to="/auth/signup"
                >New here? Create your new account</nuxt-link
              >
            </div>
          </form>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  data() {
    return {
      user: {
      username: '',
      password: '',
      },
      error:'',
    }
  },
  methods: {
    async userSignIn() {
      try {
        let response = await this.$auth.loginWith('local', {
          data: this.user
        })
        if(response){
        await this.$auth.setUserToken(response.data.accessToken)  
         console.log(response.data.accessToken)      
        }   
        this.$router.push('/');
      } catch (e) {
        console.error(e)
      }
    },
  },
}
</script>

<style>
</style>