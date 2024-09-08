<script setup lang="ts">
const router = useRouter();
const route = useRoute();
const names = ref({
  'daniel': 'Bobby Blaze'
});
const occupations = ref({
  'daniel': 'Fire Eater at Starlight Circus'
});
const backgrounds = ref({
  'daniel': "If I wasn't working here I'd probably be in Prison! I used to get into a lot of trouble for setting fire to things, but I was just really interested in flames and how they behave. I got into fire eating accidenally, really. I was in my room, with a small iece of lit wood, just staring at the flame, and I heard my dad coming up the stairs. I panicked and just stuck it in my mouth to put it out! It hurt a bit and I couldn't eat for a week but I was hooked. I went to the library and learned everyrthing I could about the fmaous 18th century fire eater, Robert Powell. After a couple of years, and a few trips to the hospital, I'd perfected my art and got myself this amazing job with the best circus in the world."
});

const imageSrc = computed(()=>{
  return "/img/" + route.params.name + '.svg';
});


</script>

<template>
  <div class="max-w-screen-lg grid items-start content-start gap-10 p-4">
    <div class="flex p-1">
    <button class="bg-gray-800 p-2 px-8 rounded-md hover:brightness-90 active:brightness-110 disabled:opacity-50 font-bold"><NuxtLink to="/">Back</NuxtLink></button>
    </div>
    <h1 class="text-7xl"><span class="text-red-600">Murder</span> Mystery at the Circus</h1>
    <div class="text-xl">
      <p>You are invited to embarc on an evening of intrigue, deceit and wrongdoing at the starlight curcus set in 1905.
      </p>
      <p>Can you work out whodunnit?</p>
    </div>
    <div class="border p-6 grid gap-3 relative">
      <div class="flex gap-5">
        <h4 class="text-4xl">Your role...</h4>
      </div>
      <div class="grid grid-cols-[auto_1fr] gap-x-5 gap-y-3">
      
        <span class="text-red-600">Name: </span>
          <span>{{ names[route.params.name] }}</span>          
        <span class="text-red-600">Occupation: </span>
        <span>{{ occupations[route.params.name] }}</span>
        <span class="text-red-600">Background: </span>
        <span>{{ backgrounds[route.params.name] }}</span>
      </div> 
      <img :src="imageSrc" class="size-40 mx-auto">    
    </div>
  </div>
</template>

<style scoped></style>