<script setup>
import { reactive, ref, onMounted, watch } from 'vue'
import TheHeader from '@/components/TheHeader.vue'
import CardList from '@/components/CardList.vue'
import Drawer from '@/components/Drawer.vue'
import axios from 'axios'

const items = ref([])

const filters = reactive({
  sortBy: 'title',
  searchQuery: ''
})
const OnChangeSelect = (event) => {
  filters.sortBy = event.target.value
}

const OnChangeSearchInput = (event) => {
  console.log(filters.searchQuery)
  console.log(event.target.value)
  filters.searchQuery = event.target.value
}
const fetchItems = async () => {
  try {
    const params = {
      sortBy: filters.sortBy
    }
    if(filters.searchQuery) {
      params.title = `*${filters.searchQuery}*`
    }
    const { data } = await axios.get('https://b340a1812fbe2047.mokky.dev/items', {
      params
       
    })
    items.value = data
  } catch (err) {
    console.log(err)
  }
}
// onMounted(() => {
// fetch('https://b340a1812fbe2047.mokky.dev/items')
// .then((res) => res.json())
// .then((data) => {
// console.log(data)
// })
// axios.get('https://b340a1812fbe2047.mokky.dev/items').then((resp) => console.log(resp.data))

// ;}
onMounted(
  fetchItems

  // async () => {
  //   try {
  //     const { data } = await axios.get('https://b340a1812fbe2047.mokky.dev/items')
  //     items.value = data
  //     console.log(data)
  //   } catch (err) {
  //     console.log(err)
  //   }
  // }
)
watch(filters, fetchItems)
</script>

<template>
  <!-- <Drawer/> -->
  <div class="w-4/5 m-auto bg-white rounded-xl shadow-xl mt-20">
    <TheHeader />
    <div class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold mb-8">Все кроссовки</h2>
        <div class="flex gap-4">
          <select
            @change="OnChangeSelect"
            class="py-2 px-3 border rounded-md outline-none"
            name=""
            id=""
          >
            <option value="name">По названию</option>
            <option value="price">По цене(дешевые)</option>
            <option value="-price">По цене(дорогие)</option>
          </select>
          <div class="relative">
            <img class="absolute left-4 top-3" src="/search.svg" alt="" />
            <input
              @input="OnChangeSearchInput"
              class="border rounded-md py-2 pl-11 pr-4 outline-none focus:border-gray-400"
              type="text"
              placeholder="поиск..."
            />
          </div>
        </div>
      </div>
      <div class="mt-10">
        <CardList :items="items" />
      </div>
    </div>
  </div>
</template>

<style scoped></style>
