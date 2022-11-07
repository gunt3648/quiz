<template>
  <div class="shelf-item">
    <h1 class="item-title">
      {{ book.title }}
    </h1>

    <p class="item-price">
      {{ book.price }} <span class="item-currency">บาท</span>
    </p>
    <button class="item-button" @click="addToCart()">Add to cart</button>
  </div>
</template>

<script>
export default {
  name: "Shelf-Item",
  props: ["book", "cart"],
  methods: {
    addToCart() {
      const ref = this.cart.find((e) => e.title === this.book.title);
      if (ref != undefined) {
        ref.quantity += 1;
      } else {
        this.cart.push({
          title: this.book.title,
          price: this.book.price,
          quantity: 1,
        });
      }
    },
  },
};
</script>

<style scoped>
.shelf-item {
  width: 20%;
  min-width: 200px;
  height: 244px;
  margin: 10px;
  padding: 10px;

  display: inline-block;
  position: relative;
  background-color: #31c6d4;
  border-radius: 5px;
}

.item-title,
.item-price {
  color: white;
}

.item-price {
  margin: 0px;

  position: absolute;
  bottom: 10px;
  left: 10px;
  font-size: 24px;
  font-weight: bold;
}

.item-currency {
  font-size: 16px;
  font-weight: normal;
}

.item-button {
  padding: 10px 15px;

  position: absolute;
  bottom: 10px;
  right: 10px;
  background-color: #2192ff;
  color: white;
  border: none;
  border-radius: 5px;
}
</style>>
