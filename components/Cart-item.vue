<template>
  <div v-if="book" class="cart-item">
    <div class="item-title">
      <span class="item-index">#{{ index }}</span>
      {{ book.title }}
    </div>
    <p class="item-price">ราคา: {{ book.price }} บาท</p>
    <p class="item-quantity">
			<button class="item-remove" @click="removeItem()">-</button>
			{{ book.quantity }}
			<button class="item-add" @click="addItem()">+</button>
		</p>
  </div>
</template>

<script>
export default {
  name: "Cart-Item",
  props: ["book", "index"],
  methods: {
		addItem() {
			this.book.quantity += 1;
		},
		removeItem() {
			this.book.quantity -= 1;
		}
	},
};
</script>

<style scoped>
.cart-item {
	margin-bottom: 10px;
  width: 100%;
  position: relative;
}

.item-index {
	margin-right: 10px;
	border-radius: 20px;

	font-weight: bold;
	color: #31C6D4;
}

.item-price, .item-quantity {
	margin: 0px;
}

.item-quantity {
	position: absolute;
	right: 0;
	bottom: 0;
}

.item-add, .item-remove {
	border: none;
	background: none;
	color: #31C6D4;
	font-size: 16px;
	font-weight: bold;
}
</style>>
