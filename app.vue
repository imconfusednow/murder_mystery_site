<template>
  <div class="min-h-svh bg-zinc-950 text-gray-100 grid justify-center">  
    <NuxtPage />
  </div>
</template>

<style>
.page-enter-active,
.page-leave-active {
  transition: all 0.4s;
}
.page-enter-from,
.page-leave-to {
  opacity: 0;
}
</style>