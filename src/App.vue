<template>
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <h4>상세페이지 내용임</h4>
      <button @click="모달창열렸니 = false">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="(menu, i) in 메뉴들" :key="i"> {{ menu }} </a>
  </div>

  <div v-for="(a, i) in 원룸들" :key="i">
    <img :src="원룸들[0].image" class="room-img" />
    <h4>{{ 원룸들[0].title }}</h4>
    <P>{{ 원룸들[0].price }}원</P>
    <!-- <button @click="신고수[0]++">허위매물신고</button>
    <span>신고수 : {{ 신고수[0] }}</span> -->
  </div>
  <div>
    <img :src="원룸들[1].image" class="room-img" />
    <h4>{{ 원룸들[1].title }}</h4>
    <P> {{ 원룸들[1].price }}</P>
  </div>
  <div>
    <img :src="원룸들[2].image" class="room-img" />
    <h4>{{ 원룸들[2].title }}</h4>
    <P> {{ 원룸들[2].price }}</P>
  </div>
</template>

<script>
import data from "./assets/oneroom.js";

export default {
  name: "App",
  data() {
    return {
      원룸들: data,
      모달창열렸니: false,
      신고수: [0, 0, 0],
      메뉴들: ["Home", "Shop", "About"],
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
    };
  },

  // methods: {
  //   increase() {
  //     this.신고수 += 1;
  //   },
  // },

  components: {},
};
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
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
