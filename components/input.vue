<script setup lang="ts">
import {ref, watch, computed} from 'vue'

const inputFoo = ref(10)
const inputBar = ref(5)
const baz = ref(0)
const multiplier = ref(1)

watch([inputFoo, inputBar], () => {
  baz.value = inputFoo.value + inputBar.value
},{ immediate:true })

const result= computed(() => {
  return baz.value * multiplier.value
})

function reset() {
  inputFoo.value = 10
  inputBar.value = 5
  baz.value = 0
  multiplier.value = 1
}

</script>

<template>
  <div class="flex flex-col">
    <div class="flex gap-10">
      <div class="flex flex-col gap-2">
        <div class="inline-flex gap-4 items-center pl-4 b b-yellow-300 bg-yellow-100 c-yellow-900 w-fit rd">
          <label for="foo" class="font-bold text-2xl">B</label>
          <input v-model.number="inputFoo" id="foo" type="text" class="p-2 bg-yellow-200 focus:ring-4 transition outline-none">
        </div>
        <span class="text-center text-xl font-semibold rd-full b bg-red-50 c-red-900 w-fit mx-auto px-2">+</span>
        <div class="inline-flex gap-4 items-center pl-4 b b-yellow-300 bg-yellow-100 c-yellow-900 w-fit rd">
          <label for="bar" class="font-bold text-2xl">C</label>
          <input v-model.number="inputBar" id="bar" type="text" class="p-2 bg-yellow-200 focus:ring-4 transition outline-none">
        </div>
      </div>

      <div class="flex flex-col b b-teal-300 c-teal-900 gap-4 items-center py-2 px-4 bg-teal-100 w-fit rd">
        <label class="font-bold text-2xl">A</label>
        <p >{{ result }}</p>
      </div>
    </div>

    <button class="bg-blue-200 b b-blue-300 c-blue-900 font-medium shadow hover:bg-blue-100 transition outline-none
    active:bg-blue-50 focus:ring-2 mt-4 px-3 py-1.5 rd-md" @click="multiplier+=1">Multiplier x{{ multiplier }}</button>

    <button class="bg-gray-100 c-gray-900 b b-gray-200 mt-2 w-30px rd-full hover:bg-gray-200 focus:bg-gray-300
    transition outline-none focus:ring" @click="reset">
      <ph-arrows-counter-clockwise class="w-1em h-1em" />
    </button>
  </div>
</template>

<style scoped>
input {
  max-width: 80px;
  width: 100%;
}
</style>
