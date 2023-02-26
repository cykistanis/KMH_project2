<template>
  <div>
    <h1>All Items</h1>
    <input type="text" v-model="searchterms" />

    <ul>
      <li v-for="p in filteredProducts" v-bind:key="p._id">
        <ul>
          <li>Product Type : {{ p.productType }}</li>
          <li>Brand: {{ p.brand }}</li>
          <li>Point Size: {{ p.specification.pointSize }}</li>
          <li>Ink Color: {{ p.specification.inkColor }}</li>
          <li>Ink Type: {{ p.specification.inkType }}</li>
          <li>Waterproof: {{ p.specification.waterProof }}</li>
        </ul>
        <button type="button" class="btn btn-primary" @click="editItems(p._id)">
          Edit
        </button>

        <br />
        <img v-bind:src="p.image" />
      </li>
    </ul>
  </div>
</template>


<script>
import axios from "axios";
const API_URL = "https://8888-cykistanis-html-6nqalz97nz9.ws-us88.gitpod.io/";

export default {
  data: function () {
    return {
      items: [],
      searchterms: "",
    };
  },

  async created() {
    let response = await axios.get(API_URL + "stationery");
    this.items = response.data;
  },
  methods: {
    editItems(itemId) {
      this.$emit("edit-items", itemId);
    },
  },
  computed: {
    filteredProducts: function () {
      let filtered = [];
      for (let p of this.items) {
        if (
          p.productType.toLowerCase().includes(this.searchterms.toLowerCase())
        ) {
          filtered.push(p);
        }
      }
      return filtered;
    },
  },
};
</script>

<style scoped>
</style>