<script setup>
  import useAPI from '@/composables/useApi'
  import MainCardsSingle from '@/components/MainCardsSingle.vue'

  const { recipes } = useAPI()
</script>

<template>
  <div class="sub-wrapper">
    <Suspense>
      <MainCardsSingle v-for="recipe in recipes" :key="recipe.recipeID" :recipe="recipe" />
      <template #fallback>
        <div>Loading...</div>
      </template>
    </Suspense>
  </div>
</template>

<style scoped lang="postcss">
  .sub-wrapper {
    @apply grid grid-cols-1 gap-4 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4;
  }
</style>