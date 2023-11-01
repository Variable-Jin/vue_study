<template>
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <img :src="원룸들[누른거].image" style="width: 50%" />
      <h4>{{ 원룸들[누른거].title }}</h4>
      <p>{{ 원룸들[누른거].content }}</p>
      <input v-model="month" />

      <p>{{ month }}개월 선택함 : {{ 원룸들[누른거].price * month }} 원</p>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ModalComponent",
  data() {
    return {
      month: 1,
    };
  },

  beforeUpdate() {
    if (this.month == 2) {
      alert("다시 선택하여 주십시오");
      this.month = 3;
    }
  },

  watch: {
    month(a) {
      if (isNaN(a) == true) {
        alert("문자 입력은 불가합니다");
        this.month = 1;
      }
    },
  },

  props: {
    원룸들: Array,
    누른거: Number,
    모달창열렸니: Boolean,
  },
};
</script>

<style></style>
