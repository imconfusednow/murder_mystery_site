<script setup lang="ts">
  const router = useRouter();
  const name = ref('');

  const nameTranslations: object = {
    'dan': 'daniel',
    'eddie': 'edward',
    'gill': 'mum',
    'gillian': 'mum',
    'john': 'dad'
  }
  
  function find() {
    if (!name.value) {
      return;
    }
    const sName: string = strippedName(name.value)
    router.push(`/character-${sName}`);
  }

  function strippedName (name: string) {
    let strippedName: string = name.toLowerCase();
    strippedName = strippedName.replaceAll("allport", "");
    strippedName = strippedName.replaceAll("peak", "");
    strippedName = strippedName.replaceAll(" ", "");

    strippedName = nameTranslations[strippedName] ?? strippedName;
    return strippedName;
  }

</script>

<template>
  <div class="max-w-screen-lg h-full grid items-start gap-10 p-4">
    <h1 class="text-7xl text-balance md:text-wrap">You are invited to a day of food and night of <span class="text-red-600">murder...</span></h1>
    <div class="grid gap-2 text-gray-300">
      <blockquote class="w-fit my-8 text-zinc-400 text-2xl text-wrap">Roll up, roll up and join us for an unforgettable night at the
        world famous Starlight Circus!</blockquote>
        
    </div>
    <TypeWriter class="text-wrap text-lg min-h-44 md:min-h-16" frequency="20" text="The lights are low and the acts are limbering up under the Big Top but who is lurking in the shadows? The real show is only just beginning! Stretch your muscles and your mind to piece together the clues and identify the killer amongst you." />
    <!-- <p class="text-wrap text-lg">The lights are
        low and the acts are limbering up under the Big Top - but who is lurking in the shadows? The real show is only
        just beginning! Stretch your muscles and your mind to piece together the clues and identify the killer amongst you.
      </p>     -->
    <div class="mx-auto gap-10 w-full grid grid-cols-3">
      <img class="" src="/img/burger.svg"/>
      <img class="" src="/img/circus.svg"/>
      <img class="" src="/img/knife.svg"/>
      </div>
    <div class="border border-slate-500 p-5 grid gap-4 w-full max-w-screen-sm mx-auto">
      <div class="grid gap-3 items-center justify-center">
        <label for="guest-name" class="text-xl">Find out who you'll be: </label>
        <form class="flex gap-1" @submit.prevent="find">
        <input v-model="name" class="rounded-sm p-2 outline-none bg-gray-800" id="guest-name"
          placeholder="Your Name" />
        <button :disabled="!name" @click="find" class="bg-green-800 p-2 px-8 rounded-md hover:brightness-90 active:brightness-110 disabled:opacity-50">Find</button>
      </form>
      </div>
    </div>
  </div>
</template>

<style scoped>
blockquote {
  position: relative;

  &::before,
  &::after {
    position: absolute;
    color: rgba(59, 59, 59, 0.8);
    font-size: 8rem;
  }

  &::before {
    font-family: 'Gill Sans';
    content: open-quote;
    left: 0rem;
    top: -0.8rem;
  }

  &::after {
    font-family: 'Gill Sans';
    content: close-quote;
    right: 0rem;
    bottom: -4rem;
  }
}
</style>