<script setup>
const props = defineProps({
    title:String,
    value:Number,
    total:Number,
    tag:String,
    unit:String,
    icon:String,

})
</script>


<template>
  <div
    class="relative w-full bg-blue-300 h-14 rounded-lg shadow-xl select-none cursor-pointer my-2"
    
  >
    <div class="absolute top-[20%] left-2 text-2xl">{{ $props.icon }}</div>
    <p class="absolute top-[20%] left-10 text-2xl">{{$props.title}}</p>
    <p class="absolute top-[25%] right-10 text-lg">{{$props.value}}/{{props.total}}{{ $props.unit }} </p>
  </div>
</template>
