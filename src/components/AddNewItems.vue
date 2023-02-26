<template>
  <div>
    <h1>Add New Items</h1>
    <div>
      <label>Product Type</label>
      <input type="text" v-model="productType" class="form-control" />
    </div>
    <div>
      <label>Brand</label>
      <input type="text" v-model="brand" class="form-control" />
    </div>
    <h5>Specifications</h5>
    <div>
      <label>Point Size</label>
      <input
        type="text"
        v-model="specification.pointSize"
        class="form-control"
      />
    </div>
    <div>
      <label>Ink Color</label>
      <input
        type="text"
        v-model="specification.inkColor"
        class="form-control"
      />
    </div>
    <div>
      <label>Ink Type</label>
      <input type="text" v-model="specification.inkType" class="form-control" />
    </div>
    <div>
      <label>Waterproof</label>
      <input
        type="text"
        v-model="specification.waterproof"
        class="form-control"
      />
    </div>
    <button @click="addNew" class="btn btn-primary mt-3">Add New</button>
  </div>
</template>


<script>
import axios from "axios";
const API_URL = "https://8888-cykistanis-html-6nqalz97nz9.ws-us88.gitpod.io/";
export default {
  data: function () {
    return {
      productType: "",
      brand: "",
      image: "",
      specification: {
        pointSize: "",
        inkColor: "",
        inkType: "",
        waterproof: "",
      },
    };
  },
  methods: {
    async addNew() {
      const response = await axios.post(API_URL + "stationery", {
        productType: this.productType,
        brand: this.brand,
        image: this.image,
        pointSize: this.specification.pointSize,
        inkColor: this.specification.inkColor,
        inkType: this.specification.inkType,
        waterproof: this.specification.waterproof,
      });
      this.$emit("add-new-items");
    },
  },
};
</script>


<style scoped>
</style>