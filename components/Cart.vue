<template>
  <div class="cart-main">
    <h2 class="shelf-header">ตะกร้า</h2>
    <div class="cart-detail">
      <p v-if="itemsInCart.length == 0">ยังไม่ได้เพิ่มสินค้าลงในตะกร้า</p>
      <div v-else>
        <Cart-item
          v-for="(item, i) in itemsInCart"
          :key="item.title + i"
          :book="item"
          :index="i + 1"
        ></Cart-item>
      </div>
    </div>

    <div class="cart-total">
      <p>จำนวนทั้งหมด: {{ totalItems }}</p>
      <p>ราคารวม: {{ totalPrice }}</p>
      <p>ส่วนลด: {{ totalDiscount }}</p>
      <p>รวมสุทธิ: {{ totalAfterDiscount }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Cart",
  props: ["cart"],
  computed: {
    itemsInCart() {
      return this.cart.filter((e) => e.quantity !== 0);
    },
    totalItems() {
      return this.itemsInCart.reduce((acc, item) => acc + item.quantity, 0);
    },
    totalPrice() {
      return this.itemsInCart.reduce(
        (acc, item) => acc + item.price * item.quantity,
        0
      );
    },
    totalDiscount() {
      let total = 0;
      if (this.itemsInCart.length > 1) {
        const max = this.itemsInCart.reduce((prev, curr) =>
          prev.quantity > curr.quantity ? prev : curr
        ).quantity;
        for (let i = 1; i <= max; i++) {
          const filtered = this.itemsInCart.filter((e) => e.quantity >= i);
          if (filtered.length > 0) {
            const sum = filtered.reduce(
              (acc, item) => acc + item.price,
              0
            );
            total += sum * (filtered.length - 1) / 10;
          }
        }
        return total;
      } else return total;
    },
    totalAfterDiscount() {
      return this.totalPrice - this.totalDiscount;
    },
  },
};
</script>

<style scoped>
.cart-main {
  margin: 0px;
}

.cart-detail {
  padding-top: 20px;
  height: 400px;
  overflow-y: scroll;
}
</style>>