<!-- HTMl -->
<template> 



<transition name="fade"> 
  <Modal @closeModal="모달창열렸니=false" :원룸들="원룸들" :누른거="누른거" :모달창열렸니="모달창열렸니"/>
</transition>

<!-- 반복문 사용 --> 
<div class="menu" >
  <a v-for="Item in 메뉴들" :key="Item">{{Item}}</a> 
</div>

<Discount/>

<button @click="priceSortLow">가격낮은순정렬</button><br>
<button @click="priceSortHigh">가격높은순정렬</button><br>
<button @click="prodNameSort">가격이름순정렬</button><br><br>
<button @click="sortBack">되돌리기</button>

<Card @openModal="모달창열렸니=true; 누른거=$event" :원룸들="원룸들[i]" v-for="(원룸,i) in 원룸들" :key="원룸"/>

</template>

<!-- Java Script -->
<script>

import data from './assets/data.js';
import Discount from './Discount.vue';
import ModalPage from './Modal.vue';
import CardPage from './Card.vue';
import TestPage from './Test.vue';

export default {
  name: 'App',
  data() {
    return {
      원룸들오리지널 : [...data],
      누른거 : 0, // 사용자가 지금 누른 상품의 번호를 기록
      원룸들 : data, 
      모달창열렸니 : false,
      신고수 : [0,0,0],
      메뉴들 : ['Home', 'Shop', 'Products', 'About'],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
    }
  },
  methods : {
    increase() {
      this.신고수++;
    },
    priceSortLow() {
      this.원룸들.sort(function(a,b) {
        return a.price - b.price       
      });
    },
    priceSortHigh() {
      this.원룸들.sort(function(a,b) {
        return b.price - a.price
      }); 
    },
    prodNameSort() {
      this.원룸들 = [...this.원룸들오리지널].sort(function(a,b){
        if (a.title > b.title) {
          return 1;
        } else if (a.title < b.title) {
          return -1;
        }
        return 0;
      });
    },
    sortBack() {
      this.원룸들 = [...this.원룸들오리지널]; // 오른쪽을 왼쪽에 집어넣어주세요
    },
  },
  components : {
    Discount : Discount,
    Modal : ModalPage,
    Card : CardPage,
    Test : TestPage,
  }
}
</script>

<!-- Style -->
<style>
.fade-enter-from { /* 애니메이션 시작시 스타일*/
  transform : translateY(-1000px);
} 
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to { /* 애니메이션 끝날시 스타일 */
  transform : translateY(-0px);
} 

.fade-leave-from { /* 애니메이션 시작시 스타일*/
  opacity: 1;
} 
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to { /* 애니메이션 끝날시 스타일 */
  opacity: 0;
} 

.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}

body {
  margin : 0
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0, 5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background : white;
  border-radius: 8px;
  padding : 20px;
}

.room-img {
  width : 100%;
  margin-top : 40px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background : darkslateblue;
  padding : 15px;
  border-radius: 5px;
}

.menu a{
  color : white;
  padding: 10px;
}
</style>
