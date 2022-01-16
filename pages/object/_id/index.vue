<template>
    <object-card :object="object" />
</template>

<script>
import ObjectCard from '~/components/Objectcard.vue'
export default {
  title: 'default',
  layout: 'default',
  auth: false,
  components: {
    ObjectCard,
  },
  data() {
    return {
      object: [],
    }
  },
  async asyncData({ $axios, params }) {
    try {
      let object = await $axios.$get(`object/${params.id}`);
      return { object }
    } catch (e) {
      return { object: [] }
    }
  },
}
</script>

<style>
</style>