<template>
  <div v-for="task in data" >
    <KeepCard :title="task.task_name" 
              :value="task.task_value"
              :total="task.task_total_value"
              :tag="task.task_tag"
              :unit="task.task_unit"
              :icon="task.task_icon"
              @click="openModel(task.task_id)"
    />
  </div>
  <div v-if="isopen" class=" absolute bg-slate-200/50 w-full top-0 left-0 h-full flex justify-center align-middle ">
    <div class=" relative top-[25%] w-[50%] h-fit bg-slate-200 flex flex-col p-2">
      <div class="text-xl mb-2">
        🈶  {{ modelData }} {{ model_id }}
      </div>
      <div class=" relative mb-2">
        <input type="number" class=" outline-none  w-full rounded-md px-2"  v-model="inputValue"   >
      </div>
      <div>
        <button class=" bg-blue-400 rounded-md px-2 shadow-md border-2 border-black w-full select-none cursor-pointer"   @click="valueAdd(model_id)">#打</button>
      </div>
      <span class=" absolute right-2 top-2 w-fit h-fit bg-red-400 px-2 rounded-sm select-none cursor-pointer " @click="isopen = !isopen" >X</span>
    </div>
  </div>
</template>


<script setup>
import { reactive, ref } from 'vue';
import KeepCard from './components/KeepCard.vue';



const isopen = ref(false)
const inputValue = ref(0)
const data = reactive([
  {
    task_id:'ukjsdkfj123',
    task_tag: "keep",
    task_icon:"🈯",
    task_name:"多喝水",
    task_value:0,
    task_total_value:3000,
    task_unit:'ML'
  },
  {
    task_id:'1231325435',
    task_tag: "keep",
    task_icon:"🈵",
    task_name:"多吃饭",
    task_value:0,
    task_total_value:3,
    task_unit:'餐'
  },

])

const modelData =ref('Title')
const model_id = ref('')

const openModel = (id) =>{
  const res = data.find((item)=>{
    if(item.task_id === id)
    {
      return item
    }
    
  })
  modelData.value = res.task_name
  model_id.value = res.task_id
  isopen.value = !isopen.value
}

const valueAdd = (id) =>{
  data.find((item)=>{
    if(item.task_id === id)
    item.task_value = item.task_value + inputValue.value
  })
  inputValue.value = 0
  isopen.value = !isopen.value
  model_id.value = ''
}

</script>