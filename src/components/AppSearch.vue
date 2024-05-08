<script>
import { store } from "../store";
export default {
  data() {
    return {
      store,
      itemSearch:"",
    };
  },
  methods: {
    getSearch() {
      this.store.itemSearch=this.itemSearch;
    },
},
};

</script>

<template>
    <div class="container"> 
        
<div class="input-group mb-3">
  <input v-model="itemSearch" type="text" class="form-control" placeholder="" aria-label="Recipient's username" aria-describedby="button-addon2">
  <button @click="getSearch()" class="btn btn-outline-secondary" type="button" id="button-addon2">Cerca</button>
</div>

    </div>

</template>
<style scoped>

</style>