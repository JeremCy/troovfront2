<template>
  <div class="max-w-md px-8 py-4 my-20 bg-white rounded-lg shadow-lg">
  <div>
    <h2 class="text-3xl font-semibold text-gray-800">{{object.title}}</h2>
    <p class="mt-2 text-gray-600">{{object.description}}</p>
  </div>
  <div class="flex justify-end mt-4">
    <nuxt-link :to="`/object/${object._id}`" class="text-xl font-medium text-indigo-500">More</nuxt-link>
  </div>
</div>
</template>

<script>
export default {
  name: 'ObjectsCard',
  props: ['object'],
}
</script>

<style>
</style>