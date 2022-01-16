<template>
  <div class="max-w-md px-8 py-4 my-20 bg-white rounded-lg shadow-lg">
    <div>
      <h2 class="text-3xl font-semibold text-gray-800">{{ object.object.title }}</h2>
       <small class="text-base text-gray-800">{{  $dateFns.format(object.object.createdAt, 'yyyy-MM-dd')  }}</small>
      <p class="mt-2 text-gray-600">{{ object.object.description }}</p>
    </div>
    <!-- <div class="flex justify-end mt-4">
      <nuxt-link
        :to="`/object/${object._id}`"
        class="text-xl font-medium text-indigo-500"
        >More</nuxt-link
      >
      <nuxt-link
        :to="`/object/${object._id}/edit`"
        class="text-xl font-medium text-indigo-500"
        >Edit</nuxt-link
      >
            <button
        @click="DeleteObject(object.id)"
        class="text-xl font-medium text-indigo-500"
        >Delete</button
      >
    </div> -->
  </div>
</template>

<script>
export default {
    name: "Objectcard",
    props: ['object'],
    methods:{
        async DeleteObject(object_id,params){
            try {
                await this.$axios.$delete(`/object/${params.id}`);
            } catch (e) {
                console.log(e);
            }
        }
    }
}
</script>

<style>
</style>