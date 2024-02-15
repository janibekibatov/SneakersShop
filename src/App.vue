<script setup>
  import { onMounted, reactive, ref, watch } from 'vue';
  //import { watch } from 'vue';
  import axios from 'axios';

  import Header from './components/Header.vue';
  import CardList from './components/CardList.vue';
  import Drawer from './components/Drawer.vue';

  const items = ref([])

  const filters = reactive({
    sortBy: '',
    searchQuery: '',
  })


  const onChangeSelect = (event) => {
    filters.sortBy = event.target.value
  }

  const fetchItems = async() => {
    try {
      const params = {
        sortBy: filters.sortBy,
        searchQuery: filters.searchQuery,
      }

      const {data} = await axios.get(`https://80bcf298c517c9bf.mokky.dev/items?title=*${filters.searchQuery}*&sortBy=${filters.sortBy
      }`)
      
      items.value = data
    } catch(err) {
      console.log(err)
    }
  }

  onMounted(fetchItems)

  watch(filters, fetchItems)
</script>

<template>
  <!-- <Drawer/> -->
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-14">
    <Header/>
    
    <div class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold mb-8">All Sneakers</h2>

        <div class="flex gap-4">
          <select @change="onChangeSelect" class="py-2 px-3 border rounded-md outline-none">
            <option value="name">By Name</option>
            <option value="price">By Price(Cheap)</option>
            <option value="-price">By Price(Expensive)</option>
          </select>

          <div class="relative">
            <img class="absolute left-4 top-3" src="/search.svg" alt="Search">

            <input class="border rounded-md py-2 pl-11 pr-4 outline-none focus:border-gray-400" type="text" placeholder="Search"/>
          </div>
        </div>

        
      </div>
      

      <CardList :items="items"/>
    </div>
    

  </div>
</template>

<style scoped>

</style>
