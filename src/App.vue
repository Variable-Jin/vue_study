<template>
  <transition name="fade">
    <Modal
      @closeModal="모달창열렸니 = false"
      :원룸들="원룸들"
      :누른거="누른거"
      :모달창열렸니="모달창열렸니"
    />
  </transition>

  <div class="menu">
    <a v-for="a in 메뉴들" :key="a"> {{ a }} </a>
  </div>

  <!-- <Discount v-if="showDiscount == true" /> -->
  <Discount v-if="amountTime == true" />

  <button @click="priceSort">가격순정렬</button>
  <button @click="sortBack">되돌리기</button>

  <Card
    @openModal="
      모달창열렸니 = true;
      누른거 = $event;
    "
    :원룸="원룸들[i]"
    v-for="(card, i) in 원룸들"
    :key="card"
  />
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
      amountTime: true,
      // showDiscount: true,
      원룸들오리지널: [...data],
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
    sortBack() {
      this.원룸들 = [...this.원룸들오리지널];
    },

    priceSort() {
      this.원룸들.sort(function (a, b) {
        return a.price - b.price;
      });
    },
  },

  // mounted() {
  //   setTimeout(() => {
  //     this.showDiscount = false;
  //   }, 3000);
  // },

  components: {
    Discount: DiscountExample,
    Modal: ModalComponent,
    Card: CardComponent,
  },
};
</script>

<style>
/* 등장 */
.fade-enter-from {
  transform: translateY(-1000px);
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  transform: translateY(0px);
}
/* 퇴장 */
.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  opacity: 0;
}

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
