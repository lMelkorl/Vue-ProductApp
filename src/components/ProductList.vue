<template>
  <div id="list">
    <h3>Product List</h3>

    <p v-if="products.length == 0">There is Nothing</p>

    <table v-else class="table">
      <thead>
        <tr>
          <th>Id</th>
          <th>Product Name</th>
          <th>Category</th>
          <th>Quantity Per Unit</th>
          <th>Unit Price</th>
          <th>Units In Stock</th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="product in products" :key="product.id">
          <td v-if="updateId === product.id">
            <input
              type="text"
              v-model="product.id"
              class="form-control"
              id="id"
            />
          </td>
          <td v-else>{{ product.id }}</td>

          <td v-if="updateId === product.id">
            <input
              type="text"
              v-model="product.productName"
              class="form-control"
              id="name"
            />
          </td>
          <td v-else>{{ product.productName }}</td>

          <td v-if="updateId === product.id">
            <input
              type="text"
              v-model="product.categoryId"
              class="form-control"
              id="categoryId"
            />
          </td>
          <td v-else>{{ product.categoryId }}</td>


          <td v-if="updateId === product.id">
            <input
              type="text"
              v-model="product.quantityPerUnit"
              class="form-control"
              id="quantityPerUnit"
            />
          </td>
          <td v-else>{{ product.quantityPerUnit }}</td>


          <td v-if="updateId === product.id">
            <input
              type="text"
              v-model="product.unitPrice"
              class="form-control"
              id="unitPrice"
            />
          </td>
          <td v-else>{{ product.unitPrice }}</td>

          <td v-if="updateId === product.id">
            <input
              type="text"
              v-model="product.unitsInStock"
              class="form-control"
              id="unitsInStock"
            />
          </td>
          <td v-else>{{ product.unitsInStock }}</td>

          <td v-if="updateId !== product.id">
            <button
              class="btn btn-sm btn-primary"
              @click="handleUpdate(product)"
            >
              Update
            </button>
            &nbsp;
            <button
              class="btn btn-sm btn-danger"
              @click="handleDelete(product)"
            >
              Delete
            </button>
          </td>


          <td v-else>
            <button
              class="btn btn-sm btn-primary"
              @click="handleSave(product)"
            >
              Save
            </button>
            &nbsp;
            <button
              class="btn btn-sm btn-danger"
              @click="updateId=null"
            >
              Cancel
            </button>
          </td>

           
          
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  props: {
    products: Array,
  },
  data() {
    return { updateId: null };
  },
  methods: {
    handleDelete(product) {
      this.$emit("delete:product", product);
    },
    handleUpdate(product) {
      this.updateId = product.id;
    },
    handleSave(product){
        this.$emit("update:product",product)
        this.updateId=null
    }
  },
};
</script>

<style scoped>
#list{
    margin: 100px;
}
</style>