<template>
  <div class="w-full absolute inset-0">
    <img src='@/assets/crew/background-crew-desktop.jpg' alt="Home desktop background"
      class="sm:hidden md:hidden lg:block w-full h-full object-cover" />
    <img src='@/assets/crew/background-crew-mobile.jpg' alt="Home mobile background"
      class="lg:hidden md:hidden sm:block w-full h-full object-cover" />
    <img src='@/assets/crew/background-crew-mobile.jpg' alt="Home mobile background"
      class="lg:hidden sm:hidden md:block w-full h-full object-cover" />
    <div class="absolute inset-0 flex lg:flex-row sm:flex-col md:flex-col items-center justify-center sm:items-center sm:justify-center gap-x-48 lg:mt-20">
      <div v-if="selectedCrewMember" class="flex flex-col lg:gap-y-20 lg:items-start sm:gap-y-6 sm:items-center sm:justify-center">
         <h2 class="flex flex-row uppercase gap-x-2 text-white"><span class="text-gray-300">02</span> Meet your crew</h2>
       <div  class="text-white flex flex-col lg:gap-y-8 sm:gap-y-4 sm:items-center sm:justify-center lg:items-start"> <p class="uppercase font-serif font-thin text-2xl">{{ selectedCrewMember.role }}</p>
        <h2 class="text-5xl font-serif uppercase sm:text-center">{{ selectedCrewMember.name }}</h2>
        <p class="text-sm lg:w-[27.5rem] md:w-[28rem] sm:w-[20rem] sm:text-center lg:text-start ">{{ selectedCrewMember.bio }}</p></div>
        <nav class="crew-nav">
          <button
            v-for="(crewMember, index) in crew"
            :key="index"
            @click="selectCrewMember(crewMember)"
            :class="{ active: selectedCrewMember && selectedCrewMember.name === crewMember.name }"
            class="crew-circle"
          ></button>
        </nav>
      </div>
      <div v-if="selectedCrewMember">
        <img :src="images[selectedCrewMember.name]" :alt="selectedCrewMember.name" class="lg:w-64 lg:h-84 sm:h-44 sm:w-36 sm:mt-8 md:mt-16 md:w-80 md:h-80" />
      </div>
    </div>
  </div>
</template>

<script>
import { ref, onMounted } from 'vue';
import data from '@/assets/data.json';

// Import images
import DouglasHurleyPng from '@/assets/crew/image-douglas-hurley.png';
import DouglasHurleyWebp from '@/assets/crew/image-douglas-hurley.webp';
import MarkShuttleworthPng from '@/assets/crew/image-mark-shuttleworth.png';
import MarkShuttleworthWebp from '@/assets/crew/image-mark-shuttleworth.webp';
import VictorGloverPng from '@/assets/crew/image-victor-glover.png';
import VictorGloverWebp from '@/assets/crew/image-victor-glover.webp';
import AnoushehAnsariPng from '@/assets/crew/image-anousheh-ansari.png';
import AnoushehAnsariWebp from '@/assets/crew/image-anousheh-ansari.webp';

export default {
  name: 'CrewView',
  setup() {
    const crew = ref(data.crew);
    const selectedCrewMember = ref(null);

    const images = {
      'Douglas Hurley': DouglasHurleyWebp, // or DouglasHurleyPng if you prefer PNG
      'Mark Shuttleworth': MarkShuttleworthWebp,
      'Victor Glover': VictorGloverWebp,
      'Anousheh Ansari': AnoushehAnsariWebp,
    };

    onMounted(() => {
      if (crew.value.length > 0) {
        selectedCrewMember.value = crew.value[0];
      }
    });

    const selectCrewMember = (crewMember) => {
      selectedCrewMember.value = crewMember;
    };

    return {
      crew,
      selectedCrewMember,
      selectCrewMember,
      images
    };
  }
};
</script>

<style scoped>
.crew-nav {
  display: flex;
  gap: 1rem;
}

.crew-nav .crew-circle {
  width: 1rem;
  height: 1rem;
  border-radius: 50%;
  background-color: gray;
  border: none;
  cursor: pointer;
  
}

.crew-nav .crew-circle :hover{
background-color: white;
}

.crew-nav .crew-circle.active {
  background-color: white;
}

.crew-details {
  margin-top: 2rem;
}

.crew-details img {
  max-width: 100%;
  height: auto;
}

.crew-details p {
  margin: 0.5rem 0;
}
</style>
