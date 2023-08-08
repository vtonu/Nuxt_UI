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
// Accordion dropdowns
const items = [
  {
    label: 'Rules',
    icon: 'i-heroicons-information-circle',
    defaultOpen: false,
    content:
      'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed neque elit, tristique placerat feugiat ac, facilisis vitae arcu. Proin eget egestas augue. Praesent ut sem nec arcu pellentesque aliquet. Duis dapibus diam vel metus tempus vulputate.',
  },
  {
    label: 'Instructions',
    icon: 'i-heroicons-arrow-down-tray',
    disabled: true,
    content:
      'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed neque elit, tristique placerat feugiat ac, facilisis vitae arcu. Proin eget egestas augue. Praesent ut sem nec arcu pellentesque aliquet. Duis dapibus diam vel metus tempus vulputate.',
  },
];
</script>

<template>
  <UCard class="m-10">
    <UAccordion color="primary" variant="outline" size="sm" :items="items" />
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
        variant="outline"
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
