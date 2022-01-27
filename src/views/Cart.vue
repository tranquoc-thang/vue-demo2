<template>
  <div class="cart">
    <h1 class="cart-heading">Cart</h1>
    <table>
      <tr>
        <th>Code</th>
        <th>Name</th>
        <th>Title</th>
        <th>Price</th>
        <th>Total</th>
        <th>Action</th>
      </tr>
      <tr>
        <td>1</td>
        <td>Name 1</td>
        <td>Title 1</td>
        <td>Price 1</td>
        <td>Total</td>
        <td>Action</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      carts: {},
    };
  },
};
</script>

<style lang="scss" scoped>
.cart {
  margin: 20px;
  &-heading {
    text-align: left;
    font-size: 1.6rem;
  }
}

table {
  width: 100%;
}

td,
th {
  border: 1px solid #ccc;
}
</style>
