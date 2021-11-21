<template>
  <div id="addForm">
    <h3>Add Product</h3>
    <form @submit.prevent="handleAdd">
      <div class="form-group">
        <label for="categoryId">Category</label>
        <input
          type="text"
          v-model="product.categoryId"
          class="form-control"
          id="categoryId"
        />
      </div>

      <div class="form-group">
        <label for="productName">Product Name</label>
        <input
          type="text"
          v-model="product.productName"
          class="form-control"
          id="productName"
        />
      </div>

      <div class="form-group">
        <label for="quantityPerUnit">Quantity Per Unit</label>
        <input
          type="text"
          v-model="product.quantityPerUnit"
          class="form-control"
          id="quantityPerUnit"
        />
      </div>

      <div class="form-group">
        <label for="unitPrice">Unit Price</label>
        <input
          type="text"
          v-model="product.unitPrice"
          class="form-control"
          id="unitPrice"
        />
      </div>

      <div class="form-group">
        <label for="unitsInStock">Units In Stock</label>
        <input
          type="text"
          v-model="product.unitsInStock"
          class="form-control"
          id="unitsInStock"
        />
      </div>
      <br />
      <button type="submit" class="btn btn-success">Add Product</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "product-add",
  data() {
    return {
      product: {
        categoryId: "",
        productName: "",
        quantityPerUnit: "",
        unitPrice: "",
        unitsInStock: "",
      },
    };
  },
  methods: {
    handleAdd() {
      this.$emit("add:product", this.product);
    },
  },
};
</script>

<style scoped>
#addForm {
  margin: 100px;
}
</style>