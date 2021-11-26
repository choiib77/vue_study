<template>

    <div>
        <h4 @click="$emit('showModal',번호)" :style="스타일">{{상품.title}}</h4>
        <img :src="상품.image" alt="" class="good-img">
        <p>{{상품.price}}원</p>
    </div>

</template>

<script>
    export default {
        name: 'Card',
        props: {
            상품: Object,
            번호: Number
        },
        showModal() {
            this.$emit('showModal', this.번호)
        }
    }
</script>

<style>

</style>