<script setup>
import { RouterLink, RouterView } from 'vue-router'
import {ref} from 'vue'
import HomeView from '@/views/HomeView.vue'
const isSidebarOpen = ref(false);

// Function to toggle sidebar visibility
const toggleSidebar = () => {
  isSidebarOpen.value = !isSidebarOpen.value;
};

</script>

<template>
  <header>

    <div class=" ">
   

      <nav class="sm:flex sm:flex-row sm:gap-x-4 sm:justify-between">
      <div   class="" >
      <img src="@/assets/shared/logo.svg" alt="logo" class="w-8 h-8 z-40 absolute lg:mt-12 ml-12 sm:mt-6 " />
 <img
            v-if="!isSidebarOpen"
            src="@/assets/shared/icon-hamburger.svg"
            alt="list"
            class="w-8 h-8 z-40 absolute  lg:hidden md:hidden sm:block sm:right-8 sm:mt-6 cursor-pointer"
            @click="toggleSidebar"
          />

          <!-- Close Icon -->
         

    </div>      
        <div class="blur-background lg:mt-12  lg:flex lg:flex-row md:flex md:flex-row  gap-x-12 lg:fixed lg:right-0 text-white z-20 font-barlow-condensed px-16 md:bg-opacity-50 sm:hidden md:hiddden  ">
        <RouterLink to="/" class="flex flex-row gap-4 py-6  hover:border-b-4 hover:border-gray-200"
        active-class="border-b-4 border-red-600" exact-active-class="border-b-4 border-white"><span>00</span>Home</RouterLink>
        <RouterLink to="/destination" class="flex flex-row gap-4 py-6  hover:border-b-4 hover:border-gray-200"  active-class="border-b-4 border-white" exact-active-class="border-b-4 border-white"><span>01</span>Destination</RouterLink>
        <RouterLink to="/crew" class="flex flex-row gap-4 py-6  hover:border-b-4 hover:border-gray-200"  active-class="border-b-4 border-white" exact-active-class="border-b-4 border-white" ><span>02</span>Crew</RouterLink>
        <RouterLink to="/technology" class="flex flex-row gap-4 py-6  hover:border-b-4 hover:border-gray-200"  active-class="border-b-4 border-white" exact-active-class="border-b-4 border-white"><span>03</span>Technology</RouterLink>
      </div>
       <div  v-if="isSidebarOpen" class="blur-background  pt-8 flex flex-col z-30   gap-y-12 lg:fixed right-0 text-white  font-barlow-condensed pl-2 md:bg-opacity-50 lg:hidden sm:h-screen md:h-screen  ">
        <img
            v-if="isSidebarOpen"
            src="@/assets/shared/icon-close.svg"
            alt="close"
            class="w-8 h-8 z-30 absolute lg:hidden md:hidden sm:block right-4 m  cursor-pointer"
            @click="toggleSidebar"
          />
        <div class="mt-16 flex flex-col gap-y-10"><RouterLink to="/" class="flex flex-row gap-2 pr-12  hover:border-r-4 hover:border-gray-200"
        active-class="border-r-4 border-red-600" exact-active-class="border-r-4 border-white"><span class="font-bold">00</span>Home</RouterLink>
        <RouterLink to="/destination" class="flex flex-row gap-2 pr-12  hover:border-r-4 hover:border-gray-200"  active-class="border-r-4 border-white" exact-active-class="border-r-4 border-white"><span class="font-bold">01</span>Destination</RouterLink>
        <RouterLink to="/crew" class="flex flex-row gap-2 pr-12 hover:border-r-4 hover:border-gray-200"  active-class="border-r-4 border-white" exact-active-class="border-r-4 border-white" ><span class="font-bold">02</span>Crew</RouterLink>
        <RouterLink to="/technology" class="flex flex-row gap-2 pr-12  hover:border-r-4 hover:border-gray-200"  active-class="border-r-4 border-white" exact-active-class="border-r-4 border-white"><span class="font-bold">03</span>Technology</RouterLink>
     </div> </div>
    </nav>
    </div>
  </header>
<main><RouterView /></main>
  
</template>

<style scoped>
.blur-background {
  backdrop-filter: blur(70px);
 
}
@media (min-width: 760px) {
  .blur-background {
  backdrop-filter: blur(70px);
 
}
}


</style>
