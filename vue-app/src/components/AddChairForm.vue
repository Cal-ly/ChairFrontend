<template>
    <form @submit.prevent="handleSubmit" class="mt-4">
      <input type="hidden" name="id" v-model="newChair.id" />
      <div class="mb-3">
        <label for="model" class="form-label">Model</label>
        <input type="text" id="model" v-model="newChair.model" class="form-control" required />
      </div>
      <div class="mb-3">
        <label for="maxWeight" class="form-label">Max Weight</label>
        <input type="number" id="maxWeight" v-model.number="newChair.maxWeight" class="form-control" required />
      </div>
      <div class="mb-3">
        <label for="hasPillow" class="form-label">Has Pillow</label>
        <select id="hasPillow" v-model="newChair.hasPillow" class="form-select">
          <option :value="true">Yes</option>
          <option :value="false">No</option>
        </select>
      </div>
      <button type="submit" class="btn btn-primary">Add Chair</button>
    </form>
  </template>
  
  <script>
  export default {
    name: 'AddChairForm',
    data() {
      return {
        newChair: {
          id: 0,
          model: '',
          maxWeight: 50,
          hasPillow: true,
        },
      };
    },
    methods: {
      handleSubmit() {
        this.$emit('addChair', this.newChair);
        this.newChair = { id: 0, model: '', maxWeight: 50, hasPillow: true }; // Reset form
      },
    },
  };
  </script>
  