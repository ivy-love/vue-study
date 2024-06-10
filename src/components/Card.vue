<template>
  <!-- 컨텐츠 -->
  <div class="list" @click="sendToggle">
    <img :src="aptData.image" class="img" />
    <h4>{{ aptData.title }}</h4>
    <p>{{ aptData.price }}</p>
  </div>

  <!-- <div class="list" v-for="(item, i) in aptData" :key="item">
    <img :src="aptData[i].image" :alt="`룸 이미지${i}`" class="img" />
    <h4>{{ aptData[i].title }}</h4>
    <p>{{ aptData[i].price }}</p>
  </div> -->
</template>

<script>
export default {
  name: "Card",
  props: {
    aptData: Object, // 코드가 길어지면 자료형 틀려서 생기는 버그가 매우 많음
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
