<template>
  <div class="w-full absolute inset-0">
   <img src='@/assets/destination/background-destination-desktop.jpg' alt="Home desktop background"
      class="sm:hidden md:hidden lg:block w-full h-full object-cover" />
    <img src='@/assets/destination/background-destination-mobile.jpg' alt="Home mobile background"
      class="lg:hidden md:hidden sm:block w-full h-full object-cover" />
    <img src='@/assets/destination/background-destination-mobile.jpg' alt="Home mobile background"
      class="lg:hidden sm:hidden md:block w-full h-full object-cover" />
    
    <div v-if="selectedDestination" class="  destination-details text-white flex lg:flex-row sm:flex-col sm:gap-y-2 items-center justify-center gap-x-48 absolute inset-0">
     
    <div class="flex flex-col lg:gap-y-28 sm:gap-y-8 sm:items-center sm:justify-center sm:mt-8">
        <h2 class="flex flex-row uppercase gap-x-2"><span class="text-gray-300">01</span> Pick your destination</h2>
        <img :src="selectedDestinationImage" :alt="selectedDestination.name" class="lg:w-64 lg:h-64 sm:w-36 sm:h-36 items-center md:w-64 md:h-64 " />
    </div>
      <div class="flex flex-col lg:gap-y-10 sm:gap-y-6 lg:mt-20 sm:mt-4 sm:items-center sm:justify-center">
       <nav class="destination-nav text-white">
      <button
        v-for="destination in destinations"
        :key="destination.name"
        @click="selectDestination(destination)"
        :class="{ active: selectedDestination && selectedDestination.name === destination.name }"
     
      >
        {{ destination.name }}
      </button>
    </nav>
  <h2  class="text-7xl uppercase font-serif sm:text-center">{{ selectedDestination.name }}</h2>
      <p class=" text-sm text-gray-200 lg:w-[27rem] sm:w-[20rem] md:w-[28rem] sm:text-center">{{ selectedDestination.description }}</p>
      <div class="flex lg:flex-row lg:gap-x-20 sm:flex-col md:flex-row md:gap-x-36 sm:gap-y-4 sm:items-center sm:justify-center">
      <p class="flex flex-col"><strong class="font-thin text-sm sm:text-center "> Avg. Distance</strong> <span class="text-xl  uppercase font-serif">{{ selectedDestination.distance }}</span></p>
      <p class="flex flex-col"><strong class="font-thin text-sm ">Travel Time</strong> <span class="text-lg  uppercase font-serif">{{ selectedDestination.travel }}</span></p>
     </div> </div>
    </div>
  </div>
</template>

<script>
import { ref, onMounted } from 'vue';
import data from '@/assets/data.json';
import moonImage from '@/assets/destination/image-moon.png';
import marsImage from '@/assets/destination/image-mars.png';
import europaImage from '@/assets/destination/image-europa.png';
import titanImage from '@/assets/destination/image-titan.png';

export default {
  name: 'DestinationView',
  setup() {
    const destinations = ref(data.destinations);
    const selectedDestination = ref(null);
    const selectedDestinationImage = ref('');

    const images = {
      Moon: moonImage,
      Mars: marsImage,
      Europa: europaImage,
      Titan: titanImage
    };

    onMounted(() => {
      if (destinations.value.length > 0) {
        selectDestination(destinations.value[0]);
      }
    });

    const selectDestination = (destination) => {
      selectedDestination.value = destination;
      selectedDestinationImage.value = images[destination.name];
    };

    return {
      destinations,
      selectedDestination,
      selectedDestinationImage,
      selectDestination
    };
  }
};
</script>

<style scoped>


.destination-nav button {
  padding: 0.5rem 1rem;
  border: none;
  background: none;
  cursor: pointer;
  font-size: 1rem;
}

.destination-nav button.active {
  border-bottom: 4px solid white
}




</style>
