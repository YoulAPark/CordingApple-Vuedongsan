<template>
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
        <img :src="원룸들[누른거].image" class="room-img">
        <h4 >{{원룸들[누른거].title}}</h4>
        <p>{{원룸들[누른거].content}}</p>
        <input v-model="month"/>
        <p> {{month}}개월 : {{원룸들[누른거].price * month}} 원</p>
        <button @click="$emit('closeModal' )">닫기</button>
        <Discount/>
    </div>
  </div>
</template>

<script>
export default { 
    name : 'ModalPage',
    data() {
      return {
        month : 1,
      }
    },
    watch : {
      month(i) {
        var num = /[0-9]/;
        if (num.test(i)==false) {
          alert("실패")
        }
        // if(i>12) {
        //   alert("할부는 12개월 이하만 가능합니다.")
        //   this.month = 1;
        // } else if (isNaN(i) == true) {
        //   alert("숫자만 입력가능합니다.")
        //   this.month = 1;
        // }
        function a(2)
      },
    },
    props : {
        원룸들 : Array,
        누른거 : Number,
        모달창열렸니 : Boolean,
    },
}
</script>

<style>

</style>