<!-- 

html 속성 안에서 데이터 바인딩할 때는 앞에 :을 붙여준다
:src, :바인딩이름

답보지 말고 다시 만들어보기 

각각의 이미지, 상세내용, 금액 등 노출해보기



props:
- 데이터는 한 곳에 보관함,
그리고 필요하면 가져다가 쓰는데
그것이 바로 props임.

- props는 읽기전용 read-only임. 받아온 걸 수정하면 안 됨(부등호 표시로 하면 안됨)

- props 데이터를 컴포넌트에 넣어두면 되는 거 아닌가 라는 의문이 있을 수 있는데
최상위 부모도 쓰는 데이터라면 최상위 부모 컴포넌트에 만들어두는 게 좋음


부모: 컴포넌트를 품어주고 있는 것
자식: 컴포넌트


props 사용법:
1. 데이터 전송(보내기)
2. 데이터 등록
3. 데이터를 가져다가 씀


1. <자식컴포넌트 :작명(데이터이름 = "데이터이름" /> // 데이터이름으로 똑같이 해놓는 게 편함, 콜론은 v-bind, props 전송에도 사용함
2. 자식컴포넌트 안에 
  props: {
    데이터이름(작명): 자료형 이름 (Object, Array, String, Number 등..)
  }



자식컴포넌트에서 데이터 보낼떄 $emit('작명', 데이터)
부모컴포넌트가 수신할 떄 @작명한거=""











-->

<template>
  <div class="wrap">
    <div class="menu">
      <a href="#" class="link" v-for="(item, index) in items" :key="index">{{
        item
      }}</a>
    </div>

    <disData></disData>
    <!-- props 데이터 보내기 -->
    <Modal
      :aptData="aptData"
      :clicked="clicked"
      :isToggle="isToggle"
      @closeModal="isToggle = false"
    ></Modal>

    <Card
      @isToggle="
        isToggle = true;
        clicked = $event; // 자식이 보낸 데이터를 $event로 받음
        // clicked = i; // 자식이 보낸 데이터를 인덱스 번호를 이용해 같으면 불러오게끔 해줌
      "
      v-for="(item, i) in aptData"
      :key="item"
      :aptData="aptData[i]"
    ></Card>

    <!-- <Card
      v-for="(item, i) in aptData"
      :key="item"
      :aptData="aptData"
      :clicked="clicked"
      :isToggle="isToggle"
    ></Card> -->
  </div>
</template>

<script>
import Card from "./components/Card.vue";
import Modal from "./components/Modal";
import data from "./assets/js/aptdata.js";
import disData from "./components/discountData";

export default {
  name: "App",
  components: {
    Card,
    disData,
    Modal,
  },
  data() {
    return {
      isToggle: false,
      clicked: 0, // 클릭한 인덱스값
      aptData: data, // 원룸 데이터
      items: ["Home", "Shop", "About"],
    };
  },

  methods: {
    addNum(index) {
      this.products[index].declNum++; // vue에서 this는 data안에 있는 큰 오브젝트를 뜻함
    },
  },
};
</script>
<style>
.wrap {
  width: 500px;
  margin: 0 auto;
  text-align: center;
}
.menu {
  background-color: darkcyan;
  padding: 15px;
  border-radius: 5px;
}

.discount {
  margin: 10px;
  padding: 10px;
  border-radius: 5px;
  background-color: #ddd;
}

.list {
  overflow: hidden;
  margin-bottom: 50px;
  padding-bottom: 40px;
  border-radius: 10px;
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.08);
}

.list:last-child {
  margin-bottom: 0;
}

.link {
  padding: 10px;
  color: #fff;
}

.img {
  width: 100%;
  height: 300px;
  object-fit: cover;
}

/* 모달창 */
.modal-wrapper {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  width: 100%;
  height: 100%;
  margin: auto;
  pointer-events: none;
  z-index: 100;
  opacity: 0;
  transition: all 0.3s;
}

.modal-wrapper.is-toggle {
  opacity: 1;
  pointer-events: visible;
}

.modal-wrapper.is-toggle .modal-bg {
  opacity: 1;
  pointer-events: visible;
}
.modal-bg {
  position: fixed;
  top: 0;
  right: 0;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 100%;
  margin: auto;
  background-color: rgba(0, 0, 0, 0.4);
  opacity: 0;
  pointer-events: none;
  transition: all 0.3s;
}

.modal {
  z-index: 1;
  position: absolute;
  width: 500px;
  height: 500px;
  border-radius: 10px;
  background-color: greenyellow;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.modal-ttl {
  color: red;
}
</style>
