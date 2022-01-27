<template>
  <div class="modal" tabindex="-1" @click.self="closeModal">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title">Modal title</h5>
          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal"
            aria-label="Close"
            @click.self="closeModal"
          ></button>
        </div>
        <div class="modal-body">
          <div class="mb-3 row">
            <label for="inputPassword" class="col-sm-2 col-form-label"
              >Name</label
            >
            <div class="col-sm-10">
              <input
                type="text"
                class="form-control"
                id="inputPassword"
                v-model="name"
              />
            </div>
          </div>
          <div class="mb-3 row">
            <label for="inputPassword" class="col-sm-2 col-form-label"
              >Title</label
            >
            <div class="col-sm-10">
              <input
                type="text"
                class="form-control"
                id="inputPassword"
                v-model="title"
              />
            </div>
          </div>
          <div class="mb-3 row">
            <label for="inputPassword" class="col-sm-2 col-form-label"
              >Description</label
            >
            <div class="col-sm-10">
              <input
                type="text"
                class="form-control"
                id="inputPassword"
                v-model="description"
              />
            </div>
          </div>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-primary" @click="addCart">
            Create
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Modal",
  data() {
    return {
      name: "",
      title: "",
      description: "",
    };
  },
  methods: {
    closeModal() {
      this.$emit("closeModal");
    },
    addCart() {
      this.$emit("addCart", this.name, this.title, this.description);
      this.closeModal();
    },
  },
};
</script>

<style lang="scss">
.modal {
  display: block;
  &-dialog {
    max-width: 600px;
  }
}

.modal {
  background: rgba(0, 0, 0, 0.6);
}
</style>
