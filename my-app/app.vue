<script setup>
const colorMode = useColorMode();

const isDark = computed({
  get() {
    return colorMode.value === 'dark';
  },
  set() {
    colorMode.preference = colorMode.value === 'dark' ? 'light' : 'dark';
  },
});
</script>

<template>
  <UCard class="m-8">
    <p>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Repudiandae
      molestiae perferendis expedita magnam adipisci, assumenda voluptatem
      dignissimos? Atque nisi ex cum iure laboriosam nihil, doloremque
      reprehenderit est fugiat, totam consequuntur? <br /><br />
    </p>
    <template #header />
    <UTabs :items="items" :default-index="2" />
    <ClientOnly>
      <UButton
        :icon="
          isDark ? 'i-heroicons-moon-20-solid' : 'i-heroicons-sun-20-solid'
        "
        color="gray"
        variant="ghost"
        aria-label="Theme"
        @click="isDark = !isDark"
      />

      <template #fallback>
        <div class="w-8 h-8" />
      </template>
    </ClientOnly>
    <template #footer />
  </UCard>
</template>
