<template>
  <Modal :원룸들="원룸들" :누른거="누른거" :모달창열렸니="모달창열렸니" />

  <div class="menu">
    <a v-for="a in 메뉴들" :key="a"> {{ a }} </a>
  </div>

  <Discount v-bind="오브젝트" :이름="오브젝트.name" :나이="오브젝트.age" />

  <Card :원룸="원룸들[i]" v-for="(Card, i) in 원룸들" :key="Card" />
  <!-- <Card :원룸="원룸들[1]" />
  <Card :원룸="원룸들[2]" />
  <Card :원룸="원룸들[3]" />
  <Card :원룸="원룸들[4]" />
  <Card :원룸="원룸들[5]" /> -->

  <!-- <div v-for="(a, i) in 원룸들" :key="i">
    <img :src="원룸들[0].image" class="room-img" />
    <h4 @click="모달창열렸니 = true" 누른거="i">{{ a.title }}</h4>
    <p>{{ a.price }}</p>
  </div> -->
</template>

<script>
import data from "./assets/oneroom.js";
import DiscountExample from "./Discount.vue";
import ModalComponent from "./Modal.vue";
import CardComponent from "./Card.vue";

export default {
  name: "App",
  data() {
    return {
      오브젝트: { name: "kim", age: 20 },
      누른거: 0,
      원룸들: data,
      모달창열렸니: false,
      신고수: [0, 0, 0],
      메뉴들: ["Home", "Shop", "About"],
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
    };
  },

  methods: {
    increase() {
      this.신고수 += 1;
    },
  },

  components: {
    Discount: DiscountExample,
    Modal: ModalComponent,
    Card: CardComponent,
  },
};
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.discount {
  background: rgb(138, 149, 201);
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}

.room-img {
  width: 50%;
  margin-top: 40px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: darkolivegreen;
  padding: 15px;
  border-radius: 15px;
}

.menu a {
  color: white;
  padding: 15px;
}
</style>
