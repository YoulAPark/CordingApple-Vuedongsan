<template>
  <div class="discount">
    <p>지금 결제하면 {{ salePercent }}% 할인</p>
  </div>
</template>

<script>
export default {
    name : 'Discount-A',
    data() {
      return {
        salePercent : 5,
      }    
    },
    mounted() {
      setInterval(()=> {
      this.salePercent --;
      }, 1000);
    },
}
</script>

<style>

</style>