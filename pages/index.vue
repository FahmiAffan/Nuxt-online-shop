<template>
  <div class="bg-grey">
    <Sidebar />
    <v-container v-scroll.self="ExpandOnScroll">
      <v-row>
        <v-col
          v-for="i in produk"
          :key="i"
          cols="12"
          md="4"
          sm="6"
          lg="4"
          xl="4"
        >
          <v-card
            width="500"
            height="500"
            class="pa-2 d-flex flex-column justify-space-between rounded-lg"
          >
            <v-img :src="i.image" max-height="256" contain class="mt-5"></v-img>
            <div>
              <v-card-title class="pa-0 py-2 pt-5 text-subtitle-2">
                {{ i.title }}
              </v-card-title>
              <v-card-item>
                <div>
                  {{ i.category }}
                </div>
              </v-card-item>
              <v-divider class="my-2 mt-4"></v-divider>
              <div class="d-flex align-center justify-space-between">
                <h1>${{ i.price }}</h1>
                <v-btn class="px-16" @click="ToCart(i.id)">Buy</v-btn>
              </div>
            </div>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      produk: [],
      scrolled: 1,
      qty: 1,
    }
  },
  mounted() {
    this.$axios
      .$get('https://fakestoreapi.com/products')
      .then((response) => (this.produk = response))
      .catch((error) => console.log(error))
  },
  methods: {
    ExpandOnScroll() {
      this.scrolled += 1
      console.log(this.scrolled)
      const collection = document.getElementsById('navbars')
      collection.style.position = 'absolute'
    },
    ToCart(id) {
      this.$axios
        .$post('https://fakestoreapi.com/carts', {
          products: [
            {
              productId: id,
              quantity: this.qty,
            },
          ],
        })
        .then((response) => response)
    },
  },
}
</script>

<style>
.bg-grey {
  background-color: #eeeeee;
}
</style>
