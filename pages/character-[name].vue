<script setup lang="ts">
const router = useRouter();
const route = useRoute();
const names = ref({
  'daniel': 'Bobby Blaze',
  'ben': 'Al Lusion',
  'edward': 'Bertie Bicept',
  'dad': 'Juan Wheel',
  'mum': 'Krystal Ball',
  'chloe': 'Sam O Salt',
  'claire': 'Vee Sharpe',
  'jacob': 'Hugh G Shooz'
});
const occupations = ref({
  'daniel': 'Fire Eater',
  'ben': 'Magician',
  'edward': 'Strongman',
  'dad': 'Unicyclist',
  'mum': 'Fortune Teller',
  'chloe': 'Fire Eater',
  'claire': 'Fire Eater',
  'jacob': 'Fire Eater'
});
const backgrounds = ref({
  'daniel': "If I wasn't working here I'd probably be in Prison! I used to get into a lot of trouble for setting fire to things, but I was just really interested in flames and how they behave. I got into fire eating accidenally, really. I was in my room, with a small iece of lit wood, just staring at the flame, and I heard my dad coming up the stairs. I panicked and just stuck it in my mouth to put it out! It hurt a bit and I couldn't eat for a week but I was hooked. I went to the library and learned everyrthing I could about the fmaous 18th century fire eater, Robert Powell. After a couple of years, and a few trips to the hospital, I'd perfected my art and got myself this amazing job with the best circus in the world.",
  'ben': "I love tricking people. I love the look on their faces when they're puzzling over how I do what I do. My parents used to have a magic act at all the summer fairs so I learnt a lot from them. But I was hungry for more and I was already better than both of them by the time I was 10. I joined Starlight when I was 14, I didn't even think about doing anything else. Magic is in my blood.",
  'edward': "I was always a strong lad. My dad had me lugging anything heavy around in his ironmongers shop from when I was 6! My muscles developed really fast but I didn't want to be an ironmonger so when I was 14, I ran away to the circus. I've only ever worked for Starlight Circus. I can't imagine performing anywhere else.",
  'dad': "I was a very acedemic student and my parents thought I was going to be a doctor, but I found an old unicycle in the cellar when I was 10 and that was that. I can't ride a normal bicycle - too many wheels! I've worked at all the top circuses but Starlight is my favourite. I'm never leaving!",
  'mum': "I come from a long line of fortune tellers — the women in my family have been doing it for about 200 years. It's not something you can learn. You're either born with it or you're not. Sometimes I don't even need to concentrate. For example, the other day, in the middle of supper, it simply came to me that the strange French painter, Cézanne, is going to die next year. Mark my words. You'll see. Anyway, there's always a long line of people waiting to see me here at Starlight. People always want to know what's in store for them.",
  'chloe': "I've been a performer with Starlight for my entire life. My mother, God rest her soul, was an acrobat here and I was born in one of the caravans. I think I could do cartwheels and handsprings before I could walk properly. There's something very dull about just walking normally, don't you think? Being the right way up all the time bores me senseless. Everyone here at Starlight is my family maybe not blood relations, but family nonetheless. I'll be here till the day I die.",
  'claire': "My dad was a scrap iron merchant and knife sharpener. I used to go round on the horse and cart with him and I was always more interested in the knives than anything else. One day, just for fun, I threw a knife at a scarecrow and I got him right between the eyes. Later that year, my parents took me to the circus and I saw a professional knife thrower for the first time. I couldn't stop thinking about it and I secretly practised in the fields near our house. When Starlight came to town a few years later, I convinced Dani to come and see what I could do and I was hired on the spot. I've been here eight years now and I still love the gasps from the crowd as I send my daggers sailing through the air, hitting the backboard just inches from my 'victim'!",
  'jacob': "When I was a child, everyone said I was really funny. I was always clowning around at school. The teachers didn't seem to appreciate it, though. I don't know why! When I found out that my great-grandfather had been a clown, I decided that was what I wanted to do. When Starlight visited my little town when I was 18, I marched in and asked Dani for a job. I had them roaring with laughter after five minutes and I've worked here ever since."
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
    <div class="border p-6 grid gap-3 relative" v-if="names[route.params.name]">
      <div class="flex gap-5">
        <h4 class="text-4xl">Your role is...</h4>
      </div>      
      <div class="grid grid-cols-[auto_1fr] gap-x-5 gap-y-3">      
        <span class="text-yellow-500">Name: </span>
          <span>{{ names[route.params.name] }}</span>          
        <span class="text-yellow-500">Occupation: </span>
        <span>{{ occupations[route.params.name] }} at Starlight Circus</span>
        <span class="text-yellow-500">Background: </span>
        <span>{{ backgrounds[route.params.name] }}</span>
      </div> 
      <img :src="imageSrc" class="size-40 mx-auto">
    </div>
    <div class="flex w-full text-orange-500 text-3xl items-center py-4" v-else>
      Sorry guest not found...
    </div>
  </div>
</template>

<style scoped></style>