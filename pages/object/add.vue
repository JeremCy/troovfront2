<template>
    <div class="px-4 pt-6 mx-auto text-white lg:w-4/12 center">
      <div
        class="relative flex flex-col w-full min-w-0 mb-6 break-words border-0 rounded-lg shadow-lg bg-[#466060]"
      >
        <div class="flex-auto px-4 py-10 pt-0 space-y-4 lg:px-10">
          <h1 class="mt-4 mb-3 text-4xl font-bold text-center">Add object</h1>
          <b-notification v-if="error" type="is-warning">
            {{ error }}
          </b-notification>
          <form @submit.prevent="addObject">
            <div class="relative w-full mb-3">
              <label
                class="block mb-2 text-xs font-bold uppercase text-blueGray-600"
                for="grid-password"
                >Title</label
              ><input
                id="title"
                type="text"
                class="w-full px-3 py-3 text-sm transition-all duration-150 ease-linear bg-white border-0 rounded shadow text-slate-800 placeholder-blueGray-300 focus:outline-none focus:ring"
                placeholder="title"
                v-model="title"
              />
            </div>
            <div class="relative w-full mb-3">

              <input 
                id="lost"
                type="checkbox"
                class=""
                v-model="lost"
              /><span>Lost items?</span>
            </div>
            <div class="relative w-full mb-3">
              <label
                class="block mb-2 text-xs font-bold uppercase text-blueGray-600"
                for="grid-password"
                >Types d'object</label
              >
              <input 
                id="Description"
                type="text"
                class="w-full px-3 py-3 text-sm transition-all duration-150 ease-linear bg-white border-0 rounded shadow resize-none text-slate-800 placeholder-blueGray-300 text-blueGray-600 focus:outline-none focus:ring"
                placeholder="types"
                v-model="types"
              />
            </div>
            <div class="relative w-full mb-3">
              <label
                class="block mb-2 text-xs font-bold uppercase text-blueGray-600"
                for="grid-password"
                >Description</label
              >
              <textarea 
                id="Description"
                type="text"
                class="w-full px-3 py-3 text-sm transition-all duration-150 ease-linear bg-white border-0 rounded shadow resize-none text-slate-800 placeholder-blueGray-300 text-blueGray-600 focus:outline-none focus:ring"
                placeholder="Description"
                v-model="description"
              />
            </div>

            <div class="mt-6 text-center">
              <button
                class="w-full px-6 py-3 mb-1 mr-1 text-sm font-bold text-white uppercase transition-all duration-150 ease-linear rounded shadow outline-none bg-slate-800 active:bg-blueGray-600 hover:shadow-lg focus:outline-none"
                type="submit"
              >
                Add
              </button>
            </div>
          </form>
        </div>
      </div>
    </div>
</template>

<script>
export default {
    auth: false,
    data(){
        return{ 
            title: "",
            description: "",
            lost: false,
            type: "",
            error: "",
        }
    },
    methods: {
        async addObject() {
            try {
                await this.$axios.post('/object/create',{
                    title: this.title,
                    description: this.description,
                    lost: this.lost,
                    type: this.type,
                })
                this.$router.push('/');
            } catch (e) {
                this.error = e.response.data.message
            }
        }
    }

}
</script>

<style>

</style>