<template>
  <div class="modal" v-if="모달창 == true" >
    <div class="modal-con">
      <h4>상세페이지</h4>
      <img :src="모달이미지" alt="" class="good-img" @click="closeModal">
      <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Optio enim voluptate nam quasi aliquam officia
        suscipit blanditiis consequuntur porro, obcaecati voluptatem perspiciatis ratione saepe eaque, nesciunt impedit
        quia animi aspernatur.</p>
    </div>
  </div>
  <div class="menu">
    <a v-for=" (메뉴,index) in 메뉴배열" v-bind:key="index">{{메뉴}}</a>
  </div>
  <div v-for="(제품,index) in 제품명" :key="index">
    <h4 @click="showModal(index)" :style="스타일">{{제품}}</h4>
    <img :src="이미지배열[index]" alt="" class="good-img">
    <p>{{price[index]}}만원</p>
    <button @click="increment(index)">허위매물신고</button>
    <span :style="스타일">신고수:{{신고수[index]}}</span>
  </div>
  <div>
  </div>
</template>

<script>
  export default {
    name: 'App',
    data() {
      return {
        price: [5, 4, 10, 0.6, 1.2],
        스타일: 'color:red',
        제품명: ['사과', '딸기', '귤', '토마토', '고구마'],
        메뉴배열: ['Home', 'Shop', 'About'],
        신고수: [0, 0, 0, 0, 0],
        이미지배열: [require('./assets/사과.jpg'), require('./assets/딸기.jpg'), require('./assets/귤.jpg'), require(
          './assets/토마토.jpg'), require('./assets/고구마.jpg')],
        모달창: false,
      }
    },
    methods: {
      increment(_index) {
        this.신고수[_index]++;
      },
      showModal(_index){
        this.모달이미지 = this.이미지배열[_index];
        this.모달창=true;
      },
      closeModal(){
        this.모달창=false;
      }
    },
    components: {}
  }
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }

  .menu {
    position: relative;
    display: block;
    padding: 15px;
    background: lightblue;
    border-radius: 5px;
  }

  .menu a {
    color: #fff;
    text-decoration: none;
    padding: 10px;
    text-transform: uppercase;
  }

  .good-img {
    width: 100%;
    margin-top: 10px;
  }

  .modal {
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    padding: 20px;
    box-sizing: border-box;
    z-index: 999;
  }

  .modal-con {
    position: relative;
    display: block;
    width: 100%;
    border-radius: 10px;
    background: #fff;
    padding: 20px;
    box-sizing: border-box;
  }
</style>