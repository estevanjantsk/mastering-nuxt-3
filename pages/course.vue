<template>
  <div
    class="p-12 bg-gray-100 w-full h-full min-h-screen flex flex-col"
    >
    <div
      class="prose mb-12"
    >
      <h1 class="text-3xl text-center">
        <span class="font-medium">
          Course:
          <span class="font-bold">Mastering Nuxt 3</span>
        </span>
      </h1>
    </div>

    <div class="flex flex-row justify-center flex-grow">
      <div
        class="prose mr-4 p-8 bg-white rounded-md min-w-[20ch] max-w-[30ch] flex flex-col"
      >
        <h3 class="font-bold text-lg mb-6">Chapters</h3>

        <div class="space-y-1 mb-4 flex flex-col" v-for="chapter in chapters"
          :key="chapter.slug">
          <h4>{{ chapter.title }}</h4>

          <NuxtLink v-for="(lesson, index) in chapter.lessons"
            :key="lesson.slug"
            class="flex flex-row space-x-1 no-underline font-normal py-1"
            :to="lesson.path"
            :class="{
              'text-blue-500': lesson.path === $route.fullPath,
              'text-gray-600': lesson.path !== $route.fullPath
            }"
          >
            <span class="text-gray-500 text-sm">{{ index + 1 }}.</span>
            <span class="text-sm">{{ lesson.title }}</span>
          </NuxtLink>
        </div>
      </div>

      <div class="prose p-12 bg-white rounded-md w-[65ch]">
        <NuxtPage />
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
  const { chapters } = useCourse();
</script>

<!-- <style scoped>
  .router-link-active {
    @apply text-blue-500;
  }
</style> -->