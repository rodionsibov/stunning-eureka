<template>
  <div class="mx-auto p-6 bg-gray-200">
    <card-list />
  </div>
  <simple-list />
</template>

<script>
import SimpleList from "@/components/SimpleList.vue";
import CardList from "@/components/CardList.vue";

export default {
  name: "App",
  components: {
    SimpleList,
    CardList,
  },
};
</script>

