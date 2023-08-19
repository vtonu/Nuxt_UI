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
    label: 'GAME124_Tonu_P1',
    icon: 'i-heroicons-information-circle',
    defaultOpen: false,
    content:
      'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed neque elit, tristique placerat feugiat ac, facilisis vitae arcu. Proin eget egestas augue. Praesent ut sem nec arcu pellentesque aliquet. Duis dapibus diam vel metus tempus vulputate.',
  },
  {
    label: 'GAME124_Tonu_P2',
    icon: 'i-heroicons-information-circle',
    defaultOpen: false,
    content:
      'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed neque elit, tristique placerat feugiat ac, facilisis vitae arcu. Proin eget egestas augue. Praesent ut sem nec arcu pellentesque aliquet. Duis dapibus diam vel metus tempus vulputate.',
  },
];
</script>

<template>
  <UCard class="m-10">
    <template #header />
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
    <h3 class="text-xl font-bold text-gray-900 dark:text-white">
      Introduction to 3D with Maya <br /><br />
    </h3>
    <p>
      This course is an introduction to the 3D content creation process as
      practiced in Maya. Best practices for 3D modeling, texturing, file
      management, and animation will be examined. Students will build several
      small scenes and render those scenes into movies. Emphasis will be placed
      on 3D as it relates to the video game industry. <br /><br />
    </p>
    <UAccordion color="primary" variant="outline" size="sm" :items="items" />
    <UTabs :items="items" :default-index="2" />
    <template #footer />
  </UCard>
</template>
