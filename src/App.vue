<template>
<transition name="fade">
<ModalWindow @closeModal="closeModal" :상품정보="상품정보" :상품번호="상품번호" :모달창="모달창"/>
</transition>
  <div class="menu">
    <a v-for=" (메뉴,index) in 메뉴배열" v-bind:key="index">{{메뉴}}</a>
  </div>

  <Discount/>
  <div>
    <button @click="sortPrice()">가격순정렬</button>
    <button @click="sortBasic()">기본값정렬</button>
  </div>
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
        상품정보 : [...상품데이터],
        원본정보: [...상품데이터],
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
      },
      sortPrice(){
        this.상품정보.sort(function(a,b){
          return a.price - b.price
        });
      },
      sortBasic(){
        this.상품정보 = this.원본정보;
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

 .fade-enter-from,
  .fade-leave-to{
   opacity: 0;
   transform: translateY(-300px);
 }
 .fade-enter-active,
  .fade-leave-active{
   transition: opacity .5s, transform .5s;
 }
 .fade-enter-to,
  .fade-leave-from{
   opacity: 1;
      transform: translateY(0);
 }

</style>