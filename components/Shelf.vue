<template>
  <div class="shelf-main">
		<h2 class="shelf-header">หมวดหนังสือ: Harry Potter</h2>

		<div class="shelf-display">
			<Shelf-item v-for="(item, i) in shelfItem" :key="item.title+i" :book="item" :cart="cart"></Shelf-item>
		</div>
	</div>
</template>

<script>
export default {
  name: "Shelf",
	props: ["cart"],
	data() {
		return {
			shelfItem: [
				{
					title: "Harry Potter: Part 1",
					price: 100
				},
				{
					title: "Harry Potter: Part 2",
					price: 100
				},
				{
					title: "Harry Potter: Part 3",
					price: 100
				},
				{
					title: "Harry Potter: Part 4",
					price: 100
				},
				{
					title: "Harry Potter: Part 5",
					price: 100
				},
				{
					title: "Harry Potter: Part 6",
					price: 100
				},
				{
					title: "Harry Potter: Part 7",
					price: 100
				}
			]
		}
	}
}
</script>

<style scoped>
.shelf-main {
  margin: 0px;
}

.shelf-header {
	padding-left: 10px;
}
</style>>
