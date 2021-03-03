<template>
  <div class="hello">
    <div class="cart-button" @click="showcart()">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke="currentColor"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          stroke-width="2"
          d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z"
        />
      </svg>
      <p>{{ cartcount }}</p>
    </div>
    <div class="cart" v-if="cartshow">
      <svg
        @click="hidecart"
        class="close-cart"
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke="currentColor"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          stroke-width="2"
          d="M10 14l2-2m0 0l2-2m-2 2l-2-2m2 2l2 2m7-2a9 9 0 11-18 0 9 9 0 0118 0z"
        />
      </svg>

      <div class="cart-area">
        <div v-for="item in cart" :key="item.index">
          <div class="cart-row">
            <h1>{{ item.title }}</h1>
            <h2>{{ item.price }} TL</h2>
          </div>
          <div class="total-price">Toplam: {{ totalprice }} TL</div>
        </div>
      </div>
    </div>
    <h1>{{ shopname }}</h1>
    <div v-if="loading">
      <img src="https://hackernoon.com/images/0*4Gzjgh9Y7Gu8KEtZ.gif" />
    </div>
    <div v-else class="market">
      <div class="card" v-for="item in items" :key="item.index">
        <div class="card-image-container">
          <img class="card-image" :src="item.image" />
        </div>
        <div class="title-container">
          <h1 class="title">{{ item.title }}</h1>
        </div>
        <div class="price-container">
          <h3 class="price">{{ item.price }} TL</h3>
          <a role="button" @click="addtocart(item)">
            <div class="add-icon-container">
              <svg
                class="add-icon"
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M12 9v3m0 0v3m0-3h3m-3 0H9m12 0a9 9 0 11-18 0 9 9 0 0118 0z"
                />
              </svg>
              <h4 class="add-icon-text">Sepete Ekle</h4>
            </div>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Main",
  data() {
    return {
      items: [],
      cart: [],
      totalprice: 0,
      cartshow: false,
      cartcount: 0,
      loading: true,
    };
  },
  mounted() {
    fetch("https://fakestoreapi.com/products")
      .then((res) => res.json())
      .then((json) => (this.items = json))
      .then(() => (this.loading = false));
  },
  methods: {
    addtocart(itemtoadd) {
      this.cart.push(itemtoadd);
      this.totalprice += itemtoadd.price;
      this.cartcount++;
    },
    showcart() {
      this.cartshow = true;
    },
    hidecart() {
      this.cartshow = false;
    },
  },
  props: {
    shopname: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
a {
  text-decoration: none;
}
a:hover {
  cursor: pointer;
}

.cart-button {
  position: fixed;
  z-index: 100;
  top: 5%;
  right: 5%;
  width: 3vw;
  background-color: rgb(102, 247, 134);
  padding: 15px;
  border-radius: 100px;
  box-shadow: 0 0 25px 0 black;
  transition: 0.2s ease;
}

.cart-button:hover {
  background-color: rgb(238, 248, 240);
  cursor: pointer;
}

.cart {
  width: 40vw;
  height: 40vw;
  background-color: rgb(255, 255, 255);
  position: fixed;
  border-radius: 25px;
  border: 1px solid black;
  box-shadow: 0 0 15px 0px gray;
  top: 50%;
  left: 50%;
  z-index: 100;
  transform: translate(-50%, -50%);
  text-align: left;
  padding: 20px;
}

.close-cart {
  position: absolute;
  top: 1vw;
  right: 1vw;
  width: 3vw;
  color: red;
  transition: 0.2s ease;
}

.cart h1 {
  font-size: 1rem;
}

.cart h2 {
  font-size: 1rem;
}

.cart-area {
  margin-top: 3vw;
}

.cart-row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 1vw;
}

.close-cart:hover {
  cursor: pointer;
  width: 4vw;
}

.total-price {
  position: absolute;
  bottom: 2vw;
  right: 2vw;
  font-size: 1.6rem;
}

.market {
  width: 90vw;
  margin: auto;
  display: grid;
  grid-template-columns: auto auto auto;
  padding: 10px;
}
.card {
  margin: 15px;
  background-color: white;
  border-radius: 15px;
  box-shadow: 0 0 15px 0px #112711;
  position: relative;
  height: fit-content;
}
.card-image-container {
  margin: 2vw 0 2vw 0;
  padding-bottom: 0vw;
  height: auto;
}
.card-image {
  max-height: 10vw;
}

.title-container {
  min-height: 5vw;
  display: flex;
  align-items: center;
  justify-content: center;
  bottom: 0;
  width: 100%;
  background: rgb(102, 247, 134);
}

.title {
  font-size: 1rem;
  padding: 0.5rem;
}

.price-container {
  background-color: #2c3e50;
  color: rgb(102, 247, 134);
  position: relative;
  padding: 10px;
  margin: 0;
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  border-radius: 0 0 15px 15px;
}

.price {
  position: relative;
}

.add-icon-container {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px 10px;
  background-color: rgb(102, 247, 134);
  border-radius: 15px;
  transition: 0.5s ease;
}

.add-icon-container:hover {
  transition: 0.5s ease;
  background-color: rgb(238, 248, 240);
}
.add-icon {
  position: relative;
  width: auto;
  width: 2vw;
  color: #2c3e50;
}

.add-icon-text {
  margin: 0;
  margin-left: 15px;
  color: #2c3e50;
}
</style>
