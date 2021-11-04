<template>
  <div id="home" class="bg-gray-900 min-h-screen h-full p-12">
    <Header :cart="cartCount" @clear="resetCart($event)" />
    <div class="grid md:grid-cols-3 sm:grid-cols-2 gap-4">
      <Card 
        v-for="item in items" 
        :key="item.id"
        :item="item" 
        :in-cart ="inCart(item.id)"
        @add-cart="addToCart($event)"
      />
    </div>
    <h6 class="text-gray-400 text-center mt-6">
      <a href="#" target="_blank" rel="noopener noreferrer">
        Ir a Github
      </a>
    </h6>
  </div>
</template>

<script>
import axios from 'axios'
import Card from '~/components/card.vue'
import Header from '~/components/header.vue';

export default {
  components: { Card, Header },
  data() {
        return {
            items: [],
            cart: []
        };
    },
    async fetch() {
        await this.getItems();
    },
    computed: {
      cartCount() {
        const text = this.cart.length === 1 ? 'producto' : 'productos'
        return `${this.cart.length} ${text}`
      },
    },
    methods: {
      async getItems() {
          const api = 'https://api.artic.edu/api/v1/artworks?page=8&limit=9';
          const response = await axios.get(api);
          response.data.data.forEach(item => {
              this.items.push(item)
          });
      },
      addToCart(id) {
        if (this.cart.includes(id)) {
          return;
        }
        this.cart.push(id)
      },
      resetCart(e) {
        this.cart = []
      },
      inCart(id) {
        return this.cart.includes(id)
      }
    },
}
</script>
