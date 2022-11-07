<template>
  <div class="main">
    <h1 class="header">
      บ้านนายดิน
    </h1>
    <div class="shelf">
      <Shelf :cart="cart"></Shelf>
    </div>
    <div class="cart">
      <Cart :cart="cart"></Cart>
    </div>
  </div>
</template>

<script>
export default {
  name: "IndexPage",
  data() {
    return {
      cart: []
    }
  }
}
</script>

<style scoped>
.main {
  margin: -8px -8px auto -8px;
  padding: 20px 10%;

  position: relative;
}
.header {
  margin: 0px;
  padding: 20px;
  padding-left: calc(10% + 10px);
  width: 100vw;

  position: absolute;
  top: 0;
  left: 0;
  background-color: #14C38E;
  color: white;
}

.shelf {
  width: 80%;
  margin-top: 70px;

  float: left;
}

.cart {
  width: calc(20% - 10px);
  margin-top: 70px;
  
  float: right;
}
</style>
