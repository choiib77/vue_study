<template>
  <div class="modal" v-if="모달창 == true">
    <div class="modal-con">
      <h4>{{상품정보[상품번호].title}}</h4>
      <img :src="상품정보[상품번호].image" alt="" class="good-img" @click="closeModal">
      <p>{{상품정보[상품번호].content}}</p>
      <p>{{상품정보[상품번호].price}}원</p>
      <p><input v-model.number="count" type="number"></p>
      <p>총금액 :{{count + 상품정보[상품번호].price }} 원</p>
      <button @click="closeModal">닫기</button>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'ModalWindow',
    props: {
      상품정보: Array,
      상품번호: Number,
      모달창: Boolean
    },
    data(){
      return {
        count: 0
      }
    },
    watch:{
      count(vv){
        if(isNaN(vv) == true){
          alert('숫자만 입력이 가능합니다.')
          this.count=0;
        }
      }
    },
    methods: {
      closeModal() {
        this.$emit('closeModal');
      }
    }
  }
</script>

<style scoped>
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