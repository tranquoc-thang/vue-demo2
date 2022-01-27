<template>
  <div>
    <div class="control">
      <input
        class="form-control me-2"
        type="search"
        placeholder="Search by name..."
        aria-label="Search"
        @input="onKeyUpSearch"
        v-model="search"
      />
      <button class="btn btn-dark" @click="onToggleModal">Add Card</button>
    </div>
    <div class="card-list">
      <Card
        v-show="!isSearch"
        v-for="card in cards"
        :key="card.id"
        class="card-item"
        :id="card.id"
        @deleteCard="deleteCard"
      >
        <template v-slot:name>
          {{ card.name }}
        </template>
        <template v-slot:title>
          {{ card.title }}
        </template>
        <template v-slot:description>
          {{ card.description }}
        </template>
      </Card>
      <Card
        v-show="isSearch"
        v-for="searchItem in searchItems"
        :key="searchItem.id"
        class="card-item"
        :id="searchItem.id"
        @deleteCard="deleteCard"
      >
        <template v-slot:name>
          {{ searchItem.name }}
        </template>
        <template v-slot:title>
          {{ searchItem.title }}
        </template>
        <template v-slot:description>
          {{ searchItem.description }}
        </template>
      </Card>
    </div>
    <Modal
      @closeModal="onToggleModal"
      @addCart="addCart"
      v-if="isShowModal"
    ></Modal>
  </div>
</template>

<script>
import Card from "../components/Card.vue";
import Modal from "../components/Modal.vue";

export default {
  name: "App",
  components: {
    Card,
    Modal,
  },
  data() {
    return {
      search: "",
      isSearch: false,
      isShowModal: false,
      searchItems: [],
      cards: [
        {
          id: 1,
          name: "Orange Juice",
          title: "Drink",
          price: 30000,
          description:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium possimus ut commodi consectetur ullam sequi fuga voluptatem ratione aliquid iusto!",
        },
        {
          id: 2,
          name: "Coffee",
          title: "Drink",
          price: 85000,
          description:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium possimus ut commodi consectetur ullam sequi fuga voluptatem ratione aliquid iusto!",
        },
        {
          id: 3,
          name: "Rice",
          title: "Food",
          price: 230000,
          description:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium possimus ut commodi consectetur ullam sequi fuga voluptatem ratione aliquid iusto!",
        },
        {
          id: 4,
          name: "Meat",
          title: "Food",
          price: 170000,
          description:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium possimus ut commodi consectetur ullam sequi fuga voluptatem ratione aliquid iusto!",
        },
        {
          id: 5,
          name: "AK-47",
          title: "Weapon",
          price: 2850000,
          description:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium possimus ut commodi consectetur ullam sequi fuga voluptatem ratione aliquid iusto!",
        },
      ],
    };
  },
  methods: {
    onToggleModal() {
      this.isShowModal = !this.isShowModal;
    },
    addCart(name, title, description) {
      this.cards = [
        ...this.cards,
        {
          id: this.cards.length + 1,
          name: name,
          title: title,
          description: description,
        },
      ];
    },
    deleteCard(id) {
      this.cards = this.cards.filter((card) => card.id !== id);
    },
    onKeyUpSearch() {
      if (this.search != "") {
        this.searchItems = this.cards.filter((card) =>
          card.name.includes(this.search)
        );
        this.isSearch = true;
        console.log(this.isSearch);
      }
      if (this.search == "") {
        this.isSearch = false;
        console.log(this.isSearch);
      }
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.card {
  &-list {
    margin: 30px 50px 50px;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
  }
  &-item {
    margin-bottom: 15px;
    max-width: calc(25% - 15px);
  }
}

.control {
  max-width: 500px;
  display: flex;
  justify-content: space-between;
  max-height: 40px;
  margin: 20px auto 0;
  & button {
    white-space: nowrap;
    min-width: 100px;
  }
}
</style>
