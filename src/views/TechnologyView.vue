<template>
  <div class="bg-black text-white w-full absolute inset-0">
    <img src='@/assets/technology/background-technology-desktop.jpg' alt="Home desktop background"
      class="sm:hidden md:hidden lg:block w-full h-full object-cover" />
    <img src='@/assets/technology/background-technology-mobile.jpg' alt="Home mobile background"
      class="lg:hidden md:hidden sm:block w-full h-full object-cover" />
    <img src='@/assets/technology/background-technology-mobile.jpg' alt="Home mobile background"
      class="lg:hidden sm:hidden md:block w-full h-full object-cover" />

      <div class="absolute inset-0 flex lg:flex-row md:flex-col-reverse sm:flex-col-reverse gap-x-40 items-center justify-center"> 
        <div class="flex flex-col gap-y-40  md:gap-y-8 sm:gap-y-2">
            <h2 class="lg:flex flex-row uppercase gap-x-2 text-xl text-white md:hidden sm:hidden "><span class="text-gray-300">03</span> space launch 101</h2>
            <div class="flex lg:flex-row md:flex-col sm:flex-col md:items-center sm:items-center sm:justify-center md:justify-center md:gap-y-6 gap-x-6 md:mt-8 sm:mt-6">
      <nav class=" md:flex md:flex-row sm:flex sm:flex-row lg:flex lg:flex-col lg:gap-y-8 sm:gap-x-8 md:gap-x-8 ">
        
        <button
          v-for="(techItem, index) in technology"
          :key="techItem.name"
          @click="selectTechItem(techItem)"
          :class="{ active: selectedTechItem && selectedTechItem.name === techItem.name }"
          class="tech-circle"
        >
          <span>{{ index + 1 }}</span>
        </button>
      </nav>
      <div v-if="selectedTechItem" class="flex flex-col gap-y-3 md:items-center md:justify-center sm:items-center sm:justify-center lg:items-start sm:mt-4 md:mt-4">
        <h2 class="lg:text-2xl md:text-2xl sm:text-lg uppercase font-serif font-thin text-gray-400">The terminology...</h2>
        <h2 class="lg:text-6xl sm:text-2xl font-serif uppercase sm:text-center lg:text-start">{{ selectedTechItem.name }}</h2>
        <p class="w-[27rem] sm:w-[20rem] text-sm md:text-center sm:text-center lg:text-start">{{ selectedTechItem.description }}</p>
      </div>
    </div></div>

    <img v-if="selectedTechItem" :src="images[selectedTechItem.name].portrait" :alt="selectedTechItem.name" class="lg:w-[30rem] lg:h-[26rem] mt-12 md:w-screen md:h-[26rem] sm:w-screen sm:h-[16rem]" />
  <h2 class=" flex-row uppercase gap-x-2 text-xl text-white lg:hidden "><span class="text-gray-300">03</span> space launch 101</h2>
</div>  </div>
</template>

<script>
import { ref, onMounted } from 'vue';
import data from '@/assets/data.json';

// Import images
import LaunchVehiclePortrait from '@/assets/technology/image-launch-vehicle-portrait.jpg';
import LaunchVehicleLandscape from '@/assets/technology/image-launch-vehicle-landscape.jpg';
import SpaceportPortrait from '@/assets/technology/image-spaceport-portrait.jpg';
import SpaceportLandscape from '@/assets/technology/image-spaceport-landscape.jpg';
import SpaceCapsulePortrait from '@/assets/technology/image-space-capsule-portrait.jpg';
import SpaceCapsuleLandscape from '@/assets/technology/image-space-capsule-landscape.jpg';

export default {
  name: 'TechnologyView',
  setup() {
    const technology = ref(data.technology);
    const selectedTechItem = ref(null);

    const images = {
      'Launch vehicle': {
        portrait: LaunchVehiclePortrait,
        landscape: LaunchVehicleLandscape
      },
      'Spaceport': {
        portrait: SpaceportPortrait,
        landscape: SpaceportLandscape
      },
      'Space capsule': {
        portrait: SpaceCapsulePortrait,
        landscape: SpaceCapsuleLandscape
      }
    };

    onMounted(() => {
      if (technology.value.length > 0) {
        selectedTechItem.value = technology.value[0];
      }
    });

    const selectTechItem = (techItem) => {
      selectedTechItem.value = techItem;
    };

    return {
      technology,
      selectedTechItem,
      selectTechItem,
      images
    };
  }
};
</script>

<style scoped>
@media (min-width: 1024px) {
   .technology-nav {
  display: flex;
  gap: 2rem;
  flex-direction: column;
} 
    
}



 .tech-circle {
  width: 3rem;
  height: 3rem;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 2px solid white;
  border-radius: 50%;
  background-color: transparent;
  color: white;
  cursor: pointer;
  font-size: 1.5rem;
  transition: background-color 0.3s, color 0.3s;
}

 .tech-circle.active {
  background-color: white;
  color: black;
}
</style>
