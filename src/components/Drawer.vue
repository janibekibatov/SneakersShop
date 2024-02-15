<script setup>
import DrawerHead from './DrawerHead.vue';
import CardItemList from './CardItemList.vue';
</script>

<template>
    <div class="fixed top-0 left-0 h-full w-full bg-black z-10 opacity-70"></div>
    
    <div class="bg-white w-96 h-full fixed right-0 top-0 z-20 p-8">
        <DrawerHead/>

       <CardItemList/>

       <div class="flex flex-col gap-4 mt-7">
            <div class="flex gap-2">
                <span>Total:</span>
                <div class="flex-1 border-b border-dashed"></div>
                <b>15990 tg</b>
            </div>

            <div class="flex gap-2">
                <span>Tax:</span>
                <div class="flex-1 border-b border-dashed"></div>
                <b>1000 tg</b>
            </div>

            <button disabled class="transition mt-4 disabled:bg-slate-300 bg-lime-500 w-full text-white rounded-xl py-3 hover:bg-lime-600 active:bg-lime-700 cursor-pointer">
            Make order
            </button>
       </div>

       
    </div>
</template>