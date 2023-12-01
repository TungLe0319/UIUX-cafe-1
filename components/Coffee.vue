<template>
  <div class="grid grid-cols-4 gap-4 p-10 bg-zinc-900">
    <div v-for="item in items" class=" transition-all duration-200 hover:scale-[1.05] relative">
      <img :src="item.src" alt="coffee cup icon" class="rounded-md shadow-2xl w-full h-full object-cover">
      <div
        class="absolute top-0 left-0 w-full h-full flex items-center justify-center opacity-0 hover:opacity-100 transition-opacity duration-300  bg-black/50 p-4">
        <p class="text-white text-lg font-Bold">
          {{ item.title  }}
        </p>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
const items = [
  {
    src: 'https://images.unsplash.com/photo-1517701550927-30cf4ba1dba5?q=80&w=1287&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
    title:'Iced Coffee'
  },
  {
    src: 'https://images.unsplash.com/photo-1530373239216-42518e6b4063?q=80&w=1287&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
    ,  title: 'Caramel Mocha Oreo Frappe'
  },
  { src: 'https://images.unsplash.com/photo-1549652127-2e5e59e86a7a?q=80&w=1287&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
    , title: 'Cold Brew' }
  ,
  { src: 'https://images.unsplash.com/photo-1562878424-0da674456d33?q=80&w=1287&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D', title: 'Cold Brew Plain' }
  ,
  { src: 'https://images.unsplash.com/photo-1561817245-de553dfe2e88?q=80&w=1288&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D', title: 'Vegan Chocolate Cupcakes' }
  ,
  { src: 'https://images.unsplash.com/photo-1586657263857-346c4b712ff5?q=80&w=1364&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
    , title: 'Croissants' }
  ,
  { src: 'https://images.unsplash.com/photo-1627308595260-6fad84c40413?q=80&w=1335&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D', title: 'Bagels' }
  ,
  { src: 'https://images.unsplash.com/photo-1645621479479-4ebaa3dbf801?q=80&w=1227&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D', title: 'Avocado Toast' }
  ,

]
</script>

<style scoped>
img {
  width: 100%;
  height: 25rem;
  object-fit: cover;

}

/* Add this to your existing stylesheet */


.hover\:scale-105:hover {
  transform: scale(1.05);
}
</style>