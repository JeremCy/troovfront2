<template>
  <main>
    <h1 class="mt-4 text-center text-white text-8xl">Troov</h1>
    <div class="grid">
      <template v-for="object in objects">
        <div class="" :key="object.id">
          <objects-card :object="object" />
        </div>
      </template>
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
      let objects = await $axios.$get(`/object/all`);
      return { objects };
    } catch (e) {
      return { objects: [] };
    }
  },
  data() {
    return {
      objects: [],
    };
  },
}
</script>
