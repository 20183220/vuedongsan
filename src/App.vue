

<template>


<!-- 최상단 메뉴 -->
  <div class = "menu">                
    <a v-for ="(a, i) in 메뉴들" :key = "i">{{a}}</a>
  </div>


<!-- 제목 클릭시 모달 -->
<div v-for="i in 6" :key="i">       
  <div class = "black-bg" v-if="모달창open[i - 1]">
    <div class="white-bg" >
    <div class="close" @click="모달창open[i - 1] = false">
      <h>X</h>
    </div>
      <h4>{{원룸들[i - 1].title}}</h4>
      <p>{{원룸들[i - 1].content}}</p>
    </div>
  </div>
</div>


<!-- 사진들, 제목들, 가격들, 신고버튼 -->
  <div class = "top" v-for="i in 6" :key = "i">   
    <img :src="원룸들[i - 1].image" 
    class = "room" 
    v-bind:class ="{active : toggle}" 
    v-on:click ="toggleE"> 
    <h4 id="title" @click="모달창open[i - 1] = true">{{원룸들[i - 1].title}}</h4>
    <p>{{원룸들[i - 1].price}}원</p>
    <button @click="신고수[i]++">허위매물신고</button> <span>신고수 : {{신고수[i]}}</span>
    sdfdsf
  </div>



</template>

<script>
import data from "./assets/oneroom.js"

export default{
  name:'App',
  data(){
    return{
      모달창open: [false, false, false, false, false, false],
       메뉴들 :['Home', 'Shop', 'Price'], 
       신고수 : [0, 0, 0],
       원룸들 : data, toggle : false
    }
  },

  methods : {
    toggleE(){
      this.toggle = !this.toggle
    }
  },

  components:{

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

.menu{
  background : darkslateblue;
  padding : 15px;
  border-radius : 5px;
  width:100%;
  position : fixed;
}
.menu a{
  color:white;
  padding:10px; 
}
.room{
  width : 50%;
  margin-top: 30px;
  transition : 1s;
  cursor : pointer;
}
.room.active{
  width:65%;
}
body{
  margin:0;
}
div{
  box-sizing : border-box;
}
.black-bg{
  width : 100%; height:100%;
  background:rgba(0, 0, 0, 0.5);
  position : fixed; padding :20px;
  transition:0.5s;
}
.white-bg{
  width :100%;
  background:white;
  border-radius: 8px; padding : 20px;
}
.top{
  padding-top :40px;
}
.close{
  text-align:right;
  color:black;
  cursor : pointer;
}
#title{
  cursor:pointer;
}
button{
  cursor:pointer;
}
</style>
