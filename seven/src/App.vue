<template>
  <div class="container">
    <div class="basket">
      <h3>Basket</h3>
      <div v-for="item in basketItems" :key="item">{{ item.title }}</div>
    </div>
    <div class="products">
      <Product
        @addToBasket="basketItems.push($event)"
        v-for="product in productList"
        :key="product.id"
        :product="product"
      />
    </div>
  </div>
</template>

<script>
import Product from "@/components/Product";
export default {
  name: "App",
  components: { Product },
  data() {
    return {
      basketItems: [],
      productList: [
        {
          id: 0,
          title: "Apple",
          description: "Apple desc",
          price: 1,
          count: 10,
          amount: 0,
        },
        {
          id: 1,
          title: "Avacado",
          description: "Avacado desc",
          price: 15,
          count: 5,
          amount: 0,
        },
        {
          id: 2,
          title: "Grapes",
          description: "Grapes desc",
          price: 7,
          count: 100,
          amount: 0,
        },
        {
          id: 3,
          title: "Cherry",
          description: "Cherry desc",
          price: 3,
          count: 90,
          amount: 0,
        },
        {
          id: 4,
          title: "Lemon",
          description: "Lemon desc",
          price: 0.25,
          count: 100,
          amount: 0,
        },
        {
          id: "5",
          title: "Watermelon",
          description: "Watermelon desc",
          price: 1,
          count: 100,
          amount: 0,
        },
        {
          id: 6,
          title: "Banana",
          description: "Banana desc",
          price: 5,
          count: 20,
          amount: 0,
        },
        {
          id: 7,
          title: "Blueberry",
          description: "Blueberry desc",
          price: 0.75,
          count: 20,
          amount: 0,
        },
        {
          id: 8,
          title: "Pineapple",
          description: "Pineapple desc",
          price: 10,
          count: 20,
          amount: 0,
        },
      ],
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.container {
  display: grid;
  grid-template-areas:
    "header header header header header header"
    "menu main main main right right"
    "menu footer footer footer footer footer";
  grid-gap: 10px;
}
.basket {
  grid-area: menu;
}
.products {
  grid-area: main;
}
</style>
