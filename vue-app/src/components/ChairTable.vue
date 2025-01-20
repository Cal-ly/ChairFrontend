<template>
  <table class="table table-striped">
    <thead>
      <tr>
        <th>Id</th>
        <th>Model</th>
        <th>Max Weight</th>
        <th>Has Pillow</th>
        <th>Actions</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="chair in chairs" :key="chair.id">
        <td>{{ chair.id }}</td>
        <td>{{ chair.model }}</td>
        <td>{{ chair.maxWeight }}</td>
        <td>{{ chair.hasPillow ? 'Yes' : 'No' }}</td>
        <td>
          <button class="btn btn-danger btn-sm" @click="$emit('deleteChair', chair.id)">Delete</button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  name: 'ChairTable',
  props: {
    chairs: Array,
  },
};
</script>
