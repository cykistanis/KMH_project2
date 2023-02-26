<template>
  <div>
    <h1>Edit items</h1>
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
  </div>
</template>


<script>
import axios from "axios";
const API_URL = "https://8888-cykistanis-html-6nqalz97nz9.ws-us88.gitpod.io/";
export default {
  props: ["itemId"],
  async created() {
    let response = await axios.get(API_URL + "stationery/" + this.itemId);
    this.productType = response.data.productType;
    this.brand = response.data.brand;
    this.image = response.data.image;
    this.specification.pointSize = response.data.specification.pointSize;
    this.specification.inkColor = response.data.specification.inkColor;
    this.specification.inkType = response.data.specification.inkType;
    this.specification.waterproof = response.data.specification.waterproof;
  },
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
};
</script>



<style scoped>
</style>