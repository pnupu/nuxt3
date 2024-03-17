<template>
  <Transition name="layout" mode="out-in">
    <div>
      <NuxtLayout>
        <Transition name="page" mode="out-in">
          <div :key="$route.fullPath">
            <NuxtPage />
          </div>
        </Transition>
      </NuxtLayout>
    </div>
  </Transition>
</template>
<script lang="ts" setup>
useHead({
  title: "Nuxt 3 test app",
});
</script>
