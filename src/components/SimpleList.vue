<template>
  <div class="overflow-scroll p-2">
    <table>
      <thead>
        <tr>
          <th>Name</th>
          <th>Email</th>
          <th>Phone</th>
          <th>Department</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="person in people" :key="person.id">
          <td>{{ person.name }}</td>
          <td>{{ person.email }}</td>
          <td>{{ person.phone }}</td>
          <td>{{ person.department }}</td>
        </tr>
      </tbody>
    </table>
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
table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

td,
th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}

tr:nth-child(even) {
  background-color: #dddddd;
}
</style>