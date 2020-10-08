<template>
  <div>
    <p v-if="products.length == 0">No Product</p>
    <table class="table">
      <thead>
        <tr>
          <th>Id</th>
          <th>Product Name</th>
          <th>Category</th>
          <th>Explanation</th>
          <th>Price</th>
          <th>Stock</th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="product in products" :key="product.id">
          <td v-if="updateId === product.id">
            <input v-model="product.id" type="text" class="form-control" />
          </td>
          <td v-else>{{ product.id }}</td>

          <td v-if="updateId === product.id">
            <input
              v-model="product.productName"
              type="text"
              class="form-control"
            />
          </td>
          <td v-else>{{ product.productName }}</td>

          <td v-if="updateId === product.id">
            <input
              v-model="product.quantityPerUnit"
              type="text"
              class="form-control"
            />
          </td>
          <td v-else>{{ product.quantityPerUnit }}</td>

          <td v-if="updateId === product.id">
            <input
              v-model="product.unitPrice"
              type="text"
              class="form-control"
            />
          </td>
          <td v-else>{{ product.unitPrice }}</td>

          <td v-if="updateId === product.id">
            <input
              v-model="product.unitsInStock"
              type="text"
              class="form-control"
            />
          </td>
          <td v-else>{{ product.unitsInStock }}</td>

          <!-- <td>{{ product.productName }}</td>
          <td>{{ product.category }}</td>
          <td>{{ product.quantityPerUnit }}</td>
          <td>{{ product.unitPrice }}</td>
          <td>{{ product.unitsInStock }}</td> -->
          <td v-if="updateId !== product.id">
            <button
              class="btn btn-sm btn-primary"
              @click="handleUpdate(product)"
            >
              Update
            </button>
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
              @click="handleUpdate(product)"
            >
              Save
            </button>

            <button class="btn btn-sm btn-danger" @click="updateId = null">
              Close
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "product-list",
  data() {
    return {
      updateId: null,
    };
  },
  props: {
    products: Array,
  },
  methods: {
    handleDelete(product) {
      this.$emit("delete:product", product);
    },
    handleUpdate(product) {
      this.updateId = product.id;
    },
    handleSave(product) {
      this.$emit("update:product", product);
    },
  },
};
</script>

<style></style>
