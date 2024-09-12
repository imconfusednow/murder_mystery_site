<script setup>
  import {ref, computed} from 'vue';

  const props = defineProps(['text', 'frequency']);
  const currentIndex = ref(0);
  let interval = null;

  const currentText = computed(() => {
    return props.text.slice(0, currentIndex.value);
  });

  onBeforeMount(() => {
    interval = setInterval(()=>{
        currentIndex.value += 1;
        if (currentIndex.value == props.text.length) {
          clearInterval(interval);
        }
    }, props.frequency);
  });

</script>

<template>
    <div>
      {{ currentText }}
    </div>
</template>

<style scoped>

</style>