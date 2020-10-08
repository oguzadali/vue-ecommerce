<template>
  <div id="addForm">
    <form @submit.prevent="handleAdd">
      <div class="form-group">
        <label for="id">Id</label>
        <input v-model="product.id" type="text" class="form-control" id="id" />
      </div>

      <div class="form-group">
        <label for="categoryId">Category</label>
        <input
          v-model="product.categoryId"
          type="text"
          class="form-control"
          id="categoryId"
        />
      </div>

      <div class="form-group">
        <label for="productName">productName</label>
        <input
          v-model="product.productName"
          type="text"
          class="form-control"
          id="productName"
        />
      </div>

      <div class="form-group">
        <label for="quantityPerUnit">quantityPerUnit</label>
        <input
          v-model="product.quantityPerUnit"
          type="text"
          class="form-control"
          id="quantityPerUnit"
        />
      </div>

      <div class="form-group">
        <label for="unitPrice">unitPrice</label>
        <input
          v-model="product.unitPrice"
          type="text"
          class="form-control"
          id="unitPrice"
        />
      </div>

      <div class="form-group">
        <label for="unitInStock">unitInStock</label>
        <input
          v-model="product.unitInStock"
          type="text"
          class="form-control"
          id="unitInStock"
        />
      </div>
      <button type="submit" class="btn btn-sm btn-success ">
        Add
      </button>
    </form>
  </div>
</template>

<script>
export default {
  name: "product_add",
  data() {
    return {
      product: {
        id: "",
        categoryId: "",
        productName: "",
        quantityPerUnit: "",
        unitPrice: "",
        unitInStock: "",
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
