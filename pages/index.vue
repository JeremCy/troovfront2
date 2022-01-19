<template>
  <main>
    <div class="flex flex-col 2xl::inline-flex center 2xl:flex-row-reverse justify-center items-center text-center">
      <img src="/hero.svg" class="2xl:max-w-sm rounded-lg w-48 h-48" />
      <div class="">
        <h1 class="mb-5 text-base font-bold lg:text-2xl 2xl:text-5xl">UN OBJET PERDU SE TRANSFORME SOUVENT EN OBJET TROUVÉ !</h1>
        <p class="mb-5">Vous avez perdu ou trouvé un objet ? Déclarez-le et la communauté se mobilise pour vous aider à le retrouver.</p>
        <button class="w-full px-6 py-3 mb-1 mr-1 text-sm font-bold text-white uppercase transition-all duration-150 ease-linear rounded shadow outline-none bg-slate-800 active:bg-white hover:shadow-lg focus:outline-none">
          <NuxtLink to="/object/add">J'ai perdue </NuxtLink>
        </button>
      </div>
    </div>
  </main>
</template>

<script>
import ObjectsCard from '~/components/ObjectsCard.vue'

export default {
  name: 'IndexPage',
  layout: 'default',
  components: {
    ObjectsCard,
  },
  auth: false,
  async asyncData({ $axios, params }) {
    try {
      let objects = await $axios.$get(`/object/all`)
      return { objects }
    } catch (e) {
      return { objects: [] }
    }
  },
  data() {
    return {
      objects: [],
    }
  },
}
</script>
