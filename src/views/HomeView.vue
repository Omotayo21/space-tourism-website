<template>
    <div class="w-full absolute inset-0">
        <img src='@/assets/home/background-home-desktop.jpg'  alt="Home desltop background"
        class="sm:hidden md:hidden lg:block w-full h-full object-cover "
        />
 <img src='@/assets/home/background-home-mobile.jpg'  alt="Home desltop background"
        class="lg:hidden md:hidden sm:block w-full h-full object-cover "
        />
        <img src='@/assets/home/background-home-mobile.jpg'  alt="Home desltop background"
        class="lg:hidden sm:hidden md:block w-full h-full object-cover "
        />
        <div class="flex flex-col items-center justify-center">
      <div class="flex lg:flex-row sm:flex-col absolute lg:bottom-20 md:bottom-28 sm:bottom-8 lg:gap-x-64 sm:items-center sm:justify-center sm:gap-y-28 sm:mt-8">
         <div class="flex flex-col lg:gap-y-8 sm:gap-y-8 md:gap-y-16 lg:items-start sm:items-center sm:justify-center md:items-center md:justify-center ">
 <p class="lg:text-lg sm:text-lg md:text-4xl text-white">So, you want to travel to</p>
  <h1 class="uppercase lg:text-7xl md:text-9xl sm:text-7xl text-white font-serif">space</h1> 
 <p class="text-white md:mx-auto md:text-center lg:text-start sm:mx-auto sm:text-center lg:w-[27.5rem] sm:w-[20rem] md:w-[40rem] text-sm">Let&apos;s face it; if you want to go to space, you might as well genuinely go to outer space and not hover kind of on the edge of it. Well sit back, and relax because we’ll give you a truly out of this world experience! </p>

         </div>
         <h2 class="bg-white rounded-full text-center lg:py-16 uppercase font-serif lg:h-40 lg:w-40 sm:h-40 sm:w-40 sm:py-16  md:h-64 md:w-64 md:py-28 ">Explore</h2>
      </div>
      </div>
    </div>
</template>

<script>


export default {
  name: 'HomeView',
  
}

</script>