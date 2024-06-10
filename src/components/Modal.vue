<template>
  <!-- 모달창 -->
  <div class="modal-wrapper" :class="{ 'is-toggle': isToggle }">
    <div class="modal">
      <p class="modal-ttl">{{ aptData[clicked].title }}</p>
      <div class="modal-txt">{{ aptData[clicked].price }}</div>
      <button type="button" @click="$emit('closeModal')">버튼</button>
      <!-- <button type="button" @click="isToggle = !isToggle">버튼</button> -->
    </div>
    <div class="modal-bg" @click="$emit('closeModal')"></div>
    <!-- <div class="modal-bg" @click="isToggle = !isToggle"></div> -->
  </div>
</template>

<script>
export default {
  name: "Modal",
  props: {
    aptData: Array,
    clicked: Number,
    isToggle: Boolean, // true, false
  },
  methods: {
    sendToggle() {
      // 위에 있는 props, data, $변수든 밑에서 다시 쓰는 경우 this를 붙인다
      // $emit 함수 안에서 쓰고 싶으면 this.$emit()
      this.$emit("isToggle", this.aptData.id);
    },
  },
};
</script>

<style></style>
