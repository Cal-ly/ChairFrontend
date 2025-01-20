<template>
  <div class="container mt-4">
    <h1 class="text-center">Chair Management</h1>
    <ChairTable :chairs="chairs" @deleteChair="deleteChair" />
    <AddChairForm @addChair="addChair" />
  </div>
</template>

<script>
import axios from 'axios';
import ChairTable from './components/ChairTable.vue';
import AddChairForm from './components/AddChairForm.vue';

export default {
  name: 'App',
  components: { ChairTable, AddChairForm },
  data() {
    return {
      chairs: [],
    };
  },
  methods: {
    fetchChairs() {
      axios.get('https://chairapi-a2ggarbthrb4h4dr.northeurope-01.azurewebsites.net/api/chair')
        .then(response => (this.chairs = response.data))
        .catch(error => console.error('Error fetching chairs:', error));
    },
    addChair(newChair) {
      axios.post('https://chairapi-a2ggarbthrb4h4dr.northeurope-01.azurewebsites.net/api/chair', newChair)
        .then(() => this.fetchChairs())
        .catch(error => console.error('Error adding chair:', error));
    },
    deleteChair(id) {
      axios.delete(`https://chairapi-a2ggarbthrb4h4dr.northeurope-01.azurewebsites.net/api/chair/${id}`)
        .then(() => this.fetchChairs())
        .catch(error => console.error('Error deleting chair:', error));
    },
  },
  mounted() {
    this.fetchChairs();
  },
};
</script>

<style scoped>
.container {
  max-width: 720px;
}
</style>
