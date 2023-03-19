<template>
  <div>
    <ModalCompo @closeModal="modalFlag=false" :products="products" :modalFlag="modalFlag" :checkNum="checkNum"/>

    <div class="menu">
      <a v-for= "a in menus" :key="a">{{ a }}</a>
    </div>

    <DiscountCompo/>
    <button @click="priceSort" >sort by price</button>
    <button @click="originalShow" >Original display</button>

    <CardCompo v-for="(작명,i) in products" :key="작명" :products="products[i]" :modalFlag="modalFlag" :checkNum="checkNum" @openModal="modalFlag=true" />
    
  </div>
</template>

<script>
import data from './assets/oneroom.js'
import DiscountCompo from './components/DiscountCompo.vue'
import ModalCompo from './components/ModalCompo.vue'
import CardCompo from './components/CardCompo.vue'

export default {
  name: 'App',
  data(){
    return{
      originalData: [...data],
      products: data,
      menus:['Home','about','page'],
      reportNum:[0,0,0],
      modalFlag: false,
      checkNum: 0,
    }
  },
  components: {
    DiscountCompo,
    ModalCompo,
    CardCompo
  },
  methods:{
    priceSort(){
      this.products.sort(function(a,b){
        return a.price - b.price;
      })
    },
    originalShow(){
      this.products = this.originalData;
    }
  }
}
</script>

<style>

div{
  box-sizing: border-box;
}
.black-bg{
  width: 100%; height: 100%;
  background: rgba(0, 0,0, 0.5);
  position: fixed; padding: 20px;
}
.white-bg{
  width: 100%; 
  background: white;
  border-radius: 8px; padding: 20px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
  
}
.menu a{
  color: white;
  padding: 10px;
}
.room-img{
  width: 100%;
  margin-top: 40px;
}
.modal-img{
  width: 50%;
}

</style>
