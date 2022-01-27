<template>
  <div class="card" style="width: 18rem">
    <div class="card-body">
      <h5 class="card-title">
        <slot name="title"></slot>
      </h5>
      <h6 class="card-subtitle mb-2 text-muted">
        <slot name="name"></slot>
      </h6>
      <p class="card-text">
        <slot name="description"></slot>
      </p>
      <button type="button" class="btn btn-primary">Add to Cart</button>
      <button
        type="button"
        class="my-btn-close btn-close btn-close-black"
        aria-label="Close"
        @click="deleteCard"
      ></button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  methods: {
    deleteCard() {
      this.$emit("deleteCard", this.id);
    },
  },
  props: {
    id: {
      required: true,
    },
  },
};
</script>

<style lang="scss">
.card {
  background: silver;
  &-body {
    position: relative;
    & .my-btn-close {
      position: absolute;
      top: 5px;
      right: 5px;
    }
  }
}
</style>
