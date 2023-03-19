<template>
    <div>
      <img :src="products.image" class="room-img" />
      <h4 @click="$emit('openModal',products.id)">{{ products.title }}</h4>
      <p>{{ products.price}}</p>
    </div>  
</template>

<script>

export default {
    props:{
        products:Object,
        checkNum: Number,
        modalFlag:Boolean
    }
}
</script>

<style>

</style>