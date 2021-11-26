<template>
<ModalWindow @closeModal="closeModal" :상품정보="상품정보" :상품번호="상품번호" :모달창="모달창"/>
  <div class="menu">
    <a v-for=" (메뉴,index) in 메뉴배열" v-bind:key="index">{{메뉴}}</a>
  </div>

  <Discount/>
  <Card @showModal="showModal($event)" v-for="(item,index) in 상품정보" :key="index" :상품="item" :번호="index"/>

</template>

<script>
import 상품데이터 from './assets/good';
import Discount from './components/Discount.vue';
import ModalWindow from './components/ModalWindow.vue';
import Card from './components/Card.vue';

  export default {
    name: 'App',
    data() {
      return {
        상품정보 : 상품데이터,
        메뉴배열: ['Home', 'Shop', 'About'],
        모달창: false,
        상품번호: 0
      }
    },
    methods: {
      showModal(_index){
        this.상품번호 = _index;
        this.모달창=true;
      },
      closeModal(){
        this.모달창=false;
      }
    },
    components: {
      Discount,
      ModalWindow,
      Card
    }
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

 

</style>