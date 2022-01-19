<template>
  <div class="max-w-md px-8 py-4 my-20 bg-white rounded-lg shadow-lg">
    <div>
      <h2 class="text-3xl font-semibold text-gray-800">{{ object.object.title }}</h2>
       <small class="text-base text-gray-800">{{  $moment().startOf(object.object.createdAt, 'yyyy-MM-dd').fromNow()  }}</small>
      <p class="mt-2 text-gray-600">{{ object.object.description }}</p>
    </div>
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