<template>
  <div class="black-bg" v-if="modalFlag">
      <div class="white-bg">
        <img :src="products[checkNum].image" style="width:100%"/>
        <h4>{{products[checkNum].title}}</h4>
        <p>{{products[checkNum].content}}</p>
        <p>{{products[checkNum].price * month}}won</p>
        Month: <input v-model.number="month" @keyup.space="checkSpaceBar"/>
        <DiscountCompo />
        <button @click="$emit('closeModal')">X</button>
      </div>
    </div>
</template>

<script>
import DiscountCompo from './DiscountCompo.vue'

export default {
    name:'ModalCompo',
    data(){
      return{
        month:1
      }
    },
    props:{
        products:Array,
        modalFlag:Boolean,
        checkNum:Number
    },
    watch:{
      month(inputValue){
        if(isNaN(inputValue)==true ){
          alert("Number needed");
          this.month = 1;
        }
      }
    },
    components: {
    DiscountCompo,
  },
  methods:{
    checkSpaceBar(){
      alert("spacebar is not allowed")
      this.month =1;
    }
  }
}
</script>

<style>

</style>