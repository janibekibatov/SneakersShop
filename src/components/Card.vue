<script setup>
    defineProps({
        imageUrl: String,
        title: String,
        price: Number,
        isFavorite: Boolean,
        isAdded: Boolean,
        onClickAdd: Function,
        onClickFavorite: Function,
    })

    // const onClickAdd = () => {
    //   alert(1)
    // }
</script>

<template>
    <div class="relative bg-white border border-slate-100 rounded-3xl p-8 cursor-pointer hover:-translate-y-2 hover:shadow-xl transition">
        <!-- <img src="/like-2.svg" alt="Like 1" class="absolute top-8 left-8"> -->
        <img @click="onClickFavorite" :src="!isFavorite ? '/like-1.svg' : '/like-2.svg'" alt="Like 1" class="absolute top-8 left-8">
        <img :src="imageUrl" alt="Sneaker">
        <p class="mt-2">{{ title }}</p>

        <div class="flex justify-between mt-5">
          <div class="flex flex-col">
            <span class="text-slate-400">Price:</span>
            <b>{{ price }} tg</b>
          </div>
          <img @click="onClickAdd" :src="!isAdded ? '/plus.svg' : 'checked.svg'" alt="Plus">
        </div>
      </div>
</template>