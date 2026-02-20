<script setup>
import { ref } from 'vue'
import LinkCard from '@/components/LinkCard.vue'

const profile = ref({
  name: 'Derek Cameron',
  slogan: 'Computer Support Specialist in Training',
  avatar:
    'https://api.dicebear.com/9.x/avataaars/svg?backgroundColor=b6e3f4&accessories[]&clothesColor=262e33&clothing=collarAndSweater,graphicShirt,hoodie,shirtCrewNeck&clothingGraphic[]&eyebrows=default&eyes=default&facialHair[]&hairColor=2c1b18&hatColor[]&mouth=twinkle&skinColor=ffdbb4&top=shortCurly&seed=Derek',
  links: [
    {
      id: 1,
      title: 'GitHub',
      url: 'https://github.com/dcamero2',
      icon: 'code',
      description: 'Check out my projects',
    },
    {
      id: 2,
      title: 'Linkedin',
      url: 'https://www.linkedin.com/in/derek-cameron-5bb44b3b2/',
      icon: 'briefcase',
      description: 'Connect with me professionally',
    },
    {
      id: 3,
      title: 'Expense Splitter',
      url: 'https://expense-splitter-vue.dcamero2.workers.dev/',
      icon: 'money',
      description: 'A website that divides expenses accordingly',
    },
  ],
})
</script>

<template>
  <main class="flex min-h-screen flex-col items-center px-4 py-8">
    <!-- Profile Header -->
    <div class="mb-8 flex flex-col items-center text-center">
      <div
        class="mb-4 h-24 w-24 overflow-hidden rounded-full border-4 border-green-400 shadow-lg shadow-green-500/20 sm:h-32 sm:w-32"
      >
        <img
          :src="profile.avatar"
          :alt="profile.name"
          class="h-full w-full object-cover"
        />
      </div>
      <h1 class="mb-2 font-display text-2xl font-bold text-white sm:text-3xl">
        {{ profile.name }}
      </h1>
      <p class="max-w-xs text-gray-300 sm:text-lg">{{ profile.slogan }}</p>
    </div>

    <!-- Link List -->
    <div class="flex w-full max-w-md flex-col gap-4">
      <LinkCard
        v-for="link in profile.links"
        :key="link.id"
        :title="link.title"
        :url="link.url"
        :description="link.description"
        :icon="link.icon"
      />
    </div>

    <!-- Navigate to Info -->
    <RouterLink
      to="/info"
      class="mt-8 text-sm text-gray-400 underline-offset-4 transition-colors duration-200 hover:text-green-400 hover:underline"
    >
      About me →
    </RouterLink>
  </main>
</template>
