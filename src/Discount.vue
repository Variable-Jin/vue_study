<template>
  <div class="discount" v-if="amountTime == true">
    <h4>지금 결제하면 {{ amount }}% 할인</h4>
    <!-- <p v-if="amountTime == true">남은 시간 :{{ amount }}초</p> -->
  </div>
</template>

<script>
export default {
  name: "DiscountExample",
  data() {
    return {
      amount: 30,
      amountTime: true,
    };
  },

  mounted() {
    setInterval(() => {
      this.amount--;
    }, 1000);

    setTimeout(() => {
      this.amountTime = false;
    }, 30000);
  },
};
</script>

<style></style>
