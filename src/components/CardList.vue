<template>
  <div class="grid sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
    <div
      v-for="person in people"
      :key="person.id"
      class="bg-white rounded-lg p-6 shadow"
    >
      <img :src="person.avatar" class="h-16 w-16 rounded-full mx-auto" alt="" />
      <div class="text-center">
        <h2 class="text-lg">
          {{ person.name }}
        </h2>
        <div class="text-purple-500">
            {{person.department}}
        </div>
        <div class="text-gray-600 text-sm">
            {{person.email}}
        </div>
        <div class="text-gray-600 text-sm">
            {{person.phone}}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { onBeforeMount, ref } from "vue";

export default {
  setup() {
    const people = ref([]);

    onBeforeMount(() => {
      fetch("http://localhost:3000/people")
        .then((res) => {
          return res.json();
        })
        .then((data) => {
          people.value = data;
        });
    });

    return {
      people,
    };
  },
};
</script>

<style>
</style>